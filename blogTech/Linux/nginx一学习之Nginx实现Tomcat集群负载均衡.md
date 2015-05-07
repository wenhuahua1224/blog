## Ngin负载均衡配置
 下面，我们看一下我们实现Nginx负载均衡的配置。配置文件为conf/nginx.conf，由于我们进行的代理的配置，通过使用一个单独的代理配置文件conf/proxy.conf，在conf/nginx.conf中引入该代理配置即可。

conf/proxy.conf的配置内容如下所示：



	#!nginx (-)
	# proxy.conf
	proxy_redirect          off;
	proxy_set_header        Host $host;
	proxy_set_header        X-Real-IP $remote_addr;  #获取真实ip
	#proxy_set_header       X-Forwarded-For   $proxy_add_x_forwarded_for; #获取代理者的真实ip
	client_max_body_size    10m;
	client_body_buffer_size 128k;
	proxy_connect_timeout   90;
	proxy_send_timeout      90;
	proxy_read_timeout      90;
	proxy_buffer_size       4k;
	proxy_buffers           4 32k;
	proxy_busy_buffers_size 64k;
	proxy_temp_file_write_size 64k;
 


各配置项的含义，可以通过查阅相关文档了解。下面看conf/nginx.conf的配置，我们根据实践操作所做的修改，并对相关基本配来做适当的说明，如下所示：

	user  root root; # Nginx所在的用户和用户组
	
	worker_processes  3; # 启动的工作进程数量
	
	error_log /usr/local/webserver/nginx/logs/nginx_error.log crit; #日志位置和日志级别
	#error_log  logs/error.log;
	#error_log  logs/error.log  notice;
	#error_log  logs/error.log  info;
	
	pid /usr/local/webserver/nginx/nginx.pid; # Nginx进程ID
	
	
	events {
	    worker_connections  1024;
	}
	
	
	http {
	    include       mime.types;
	    default_type  application/octet-stream;
	
	    #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
	    #                  '$status $body_bytes_sent "$http_referer" '
	    #                  '"$http_user_agent" "$http_x_forwarded_for"';
	
	    #access_log  logs/access.log  main;
	
	    sendfile        on;
	    #tcp_nopush     on;
	
	    #keepalive_timeout  0;
	    keepalive_timeout  65;
	
	    #gzip  on;
	    upstream localhost { # 发到localhost上的请求，通过Nginx转发到实际处理请求的服务器
	           server 192.168.8.222:8080 weight=1;
			   server 192.168.8.222:8180 weight=1;
	           
	    }
	
	    server {
	        listen       80; # Nginx监听的端口，默认为80
	        server_name  localhost; # Nginx所在主机的名称
	
	        #charset koi8-r;
	
	        #access_log  logs/host.access.log  main;
	
	        location / {
	            root   html/solr; # 请求资源的路径（代理：/home/shirdrn/servers/nginx/tml/solr/，该目录下没有任何数据）
	            index  index.html index.htm;
	            proxy_pass   http://localhost; # 代理：对发送到localhost上请求进行代理
	            include proxy.conf; # 引入proxy.conf配置
	        }
	
	        #error_page  404              /404.html;
	
	        # redirect server error pages to the static page /50x.html
	        #
	        error_page   500 502 503 504  /50x.html;
	        location = /50x.html {
	            root   html;
	        }
	
	        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
	        #
	        #location ~ \.php$ {
	        #    proxy_pass   http://127.0.0.1;
	        #}
	
	        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
	        #
	        #location ~ \.php$ {
	        #    root           html;
	        #    fastcgi_pass   127.0.0.1:9000;
	        #    fastcgi_index  index.php;
	        #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
	        #    include        fastcgi_params;
	        #}
	
	        # deny access to .htaccess files, if Apache's document root
	        # concurs with nginx's one
	        #
	        #location ~ /\.ht {
	        #    deny  all;
	        #}
	    }
	
	
	    # another virtual host using mix of IP-, name-, and port-based configuration
	    #
	    #server {
	    #    listen       8000;
	    #    listen       somename:8080;
	    #    server_name  somename  alias  another.alias;
	
	    #    location / {
	    #        root   html;
	    #        index  index.html index.htm;
	    #    }
	    #}
	
	
	    # HTTPS server
	    #
	    #server {
	    #    listen       443;
	    #    server_name  localhost;
	
	    #    ssl                  on;
	    #    ssl_certificate      cert.pem;
	    #    ssl_certificate_key  cert.key;
	
	    #    ssl_session_timeout  5m;
	
	    #    ssl_protocols  SSLv2 SSLv3 TLSv1;
	    #    ssl_ciphers  HIGH:!aNULL:!MD5;
	    #    ssl_prefer_server_ciphers   on;
	
	    #    location / {
	    #        root   html;
	    #        index  index.html index.htm;
	    #    }
	    #}
	
	}
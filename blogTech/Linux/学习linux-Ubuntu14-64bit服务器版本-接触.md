
## 一、初始化系统

### 1、修改ip：
  1. 修改配置文件

        sudo vim /etc/network/interfaces #添加以下内容：
        auto eth0                  #设置自动启动eth0接口
        iface eth0 inet static     #配置静态IP
        address 192.168.11.88      #IP地址
        netmask 255.255.255.0      #子网掩码
        gateway 192.168.11.1        #默认网关
  2. 修改dns:
  
        sudo gedit /etc/resolve.conf
        nameserver 8.8.8.8
        nameserver 8.8.8.4
  3.重启网络，使配置生效

        sudo /etc/init.d/networking restar
         
### 2、 安装Vim



### 3、 安装ssh服务



### 4、 连接pietty

  - 修改ssh配置文件 否则root无法进行远程登录
 
		……
		#Authentication:
		#缺省是no
		PermitRootLogin yes
		#缺省的是no
		PermitEmptyPasswords yes
		……
  - 使用pietty或者putty远程连接


## 二、安装依赖库

### 1、gcc

       sudo apt-get install build-essential
       http://wiki.ubuntu.org.cn/Gcc
       
## 三、安装软件

### 1、 redis安装
  1. 下载安装

        cd /usr/local/src/ 
        wget http://download.redis.io/releases/redis-3.0.1.tar.gz
		$ tar xzf redis-3.0.1.tar.gz
		$ cd redis-3.0.1
		$ make

  2. 为了便于管理：

        mkdir -p /usr/local/redis/bin
        mkdir -p /usr/local/redis/etc
          
        cp /usr/local/src/redis/redis.conf /usr/local/redis/etc
        cd /usr/local/src/redis/src
        cp ...  /usr/local/redis/bin

  3. 优化启动配置
 
    - 修改配置文件
        
            redis.conf  daemonize yes
        
### 2、nodejs安装

  1. 下载源码 
  
    你需要在http://nodejs.org/下载最新的Nodejs版本，本文以v0.10.24为例:

        cd /usr/local/src/
        wget http://nodejs.org/dist/v0.10.24/node-v0.10.24.tar.gz

  2. 解压源码

        tar zxvf node-v0.10.24.tar.gz

  3. 编译安装

		cd node-v0.10.24
		./configure --prefix=/usr/local/node/0.10.24
		make
		make install

  4. 配置NODE_HOME，进入profile编辑环境变量

		vim /etc/profile

    - 设置nodejs环境变量，在export PATH USER LOGNAME MAIL HOSTNAME HISTSIZE HISTCONTROL 一行的上面添加如下内容:

            #set for nodejs
			export NODE_HOME=/usr/local/node/0.10.24
			export PATH=$NODE_HOME/bin:$PATH
			:wq保存并退出，编译/etc/profile 使配置生效

    - 使其生效
   
			source /etc/profile

  5. 验证是否安装配置成功

		node -v
    - 输出 v0.10.24 表示配置成功

  6. npm模块安装路径

		/usr/local/node/0.10.24/lib/node_modules/

### 3、安装nginx  

#### 3.1安装nginx




	/usr/local/webserver/nginx/sbin/nginx -s reload            # 重新载入配置文件
	/usr/local/webserver/nginx/sbin/nginx -s reopen            # 重启 Nginx
	/usr/local/webserver/nginx/sbin/nginx -s stop              # 停止 Nginx
 
#### 3.2安装NPM

npm install
 
 

### 4、安装jdk
  
  1. 安装前准备
  
		sudo mkdir /usr/lib/jvm
		sudo cp -r ./jdk-6u45-linux-x64.bin /usr/lib/jvm/
  2. 安装：
	 - 执行权限
	              
            chmod +x jdk-6u7-linux-i586.bin
	 - 执行安装命令
	 
	        ./jdk-6u7-linux-i586.bin
  3. 设置环境变量。设置环境变量有好几种。我们选其中一种进行配置 

		vim /etc/profile
		 
		export JAVA_HOME=/usr/local/lib/jdk/jdk1.6.0_45
		export JRE_HOME=$JAVA_HOME/jre
		export PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
		export CLASSPATH=$CLASSPATH:.:$JAVA_HOME/lib:$JAVA_HOME/jre/lib
		 
		source /etc/environment 

  4. 验证jdk是否安装成功
  		
  		java -version 
### 5、安装tomcat

  1. tomcat是绿色的直接解压就可以使用
  
    - 解压安装
    
			cd /opt
			tar -zxvf apache-tomcat-6.0.43.tar.gz

    - 配置环境变量
    
			cd /opt/apache-tomcat-6.0.43
			vi ./bin/startup.sh


			export JAVA_HOME=/usr/local/lib/jdk/jdk1.6.0_45
			export JRE_HOME=$JAVA_HOME/jre
			export PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
			export CLASSPATH=$CLASSPATH:.:$JAVA_HOME/lib:$JAVA_HOME/jre/lib
			export TOMCAT_HOME=/opt/apache-tomcat-6.0.43
    - 启动
    
			./bin/startup.sh




[link_redis_1]: http://www.w3cschool.cc/redis/redis-install.html "redis安装教程"
[link_redis_2]: http://redis.io/download "redis官方"

[link_nginx_1]: http://www.w3cschool.cc/linux/nginx-install-setup.html "nginx安装教程"
[link_nginx_2]: http://blog.csdn.net/shirdrn/article/details/6845520 "nginx与tomcat负载配置"




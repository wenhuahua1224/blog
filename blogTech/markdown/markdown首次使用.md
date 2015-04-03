

# markdown语法

## 一、标题

# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题

## 二、列表
### 1、无序列表

* 第一个
* 第二个
* 第三个

### 2、有序列表

1. 第一个
2. 第二个
3. 第三个

## 三、引用

> 不悔梦归处，只恨太匆匆    ---电影《匆匆那年》

## 四、图片与链接

### 1、图片

![刘若英-原来你也在这里](a.jpg "这是内部引用") 

![aaa][imga]

[imga]:a.jpg "这是外部引用"

### 2、链接

[star45主页](http://star45.github.io/ "这是内部引用")

[star45github主页][link1]

[link1]:http://star45.github.io/ "这是外部引用"

## 五、粗体与斜体

### 1、粗体

**青春**

### 2、斜体

*青春*

## 六、表格

人物|时间|地点
---|---|---
刘备|1100|未知
刘备|1100|未知
刘备|1100|未知
刘备|1100|未知

## 七、代码框

  - 这是*java*代码
	
	+ 第一种
	  以下是代码
		```java
		/**
		 * 
		 * @brief 方法简短说明 
		 * @details 详细说明 
		 * @warning 注意事项
		 * @date 2015年3月25日 上午8:54:31
		 * @param args
		 */
		public static void main(String[] args) {
			System.out.println("Hello World");
	  }```	
		
    + 第二种
	
		以下是代码
	
		public static void main(String[] args) {
			System.out.println("Hello World");
		}
	
	- 这是*Python*代码
	
		```python
		@requires_authorization
		def somefunc(param1='', param2=0):
		    '''A docstring'''
		    if param1 > param2: # interesting
		        print 'Greater'
		    return (param2 - param1 + 1) or None
		class SomeClass:
		    pass
		>>> message = '''interpreter
		... prompt
		'''

## 八、分割线

***
A life without a rehearsal, every day is broadcast live. sunshine, from your heart clear. ------人生没有彩排，每天都是直播。阳光，源自你内心的清澈。
***
## 九、脚注

生成一个脚注[^footnote].
  [^footnote]: 这里是 **脚注** 的 *内容*.

写于2015/3/25 9:16:27 




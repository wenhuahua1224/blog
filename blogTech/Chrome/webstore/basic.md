# 第1节-基本插件

## 1-infinity

## 2-有道云笔记

## Vimium

**vimium是一款让你在chrome浏览器能方便地使用键盘操作浏览器的插件**

完全键盘操作，
Vimium使用快捷键总结：
KEY BINDINGS

NOTE: 标注为“*”的为进阶用法

在当前页中导航

key function
?   显示快捷键帮助
h,j,k,l 向左/下/上/右移动
gg,G    移动到页首/页尾
d,u (down/up) 向下/上翻页
zH,zL   向左/右翻一屏 *
f,F 打开链接，f在当前页打开，F在新页面打开 [1]
r   刷新，我大F5
gs  查看源码 *
i   进入插入模式（在默认focus输入框的页面有用，比如在B站输入屏蔽关键字的时候） *
yy  复制当前页URL
yf  复制链接URL [1]
gf  循环到下一个frame （在邮箱之类的网站很有用） *
gi  focus到第一个输入框 （按tab向下）
注[1]： 当按下f,F,yf时，将会为每个链接建立一个字母编号，此时键入对应的字母编号即可选中对应链接。

导航到新页面

key function
o,O 打开URL/书签/历史。o在当前tab打开，O在新tab打开
b,B 打开书签。b在当前tab打开，B在新tab打开
H,L 后退，前进
查找内容

key function
/   查找关键字 [2]
n,N 到下一个/上一个匹配项
注[2]: /contents\r将开启JavaScript正则匹配， /contents\I将强制大小写敏感， \\将匹配\

操作tab

key function
J,K 到左边/右边一个tab
g0,g$   到最左边/右边的tab
yt  复制当前tab
x   关闭当前tab
X   恢复刚关闭的tab
T   在所有tab中查找 *
进阶用法 *

key function
]],[[   进入名称为 “next”/“previous” 或类似 ”>“/”<“ 的链接
alt+f   打开多个链接
gu  到上一个层次
gU  到首页
W   为当前tab打开一个新的窗口
mx, `x  和vim类似的定位功能，x代表[a-z]，使用mx记住当前位置，使用`x返回


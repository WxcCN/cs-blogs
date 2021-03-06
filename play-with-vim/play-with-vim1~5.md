### 1、移动
h,j,k,l分别对应左下上右

### 2、模式
vim有四种模式：普通模式，插入模式，可视模式，命令行模式

1. 进入vim 默认为普通模式，光标为方块
2. 输入i 进入插入模式，窗口左下角为insert ，光标为闪烁竖线(闪不闪和vim配置有关)
3. 在普通模式下输入ctrl + v (windows有的是ctrl + q) 进入可视模式
4. 在普通模式下输入冒号 进入命令行模式

### 3、基于单词移动
![](https://images2018.cnblogs.com/blog/1034168/201807/1034168-20180720002457904-656469918.png)
比如在日常编程中一行代码：
private static final long serialVersionUID = 351592739956574233    6L;
当光标停留在private时
![](https://images2018.cnblogs.com/blog/1034168/201807/1034168-20180720002707705-880721563.png)
普通模式下，输入：
* w：到下一单词开头，即static的s
* b：反向移动到当前单词（如果光标不在单词开头）/ 上一单词 开头
* e：移动到当前单词（如果光标不在单词结尾）/下一单词的 结尾
* ge：反向移动到当前单词/ 上一单词 结尾

但是我们往往会遇到一些标点，由于他们的存在我们使用ew的时候往往有些问题，vim是如何划分单词的呢：

### 4、单词与字串
单词：由字母、数字、下划线或其他非空白字符的序列组成
字串：由非空白字符序列组成
他们都以空白字符分隔。
以request.getParameter("uuid"); 为例
单词：request  .  getParameter  ("  uuid  ");
只有一个字串
也就是说 字母、数字、下划线 连在一起的 属于一个单词，
非空白字符连在一起的，也是一个单词。
如果把uuid换成一个， 逗号
那么 (","); 就是一个单词

那么在字串间的移动也有快捷键
即 W  E  B  gE 原理同3

### 5、屏幕行与实际行
如果一行内容大于窗口，会进行换行 就像这样：
![](https://images2018.cnblogs.com/blog/1034168/201807/1034168-20180719000923671-12248408.png)
标号为实际行7的屏幕行占用了两行。
jk移动的话是以实际行为准，如果要移动屏幕行，使用gj, gk。

#Jmeter实战
##入门篇
###1、下载与使用

下载地址：http://jmeter.apache.org/download_jmeter.cgi

开源，基于java编写，所以得有jdk（jre）环境，下载完成直接解压，进入bin目录运行jmeter即可

![](http://images2015.cnblogs.com/blog/1034168/201704/1034168-20170422190616196-1746678435.png)

各个平台都差不多， 点开之后进入主界面

![](http://images2015.cnblogs.com/blog/1034168/201704/1034168-20170422190743962-1111749513.png)


可以通过 选项栏选择语言

![](http://images2015.cnblogs.com/blog/1034168/201704/1034168-20170422190917852-1158140118.png)

接下来就可以进行测试工作了。


###2、常用组件

因为我是用范围主要是测试http接口，其实主要就是测我自己写的接口，所以我就讲我用到的

####1)线程组
测试计划－添加－threads－线程组
因为我们的组件都是跑在线程上， 这里可以通过线程组模拟用户数量等。

####2)观察结果树
线程组－添加－监听器－观察结果树
这个组件用于调试观察我们的测试请求，可以看到接口响应，一会讲。

####3)http请求
线程组－添加－sample－http请求

这时候，我们一次请求需要的基本组件就这么多， 以百度为例。

![](http://images2015.cnblogs.com/blog/1034168/201704/1034168-20170422192725306-2038499914.png)

我们在服务器域名上输入被测系统的域名，路径就是接口路径，可以在Parameters里面添加参数。

之后点击运行， 就可以在 观察结果树 里面看到接口返回的信息了

![](http://images2015.cnblogs.com/blog/1034168/201704/1034168-20170422193237071-142899537.png)

可以清楚地看到响应头和响应数据，并且jmter支持直接用一些格式解析响应数据

![](http://images2015.cnblogs.com/blog/1034168/201704/1034168-20170422193353431-303191773.png)

这个就根据需求选择了， 一般rest接口都是json，直接默认text就可以。

关于http协议的知识就不赘述了。

####4) http cookie Manager,cookie manager

cache 和 cookie是http中经常需要使用的组件，与后端交互往往需要带上cookie的数据才能获取理想的响应。

直接 添加－配置元件即可。

关于cookie啰嗦一句， 如果模拟多用户， 最好每次都清除cookie，这样结果比较准确， 因为你带着cookie访问后端的逻辑会不一样，
当然这些都建立在你了解被测系统的基础上做决定。

![](http://images2015.cnblogs.com/blog/1034168/201704/1034168-20170422194559962-1880919553.png)

####5)测试数据

数据的准备一般直接从测试库down下来即可，

转成csv格式，很简单类似于这样

![](http://images2015.cnblogs.com/blog/1034168/201704/1034168-20170422195944602-1407586274.png)

然后

![](http://images2015.cnblogs.com/blog/1034168/201704/1034168-20170422200212009-1772379259.png)

csv file的值就是文件路径。
文件列号就是，要用第一列就填0，第二列就写1，以此类推。然后点生成

之后在想用到数据的地方，拷贝生成的字符串就行了，例如。
![](http://images2015.cnblogs.com/blog/1034168/201704/1034168-20170422200333321-1421011673.png)
这个用户名就可以每次变化了。

####6)脚本的录制

因为一个个添加请求太麻烦，出错率也高，（好吧主要是懒）。
有两种录制方法
1.badboy工具
2.http代理服务器。
这两种方法有很多博客了。
因为我没找到mac版的badboy，我就用了代理服务器，其实原理差不多，也挺方便。

####7)正则表达式提取器
脚本录制完还没结束，因为很多请求的参数是依赖于上一个请求的（比如说第一个接口是返回用户id，第二个接口是通过id获取详细信息。 ）
那么显然，我们每次传的id都不会相同，因为用户不同。 因为在真实环境中，这些id往往由js来控制写入请求参数里面，而jmeter无法执行这些js。这就要让测试人员认真过一下每个接口，看看是否有类似的情况。 如果有，那么我们就用正则提取器来提取这个“id”。供下一步使用。

![](http://images2015.cnblogs.com/blog/1034168/201704/1034168-20170422201219274-1877738523.png)

比如这个响应json的st需要给下一步使用，这个st就是“id”

那么 我们在http请求里添加－后置处理器－正则表达式提取器

![](http://images2015.cnblogs.com/blog/1034168/201704/1034168-20170422201343243-1113588552.png)

引用名称就是起个名字，正则表达式需要自己写，
模板是使用提取到的第几个值。因为可能有多个值匹配，所以要使用模板。从 1 开始匹配，依次类推。这里只有一个，所以填写 $1$ 即可；
匹配数字表示如何取值。0 代表随机取值，1 代表全部取值。这里只有一个，填 1 即可；
缺省值表示参数没有取到值的话，默认给它的值。一般不填。

接下来在使用到id的地方直接写 ${ST} 就可以了， 和上面测试数据的是一个意思。

####)聚合报告
以上基本可以完成一次自动化的测试了， 模拟用户数量直接在线程组里设置即可，
然后添加一下聚合报告，启动测试，就可以查看结果了。
别忘记先禁用 观察结果树 ，这样会省很多的资源。
over。


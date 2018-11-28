###idea 模版之自定义类与方法注释

很多公司都有要求的代码注释规范，我们每新建类或者方法的时候从新复制粘贴很麻烦，而且容易粘错。
当然自定义模板还可以用到很多地方，比如系统自带的 `sout`就是`system.out.print();` 当你输入某文本的时候，系统会自动替换成目标文本。 

####首先介绍一下类模板
不只是java类，所有支持的文件头都可以自定义

File -- Settings -- Editor -- Code Style -- File and Code Templates
![](http://images2015.cnblogs.com/blog/1034168/201702/1034168-20170219211126175-1661375026.png)

将对应文本替换就可以了，根据自己需求。 这些变量在Descriptions里面有定义 我先粘出来方便查找吧。


```
${PACKAGE_NAME}

name of the package in which the new file is created
${NAME}
 
name of the new file specified by you in the New <TEMPLATE_NAME> dialog

${USER}
 
current user system login name

${DATE}
 
current system date

${TIME}
 
current system time

${YEAR}
 
current year

${MONTH}
 
current month

${MONTH_NAME_SHORT}
 
first 3 letters of the current month name. Example: Jan, Feb, etc.

${MONTH_NAME_FULL}
 
full name of the current month. Example: January, February, etc.

${DAY}
 
current day of the month

${HOUR}
 
current hour

${MINUTE}
 
current minute

${PROJECT_NAME}
 
the name of the current project
```

但是这个暂时不知道怎么修改。

###然后就是方法模板
其实就是文本替换，也很简单

settings >  live templates

![](http://images2015.cnblogs.com/blog/1034168/201702/1034168-20170219213023863-693662782.png)

abbreviation 就是缩写 比如sout。
底下的是作用域，这里面的变量又不一样， 点击右侧 Edit variables可以编辑

其实是很多函数。 这个有需求的自己去查一查吧。
#Linux小技巧  
  
###定制专属命令

很多情况下我们需要用命令行客户端完成一些工作，但是每次敲命令得加上一系列的参数啥的特别麻烦。

比如如果链接redis，redis的ui客户端是在是太卡了。 总之之类的吧。还有很多应用场景。

以下是网上找的常用的配置

[原帖](http://blog.csdn.net/caib1109/article/details/51864686)


```
#将rm命令(不可逆删除)重定向到mv到某个文件夹, 当你不小心删了整个项目, 这个命令将救你一命
alias rm="mv -t /某个文件夹"  

#在任何地方用一个命令快速开关tomcat服务
export TOMCAT_HOME=/某个文件夹/tomcat-7.0.79
alias starttomcat="bash ${TOMCAT_HOME}bin/startup.sh"
alias closetomcat="bash ${TOMCAT_HOME}bin/shutdown.sh"

#在任何地方用一个命令下载到指定文件夹
alias wget="wget -P /某个文件夹"
```

然后输入 `source ~/.bashrc` 在当前shell生效。





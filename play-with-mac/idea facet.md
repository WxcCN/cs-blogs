###idea facet

昨天从svn检查一个项目后，部署至tomcat服务器，启动成功，但实际代码其实没有进去，
因为该项目不是maven项目， artifacats是自己配的， 应该是这里弄错的。
最后请教同事， 要配一下facet来标记成一个web项目。

> Facets表示某个module有的特征，比如web、strtus2、spring、hibernate等；
Artifacts是maven中的一个概念，表示某个module要如何打包，例如war exploded、war、jar、ear等等这种打包形式搜索；
一个module有了Artifacts就可以部署到应用服务器中了！

> >> Facets和Artifacts的区别：
Facets表示这个module有什么特征，如Web，spring和hibernate等。 artifact这个和maven的概念一下，就是这个module要产出什么，war，jar还是ear。
在给项目配置Artifacts的时候有好多个type的选项，exploed是什么意思：
explode 在这里你可以理解为展开，不压缩的意思。也就是war、jar等产出物没压缩前的目录结构。建议在开发的时候使用这种模式，便于修改了文件的效果立刻显现出来。
默认情况下，idea的modules和artifacts的output目录已经设置好了，不需要更改，打成war包的时候会自动在WEB-INF目录下生产classes目录，然后把编译后的文件放进去。


之后配置完fecet之后，部署artifact，项目成功启动

###参考博客

[ Intellij IDEA的Facets和Artifacts](http://blog.csdn.net/gongsunjinqian/article/details/53018172)
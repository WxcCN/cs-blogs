昨天idea出现了一个奇怪的问题：

项目没有按我指定的配置运行，按cmd＋；可以看输出。而是运行了配置包下的test环境的配置，
先一看，test环境被初始化为资源包并且在输出目录上， 先取消（file－》project structure－》source folders）

然后问题没解决，查看maven配置


```
		<profile>
			<id>test</id>
			<activation>
				<activeByDefault>false</activeByDefault>
			</activation>
			<properties>
				<res.dir>${basedir}/resource/test</res.dir>
				<war.name>test</war.name>
			</properties>
		</profile>
```

其中activeByDefault为true [pom简介](http://www.cnblogs.com/qq78292959/p/3711501.html)
之后在myeclipse中可以启动了，但是idea还是不行。

然后file －》invalidate chache  ＋ build －》 rebuild projecet 就可以了。

暂时没有确定具体是什么原因造成，  因为之前在idea中修改了test环境的配置， 编至 classes下可见，但是与控制台输出的不一样。 
所以暂时只能理解为缓存，等以后系统学一学在重新审视这个问题。
#快速搭建Sprting boot
###(包含日志组件 AOP等)


##1、利用idea搭建框架

很简单 点击 File -> new -> Project -> Spring Initializr

Initializr Service URL 填 https://start.spring.io

剩下填空就行了，最好路径中不要带中文

项目结构和pom如图

![spring ini](http://images2017.cnblogs.com/blog/1034168/201712/1034168-20171210231745240-1048659734.png)

##2、编写controller
新建一个类

类名添加 @RestController

方法名使用@RequestMapping(value = "/test",methon = RequestMethod.GET)
		或者@    @GetMapping(value = "/test2") 
其他同理

##3、启动方式
1、idea 自带启动方式， 点击![](http://images2017.cnblogs.com/blog/1034168/201712/1034168-20171210232555224-842144218.png)
三角形或者虫子即可。
2、进入项目目录 mvn spring-boot run
3、编译成jar包 mvn install   ->  java -jar  spring**.jar

##4、属性配置
默认会在resources目录下有application.properties
推荐更换为yml application.yml

![](http://images2017.cnblogs.com/blog/1034168/201712/1034168-20171210233121130-129980179.png)

###ps.属性注入

1、在yml中直接输入自定义的属性kv 例如 myvalue1: 12。
在使用的地方加上注解 @Value("${myvalue1}")
属性也可以作为变量在yml传给其他变量使用

2、对象的注入
在yml写好对象的属性 例如 myobj.v1: 2   myobj.v2: adf
在相应的对象加入注解 @ConfigurationProperties(prefix = "myobj")
这样，该对象如果注入到其他对象内使用时就带上配置的值了

###4.1 数据库配置



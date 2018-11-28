###js判断字符长度
直接使用String对象的属性,空格亦算一个字符

```
	myString = "Hello world";
	length = myString.length

```

###js比较字符串大小
js 字符串可以直接比较大小，规则是比较第一个字符的ascii码，如果第一个相同，继续比较下一位。



```
	a= 'AA';b= "B";c= "AC";d="BB"
a>b
	false
a<b
	true
a<c
	true
b<c
	false
b>d
	false
d<d
	false
b<d
	true
	
```

###js字符大小写转换
对于一个string对象str

```
str = "hello"
"hello"
str.toLocaleUpperCase();
"HELLO"
	
```
小写同理， 非字母不影响.
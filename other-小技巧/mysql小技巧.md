##mysql


[安装mysql](http://www.th7.cn/db/mysql/201504/101743.shtml)
###命令行链接数据库
`mysql -h ip -u user -P pawoord -p port` 
具体参数 --help写的很清楚

然后就可以执行sql了。
`select * from 表 where \G	`
这个\G  加上\G参数之后，表结构就变成纵向输出，即每条记录都会用 
字段名1:字段值1
字段名2:字段值2
的形式显示，方便人类阅读，这个在navicat等客户端有的不支持



###将一列值赋予另一列
会遇到新增一列， 需要用其他列的值来初始化这一列

或者根据业务条件把某行的某列值直接赋予到其他列。

行号	 | 列1 | 列2
:----------- | :-----------: | -----------:
1         | aaa        | ddd
2         | bbb        | ccc

```
UPDATE 表 SET 列1 = 列2 WHERE 1 = 1 ;UPDATE 表 SET 列1 = 列2 WHERE 行号 = 2;
```

###插入修改删除表的列
- 查看列：desc 表名;
- 修改表名：alter table t_book rename to bbb;
- 添加列：alter table 表名 add column 列名 varchar(30);
- 删除列：alter table 表名 drop column 列名;
- 修改列名MySQL： alter table bbb change nnnnn hh int;
- 修改列名SQLServer：exec sp_rename't_student.name','nn','column';
- 修改列名Oracle：lter table bbb rename column nnnnn to hh int;
- 修改列属性：alter table t_book modify name varchar(22);

###mysql命令行 
命令结束需要加 `;`

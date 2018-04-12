## Android 开发中使用SQLite数据库

	使用Facebook的stetho来做可视化学习数据库SQLite的操作

[Android ：SQLlite数据库 使用手册 \- 简书](https://www.jianshu.com/p/8e3f294e2828)

Android SQLite 使用的基本操作：

1. Bean类，对应数据库中的表结构；
2. 覆写SQLiteOpenHelper类，创建数据库和表；
3. Dao类，对对应的数据库表进行增删改查操作；

[android sqlite数据库 查询 \- 简书](https://www.jianshu.com/p/4f67e8c3463b)

----
	
	SQLiteOpenHelper
	SQLiteDatabase=SQLiteOpenHelper.getReadableDataBase();

参考 [Android开发中使用SQLite数据库](https://www.ibm.com/developerworks/cn/opensource/os-cn-sqlite/)

![944365\-473cb21a518cade1\.png \(606×476\)](http://upload-images.jianshu.io/upload_images/944365-473cb21a518cade1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 数据库升级：

升级数据的几种情况：

1. 增加表
2. 删除表
3. 修改表（增加表字段，删除表字段，修改表字段等操作）

[绝对值得一看的 Android 数据库升级攻略 \- Android \- 掘金](https://juejin.im/entry/586b5ecc61ff4b006d7eef05)

### MySql

1）MySql基本操作

- 创建数据库和表
- 对单表的增删改查

2）MySql多表操作

- 添加主键/外键
- 多表操作（左连接/右连接）

3）MySql事务

- 事务的概念，开启（transaction）、提交（commit）和回滚（rollback）事务
- 事务的四种隔离级别
- 创建存储过程
- 调用、查看、修改和删除存储过程

[mysql添加外键 \- yccMelody \- 博客园](http://www.cnblogs.com/yccmelody/p/5416456.html)

### 注意点
	SQL语句中的字符串是用单引号表示的，而不是双引号；

	create database student character set utf8;
	drop database student;

	create table news_table (  
        _id integer primary key autoincrement,   
        news_tittle varchar(50),  
        news_content varchar(5000)
	)	

	//在news_table表后添加一个student_name字段
	alter table news_table add column student_name text;

	insert into news_table (name,time) values ('jakey','2017/8/9');

	select * from news_table where name='jakey';

	update news_table set name='JakeyYe' where name='jakey';

	delect from news_table where name='JakeyYe';

	drop table if exists table_name;//删除数据库中的指定表

[mysql基本操作命令汇总\-\-笔记 \- 简书](http://www.jianshu.com/p/118e1c41e9f0)
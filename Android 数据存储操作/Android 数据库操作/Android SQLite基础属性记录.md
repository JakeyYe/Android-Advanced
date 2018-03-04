## Android SQLite基础属性记录

	SQLite是Android内置的一个小型、关系型、属于文本型的数据库；
	Android提供了对SQLite数据库的完全支持，应用程序中的任何类都可以通过名称来访问任何的数据库，但是应用程序之外的就不能访问；

SQLite支持的几种数据类型：

- null：表示一个null值
- integer：表示一个整数
- text：表示按照字符串来存储
- blob：表示按照二进制值存储，不做任何改变



1，不像其他的数据库只支持强类型的数据，也就是每一列的类型都必须预先指定，但是SQLite采用的是弱类型的字段；

2，SQLiteDatabase.execSQL()方法，执行不是SELECT或任何其他返回数据的SQL语句的单个SQL语句，重点是**不能执行select查询SQL语句**，原因是该方法没有返回值，返回类型为void；

[Android SQLite详解 \- 简书](http://www.jianshu.com/p/5c33be6ce89d)

[Android：SQLlite数据库操作最详细解析 \- 简书](http://www.jianshu.com/p/8e3f294e2828)
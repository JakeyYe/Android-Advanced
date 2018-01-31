## 数据库 greenDao 3.0 记录

	greenDao 是针对 Android SQLite 数据库的 ORM 组件；

greenDao 是 Android 的 ORM 框架，ORM 就是对象关系映射（Object Relative Mapping），它的实现思想就是将关系数据库中表的数据映射为对象，以对象的形式展现，一个类对应数据库中的一张表，该类的一个对象对应表中的一行数据，这样开发人员就可以把数据库的操作转化为对这些对象的操作，因此它的目的就是为了方便开发人员用面向对象的思想来实现数据库的操作；

SQLite 是一个关系型数据库，Java 用的是对象，对象和关系之间的数据交互需要一个东西去转换，这就是 greenDao 的作用，转换过程也复杂，数据库的列对应 Java 对象里的参数就可以了；

greenDao 3.0 会通过一个插件来生成代码，这个插件会去浏览所有被@Entity注解的类去收集表信息，并生成三个类，DaoSession,DaoMaster,和所有的Dao类。

### greenDao 3.0 的使用教程：
	1，在应用的build.gradle文件中添加下面的内容：
		classpath 'org.greenrobot:greendao-gradle-plugin:3.2.2'

	2，在Module的build.gradle文件中，添加下面的内容：
		apply plugin: 'org.greenrobot.greendao'
	
		//greenDao依赖
    	compile 'org.greenrobot:greendao:3.2.2'
	
	3，可以添加下面greenDao配置：
		greendao {
          schemaVersion 1
		  //通过gradle插件生成的数据库相关文件的包名，默认为你的entity所在的包名
          daoPackage 'com.example.mrye.greendaoexample.db'
          //设置自动生成文件的目录路径，要和上面的设置一起使用
          targetGenDir 'src/main/java'
     }


### 重要点记录

1，两个重要注解

1. @Entity 在对象上声明的注解，该对象对应数据库中的一张表
2. @id  id注解

2，配置声明

1. schemaVersion 数据库版本
2. daoPackage 包目录路径
3. targetGenDir 插件生成文件路径


[GreenDao 3\.0 的使用 \- CSDN博客](http://blog.csdn.net/mr_zhang0101/article/details/73486024)

[Android Studio集成greenDAO 3\.0基础教程 \- TeachCourse](http://teachcourse.cn/2464.html)
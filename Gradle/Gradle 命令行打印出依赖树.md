## Gradle 命令行打印出依赖树

	Gradle是一个非常好用的编译工具，特别是继承了maven的依赖项管理功能，需要的Library不需要像传统IDE一样手动下载复制到项目中，只需要简单的一句gradle脚本，就能自动下载下来并编译；

	每个模块都可能依赖其他模块，这些模块又会依赖别的模块，而一个项目中的多个模块，可能会对同一个模块的不同版本都有依赖，这样的话就可能会产生冲突；

	通过gradle命令行查看依赖树，可以比较直接地看到模块之间的依赖关系；


同样配置下的版本冲突，会自动使用最新版；而不同配置下（比如同时有compile，androidTestCompile等）的版本冲突，gradle同步会直接报错；

[Gradle依赖项学习总结，dependencies、transitive、force、exclude的使用与依赖冲突解决 \| Paincker \| Hacker Meets Painter](http://www.paincker.com/gradle-dependencies)

#### .gradlew app:dependences 命令行打印出app模块的所有的依赖
	原始命令行是
	gradle <subproject>:dependences

#### ./gradlew app:dependencies --configuration compile 将compile配置的依赖树打印出来
	Window平台是这样写：
	gradlew app:dependencies --configuration compile

[Using gradle to find dependency tree \- Stack Overflow](https://stackoverflow.com/questions/21645071/using-gradle-to-find-dependency-tree)

[gradle \- gradlew: Permission Denied \- Stack Overflow](https://stackoverflow.com/questions/17668265/gradlew-permission-denied)
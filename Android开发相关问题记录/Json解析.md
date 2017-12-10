## JSON解析

[Json官网](http://json.org/json-zh.html) 

JSON是轻量级的数据交换格式，键/值，键只能为String类型，值可以为多种数据类型；JsonObject(对象)，JsonArray(数组)的区别：
一个对象以"{"开头，以"}"结尾；数据以"["开头，以"]"结尾，对象是一个无序的" '键/值' 对"集合，键值对之间用逗号分
隔，数组是值的有序集合，值之间用逗号分隔。JsonObject就是键值对的无序集合，是一对一的关系；JsonArray是键值对的有序集
合，不过是一对多的关系，一个键对应多个值的关系。

	


#### Gson解析（序列化（Java对象转化为Json）/反序列化（Json转化为Java对象））：

	1，Java对象一定要有一个无参构造方法，这就是Gson实例化对象的关键；
	2，Java对象类中不要求有set/get方法
	3，当Json数据中，有多个键时（相当于有些键值对在有些情况时没有的），在Java对象类中可以全写上，这样可以不使用SerialName注解，当返回的Json数据中没有Java对象类中的键时，就会自动设置
	默认的一个值（String类型为null，int类型为0），也不会出问题，这样就不用为一个键出现多个名字而担忧（还可以使用SerialName注解）；
	4，Json数据中的值，只有int,float,double等这些数据可以直接写，字符串是要用引号括起来的，如：String data = "{name:'erwe',age:26,data:'no email'}";而不是gson不能解析带空格的字符串。

	Gson基本使用
	Gson注解
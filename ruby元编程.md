### 第二章：方法（消除方法的重复性）
- 动态调用方法
	- 使用Object#send()来调用方法。这种技术称为动态派发。
- 动态定义方法
	- 利用Module#define_method()方法定义一个方法，只需要为其提供一个方法名和一个充当方法主体的块即可。一般使用其代替def关键字来定义方法
- 使用method_missing()方法
	- 通过覆盖method_missing方法来解决问题
	- Module#const_missing()方法，当引用一个不存在的常量时，ruby将这个常量名作为符号传递给它。
	- 白板类：删除继承来的方法，使其只包含需要的方法。从BasicObject继承来的类会自动成为白板类。
	- Module#undef_method()方法删除所有的方法（包括继承），Module#remove_method()方法，只会删除接收者自己的方法。

- 动态代理(dynamic proxy)
	| 一个捕获幽灵方法调用并把它们转发给另外一个对象的对象，称为动态代理

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
	> 一个捕获幽灵方法调用并把它们转发给另外一个对象的对象，称为动态代理

### 第三章：代码块(**块是一种控制作用域的强大手段**)
- 查看当前方法是否包含块，Kernel#block_given?()方法来做到。
- 当定义一个块时，它会获取当时环境中的绑定，并且把它传递给一个方法时，它会带着这些绑定一起进入方法。
- 一般把块称为闭包，意味着一个块可以获取局部绑定，并一直带着它们。
- 一旦进入新的作用域，原先的绑定就会被替换为一组新的绑定
- 作用域门：类定义，模块定义，方法
- 在类和模块定义的代码会被立即执行，相反，方法定义的代码只有在方法被调用时被执行。
- 扁平化作用域：
- 使用Class.new()来代替class关键字
- 使用Module#define_method()方法来代替def
- Object#instance_eval(),把instance_eval()方法的块称为一个(**上下文探针**),因为它就像是深入到对象中的代码片段，对其进行操作。
- 存储一个块供以后使用：lambda(),proc(),Proc.new()
- 在lambda中的return是从当前的lambda中返回，而proc则是从定义proc的作用域中返回
- 可以使用Method#to_proc()方法把Method对象转换为Proc对象 

### 第四章：类定义
- 在ruby中定义类时，实际上是在运行代码
- 类宏
- 环绕别名
- 单件类（eigenclass是ruby的高级内容）,只能有一个实例
- class_eval()方法，它不需要使用class关键字就可以修改当前类
- 对象的eigenclass：class << 对象名
- 类方法是存储在eigenclass中的单件方法，可以在类这class << self 这样定义类方法
- 当类包含模块时，它获得的是实例方法，而不是类方法。类方法存在于模块的eigenclass中，依然无法触碰。
- 类扩展和对象扩展的应用非常普遍，ruby提供了一个专门的Object#extend()方法
- 别名：使用alias关键字，第一个参数是方法的新名字，第二个是原始名字，相同功能的Module#alias_method()方法
- 先给方法起一个别名，然后重新定义它，这时别名方法还是引用的原始方法。
- 使用环绕别名
	1. 给方法定义一个别名
	2. 重定义这个方法
	3. 在新的方法中调用老的方法

### 第五章：编写代码的代码
- eval()方法，Kernel#eval()方法会执行字符串中的代码，并返回执行结果。
- 可以使用Kernel#binding()方法来创建Binding对象，对于*eval()方法家族，可以给它们传递一个Binding对象作为额外的参数，代码就在这个作用域中执行
- ruby安全级别，从默认的0到4，$SAFE
- 操作实例变量：Object#instance_variable_get()方法和Object#instance_variable_set()方法，例：instance_variable_set("@#{str}",value)
- 钩子方法(难)，是不是就是回掉的应用呢，当做某事时触发某个事件。
	- inherited()方法是Class的一个实例方法，当类被继承时，ruby会调用这个方法。Class的实例方法就是类方法。
	- 可以通过覆盖Module#included()方法在模块的生命周期中插入代码
	- 可以通过环绕别名把一个普通的方法变成一个钩子方法
	- 通过在eigenclass中包含一个模块来达到定义类方法
- 类扩展混入：是类扩展与钩子方法的混合
	- 定义一个模块，姑且叫MyMixin
	- 在MyMixin中定义一个内部模块，并给它定义一些内部方法，这些方法最终会成为内方法
	- 覆盖MyMixin#included()方法来用ClassMethods扩展包含者(使用extend()方法)

***********

### 第七章：ActiveRecord的设计

# Python

# 类

## 声明

```Python
class ClassName:
	a = 10
	def __init__(self):
	def show(self):
```

方法必须有`self`​形参传入

## self

self = this

## 使用

```Python
class Employee:
    age = 0

    def __init__(self, age):
        self.age = age

    def show(self):
        print(self.age)


emp1 = Employee(18)
emp1.show()

del emp1.age  # 设置为对应属性的默认值
emp1.show()

hasattr(emp1, 'age')    # 如果存在 'age' 属性返回 True。
getattr(emp1, 'age')    # 返回 'age' 属性的值
setattr(emp1, 'age', 8) # 添加属性 'age' 值为 8
delattr(emp1, 'age')    # 删除属性 'age'
```

## 内置类属性

* \_\_dict\_\_ : 类的属性（包含一个字典，由类的数据属性组成）
* \_\_doc\_\_ :类的文档字符串
* \_\_name\_\_: 类名
* \_\_module\_\_: 类定义所在的模块（类的全名是'\_\_main\_\_.className'，如果类位于一个导入模块mymod中，那么className.\_\_module\_\_ 等于 mymod）
* \_\_bases\_\_ : 类的所有父类构成元素（包含了一个由所有父类组成的元组）
* __del__: 析构函数

## 继承

```Python
class Person:
    age = 0


class Employee(Person):
    salary = 0.0

```

1. 如果在子类中需要父类的构造方法就需要显式的调用父类的构造方法，或者不重写父类的构造方法。详细说明可查看：[ python 子类继承父类构造函数说明](https://www.runoob.com/w3cnote/python-extends-init.html)。
2. 在调用基类的方法时，需要加上父类的类名前缀，且需要带上 self 参数变量。区别在于类中调用普通函数时并不需要带上 self 参数
3. Python 总是首先查找对应类型的方法，如果它不能在派生类中找到对应的方法，它才开始到父类中逐个查找。（先在本类中查找调用的方法，找不到才去父类中找）。

如果在继承元组中列了一个以上的类，那么它就被称作"多重继承" 。

### 继承检测

* ​`issubclass()`​ - 布尔函数判断一个类是另一个类的子类或者子孙类，语法：issubclass(sub,sup)
* ​`isinstance(obj, Class)`​ 布尔函数如果obj是Class类的实例对象或者是一个Class子类的实例对象则返回true。

## 方法重写

没有注解，直接def同名函数即可覆盖

下表列出了一些通用的功能，你可以在自己的类重写：

|序号|方法, 描述 & 简单的调用|
| ------| -----------------------------------------------------|
|1| **__init__**   **( self [,args...] )** <br />构造函数<br />简单的调用方法: *obj*  *=*  *className(args)*|
|2| **__del__( self )** <br />析构方法, 删除一个对象<br />简单的调用方法 : *del obj*|
|3| **__repr__( self )** <br />转化为供解释器读取的形式<br />简单的调用方法 : *repr(obj)*|
|4| **__str__( self )** <br />用于将值转化为适于人阅读的形式<br />简单的调用方法 : *str(obj)*|
|5| **__cmp__**   **( self, x )** <br />对象比较<br />简单的调用方法 : *cmp(obj, x)*|

## 运算符重载

```Python
class Vector:
    def __init__(self, a, b):
        self.a = a
        self.b = b

    def __str__(self):
        return "Vector (%d, %d)" % (self.a, self.b)

    def __add__(self, other):
        return Vector(self.a + other.a, self.b + other.b)


v1 = Vector(2, 10)
v2 = Vector(5, -2)
print(v1 + v2)
```

## 私有属性和方法

添加`__`​即设置变量或方法为private

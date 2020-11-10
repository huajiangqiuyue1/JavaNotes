### JDK1.8新特性

![image-20201018164440295](http://markdown.xiaonainiu.top/img/image-20201018164440295.png)



### 注解

Annotation（注解）是 Java 提供的一种对元程序中元素关联信息和元数据（metadata）的途径
和方法。Annatation(注解)是一个接口，程序可以通过反射来获取指定程序中元素的 Annotation
对象，然后通过该 Annotation 对象来获取注解中的元数据信息。

#### 4  种标准 元注解

元注解的作用是负责注解其他注解。 Java5.0 定义了 4 个标准的 meta-annotation 类型，它们被
用来提供对其它 annotation 类型作说明。

##### @Target 修饰的对象范围

@Target说明了Annotation所修饰的对象范围： Annotation可被用于 packages、types（类、
接口、枚举、Annotation 类型）、类型成员（方法、构造方法、成员变量、枚举值）、方法参数
和本地变量（如循环变量、catch 参数）。在 Annotation 类型的声明中使用了 target 可更加明晰
其修饰的目标

##### @Retention 定义 被保留的时间长短

Retention 定义了该 Annotation 被保留的时间长短：表示需要在什么级别保存注解信息，用于描
述注解的生命周期（即：被描述的注解在什么范围内有效），取值（RetentionPoicy）由：

- SOURCE:在源文件中有效（即源文件保留）
- CLASS:在 class 文件中有效（即 class 保留)
- RUNTIME:在运行时有效（即运行时保留）

##### @Documented  描述-javadoc

@ Documented 用于描述其它类型的 annotation 应该被作为被标注的程序成员的公共 API，因
此可以被例如 javadoc 此类的工具文档化。
@Inherited  阐述了某个被标注的类型是被继承的
@Inherited 元注解是一个标记注解，@Inherited 阐述了某个被标注的类型是被继承的。如果一
个使用了@Inherited 修饰的 annotation 类型被用于一个 class，则这个 annotation 将被用于该
class 的子类。

### 反射机制

#### 什么是Java反射机制？

Java反射机制是在运行状态中，对任意一个类，都能够知道这个类的所有方法和属性；对任意一个对象，都能够调用任意一个方法；这种动态获取以及动态调用对象的方法功能成为Java反射机制。

#### 反射机制提供了那些功能？

-  在运行时判定任意一个对象所属的类
- 在运行时构造任意一个类的对象
- 在运行时判定任意一个类所具的成员变量和方法；
- 在运行时调运任意一对象的方法
- 生成动态代理

获得class的几种方式

![image-20201007092424214](http://markdown.xiaonainiu.top/img/image-20201007092424214.png)

#### 反射机制的应用场景

- 逆向代码，例如反编译
- 与注解结合的框架 如Retrofit（网络加载）
- 动态生成类框架 Gson




























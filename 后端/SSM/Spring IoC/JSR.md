# JSR

理解JSR系列注解

JSR（Java Specification Requests）是Java平台标准化进程中的一种技术规范，而JSR注解是其中一部分重要的内容。按照JSR的分类以及注解语义的不同，可以将JSR注解分为不同的系列，主要有以下几个系列：

1. JSR-175: 这个JSR是Java SE 5引入的，是Java注解最早的规范化版本，Java SE 5后的版本中都包含该JSR中定义的注解。主要包括以下几种标准注解：

* ​`@Deprecated`​: 标识一个程序元素（如类、方法或字段）已过时，并且在将来的版本中可能会被删除。
* ​`@Override`​: 标识一个方法重写了父类中的方法。
* ​`@SuppressWarnings`​: 抑制编译时产生的警告消息。
* ​`@SafeVarargs`​: 标识一个有安全性警告的可变参数方法。
* ​`@FunctionalInterface`​: 标识一个接口只有一个抽象方法，可以作为lambda表达式的目标。

1. JSR-250: 这个JSR主要用于在Java EE 5中定义一些支持注解。该JSR主要定义了一些用于进行对象管理的注解，包括：

* ​`@Resource`​: 标识一个需要注入的资源，是实现Java EE组件之间依赖关系的一种方式。
* ​`@PostConstruct`​: 标识一个方法作为初始化方法。
* ​`@PreDestroy`​: 标识一个方法作为销毁方法。
* ​`@Resource.AuthenticationType`​: 标识注入的资源的身份验证类型。
* ​`@Resource.AuthenticationType`​: 标识注入的资源的默认名称。

1. JSR-269: 这个JSR主要是Java SE 6中引入的一种支持编译时元数据处理的框架，即使用注解来处理Java源文件。该JSR定义了一些可以用注解标记的注解处理器，用于生成一些元数据，常用的注解有：

* ​`@SupportedAnnotationTypes`​: 标识注解处理器所处理的注解类型。
* ​`@SupportedSourceVersion`​: 标识注解处理器支持的Java源码版本。

1. JSR-330: 该JSR主要为Java应用程序定义了一个依赖注入的标准，即Java依赖注入标准（javax.inject）。在此规范中定义了多种注解，包括：

* ​`@Named`​: 标识一个被依赖注入的组件的名称。
* ​`@Inject`​: 标识一个需要被注入的依赖组件。
* ​`@Singleton`​: 标识一个组件的生命周期只有一个唯一的实例。

1. JSR-250: 这个JSR主要是Java EE 5中定义一些支持注解。该JSR包含了一些支持注解，可以用于对Java EE组件进行管理，包括：

* ​`@RolesAllowed`​: 标识授权角色
* ​`@PermitAll`​: 标识一个活动无需进行身份验证。
* ​`@DenyAll`​: 标识不提供针对该方法的访问控制。
* ​`@DeclareRoles`​: 声明安全角色。

但是要理解JSR是Java提供的**技术规范**，也就是说，他只是规定了注解和注解的含义，**并不是直接提供特定的实现**，而是提供标准和指导方针，由第三方框架（Spring）和库来实现和提供对应的功能。

‍

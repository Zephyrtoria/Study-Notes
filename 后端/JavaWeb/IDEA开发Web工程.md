# IDEA开发Web工程

# IDEA中开发并部署运行Web项目

1. 简历Tomcat和IDEA的关联
2. 使用IDEA创建一个JavaWeb工程，在Web工程中开发代码
3. 使用IDEA将工程构建成一个可以发布的APP
4. 使用IDEA将构建好的APP部署到Tomcat中，启动运行

## IDEA关联本地Tomcat

> 可以在创建项目前设置本地tomcat,也可以在打开某个项目的状态下找到settings

​![image](assets/image-20240704215756-ymxkf1a.png)​

> 找到 Build,Execution,Eeployment下的Application Servers ,找到+号

​![image](assets/image-20240704215827-y7rb6fc.png)​

> 选择Tomcat Server

​![image](assets/image-20240704215905-9qpi6or.png)​

> 选择tomcat的安装目录

​![image](assets/image-20240704215908-10bs8rn.png)​

> 点击ok

​![image](assets/image-20240704215914-1lvxi77.png)​

> 关联完毕

​![image](assets/image-20240704215918-842swj9.png)​

## IDEA创建Web工程

> 推荐先创建一个空项目,这样可以在一个空项目下同时存在多个modules,不用后续来回切换之前的项目,当然也可以忽略此步直接创建web项目

​![image](assets/image-20240704220738-mp2k50q.png)​

​![image](assets/image-20240704220742-ylp4k53.png)​

> 检查项目的SDK,语法版本,以及项目编译后的输出目录

​![image](assets/image-20240704220753-idce0m4.png)​

​![image](assets/image-20240704220746-811820e.png)​

> 先创建一个普通的JAVA项目

​![image](assets/image-20240704220800-gj9omay.png)​

> 检查各项信息是否填写有误

​![image](assets/image-20240704220804-sf6ffr3.png)​

> 创建完毕后,为项目添加Tomcat依赖

​![image](assets/image-20240704220809-8jkuy44.png)​

​![image](assets/image-20240704220812-txsr7fc.png)​

​![image](assets/image-20240704220815-c61ushk.png)​

> 选择modules,添加 framework support
>
> 注意新版中需要到：help -> find action 或 双击Shift 中搜索

​![image](assets/image-20240704220819-n13hg5t.png)​

> 选择Web Application 注意Version,勾选 Create web.xml

​![image](assets/image-20240704220822-fiudo1c.png)​

> 删除index.jsp ,替换为 index.html

​![image](assets/image-20240704220826-n1wqtm2.png)​

​![image](assets/image-20240704220829-wdkasi2.png)​

### 处理配置文件

* 在工程下创建resources目录,专门用于存放配置文件(都放在src下也行,单独存放可以尽量避免文件集中存放造成的混乱)
* 标记目录为资源目录,不标记的话则该目录不参与编译

​![image](assets/image-20240704220833-978r650.png)​

* 标记完成后,显示效果如下

​![image](assets/image-20240704220836-tguf7zj.png)​

### 处理依赖jar包问题

* 在WEB-INF下创建lib目录
* 必须在WEB-INF下,且目录名必须叫lib!!!
* 复制jar文件进入lib目录

​![image](assets/image-20240704220840-16tjxz0.png)​

* 将lib目录添加为当前项目的依赖,后续可以用maven统一解决

​![image](assets/image-20240704220843-ztiymel.png)​

​![image](assets/image-20240704220847-kapbklf.png)​

* 环境级别推荐选择module 级别,降低对其他项目的影响,name可以空着不写

​![image](assets/image-20240704220851-pvncadr.png)​

* 查看当前项目有那些环境依赖

​![image](assets/image-20240704220854-l60jyk4.png)​

​![image](assets/image-20240704220858-vd359zy.png)​

* 在此位置,可以通过-号解除依赖

​![image](assets/image-20240704220901-lex0enq.png)​

## IDEA构建Web项目

这步操作可以省略，直接进行下一步的时候IDEA也会自动构建

​![image](assets/image-20240704223825-i208pww.png)​

​![image](assets/image-20240704223839-11wthno.png)​

生成可发布的APP：

​![image](assets/image-20240704223906-296e48c.png)​

项目中src和resources中的.java文件编译后的.class文件都会放入classes中

## IDEA部署-运行Web项目

> 检查idea是否识别modules为web项目并存在将项目构建成发布结构的配置

* 就是检查工程目录下,web目录有没有特殊的识别标记

​![image](assets/image-20240704220905-d9frolh.png)​

* 以及artifacts下,有没有对应 _war_exploded,如果没有,就点击+号添加

​![image](assets/image-20240704220908-25vk5li.png)​

> 点击向下箭头,出现 Edit Configurations选项

​![image](assets/image-20240704220912-tak6owp.png)​

> 出现运行配置界面

​![image](assets/image-20240704220915-1lvywfe.png)​

> 点击+号,添加本地tomcat服务器

​![image](assets/image-20240704220918-px9fz2w.png)​

> 如果IDEA只关联了一个Tomcat,红色部分就只有一个Tomcat可选

​![image](assets/image-20240704220922-56kgw99.png)​

> 选择Deployment,通过+添加要部署到Tomcat中的artifact

​![image](assets/image-20240704220925-21id9nu.png)​

> applicationContext中是默认的项目上下文路径,也就是url中需要输入的路径,这里可以自己定义,可以和工程名称不一样,也可以不写,但是要保留/,我们这里暂时就用默认的

​![image](assets/image-20240704220930-vsrr0on.png)​

> 点击apply 应用后,回到Server部分. After Launch是配置启动成功后,是否默认自动打开浏览器并输入URL中的地址,HTTP port是Http连接器目前占用的端口号

​![image](assets/image-20240704220935-u8ortyv.png)​

> 点击OK后,启动项目,访问测试

* 绿色箭头是正常运行模式
* "小虫子"是debug运行模式

​![image](assets/image-20240704220940-oliawx1.png)​

* 点击后,查看日志状态是否有异常

​![image](assets/image-20240704220943-10ir17w.png)​

* 浏览器自动打开并自动访问了index.html欢迎页

​![image](assets/image-20240704220947-z8dhyus.png)​

### 工程结构和可以发布的项目结构之间的目录对应关系

​![image](assets/image-20240704220950-00pao67.png)​

### IDEA部署并运行项目的原理

idea并没有直接进将编译好的项目放入Tomcat的webapps中，而是根据关联的Tomcat，创建了一个Tomcat副本，将项目部署到了这个副本中

idea的Tomcat副本在C:\用户\当前用户\AppData\Local\JetBrains\IntelliJIdea2022.2\tomcat\中

这个副本并不是一个完整的tomcat,副本里只是准备了**和当前项目相关的配置文件**而已

idea启动tomcat时，是让本地tomcat程序按照tomcat副本里的配置文件运行

idea的tomcat副本部署项目的模式是通过conf/Catalina/localhost/*.xml配置文件的形式实现项目部署的

​![image](assets/image-20240704220955-b1ihwy2.png)​

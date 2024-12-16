# CentOS 7.6 安装

# 安装CentOS7.6

---

l 检查BIOS虚拟化支持

​![](assets/wps1-20240717220820-wbkciwm.jpg)​

l 新建虚拟机

​![](assets/wps2-20240717220820-s3bv6te.jpg)​

​![](assets/wps3-20240717220820-x5k12oh.jpg)​

​![](assets/wps4-20240717220820-zt3f93e.jpg)​

​![](assets/wps5-20240717220820-iwh0rxe.jpg)​

​![](assets/wps6-20240717220820-e8jacuh.jpg)​

​![](assets/wps7-20240717220820-8th9rzn.jpg)​

l 配置虚拟机的内存

​![](assets/wps8-20240717220820-dpi41zm.jpg)​

l 配置处理器， **分配的处理器内核多，虚拟机速度**快

​![](assets/wps9-20240717220820-4rknz34.jpg)​

l 配置网络

​![](assets/wps10-20240717220820-6h71gj1.jpg)​![](assets/wps11-20240717220820-mj4d7i7.jpg)​

l 正式安装Centos系统

​![](assets/wps12-20240717220820-mtf1jpd.jpg)​

​![](assets/wps13-20240717220820-jherzi3.jpg)​

l 说明: 选择第一个，不需要 Test this media ，否则检测时间很长

​![](assets/wps14-20240717220820-dswaakz.jpg)​

​![](assets/wps15-20240717220820-x7mtzy1.jpg)​

l 选择安装软件，默认是最小化安装.

​![](assets/wps16-20240717220820-b9rxj8s.jpg)​

l 软件选择(套餐)，需要什么，安装好后也可以再安装。**也可以根据需要勾选附加** 项

， 比如这里我勾选了兼容库和基本开发工具(jdk,gcc), 安装好后，也可以卸载，更新等操作

​![](assets/wps17-20240717220820-t2b63bn.jpg)​

l 安装位置，进行分区操作

​![](assets/wps18-20240717220820-tf6uoxt.jpg)​

​![](assets/wps19-20240717220820-u9hl5y5.jpg)​

​![](assets/wps20-20240717220820-ao90vgl.jpg)​

l 先指定/boot   分区，即引导分区，大小为1G, 然后**点击添加挂载点**.

​![](assets/wps21-20240717220820-fsk4tl4.jpg)​

​![](assets/wps22-20240717220820-yfvcn78.jpg)​

​![](assets/wps23-20240717220820-xsvvo39.jpg)​

l 指定swap分区设备类型和文件系统

​![](assets/wps24-20240717220820-vhy3unv.jpg)​

​![](assets/wps25-20240717220820-evo9naw.jpg)​

​![](assets/wps26-20240717220820-7fx1y5r.jpg)​

​![](assets/wps27-20240717220820-vs7l1d1.jpg)​

​![](assets/wps28-20240717220820-euw2xtc.jpg)​

​![](assets/wps29-20240717220820-ozmxr62.jpg)​

​![](assets/wps30-20240717220820-3vy3x22.jpg)​

l 设置网络和主机名, 安装好后也可以设置

​![](assets/wps31-20240717220820-7b70j4i.jpg)​

l 设置你的主机名，然后点击完成即可.

​![](assets/wps32-20240717220820-iqkd837.jpg)​

l 点击开始安装就开始了

​![](assets/wps33-20240717220820-fggrm0n.jpg)​

​![](assets/wps34-20240717220820-rdaga94.jpg)​

l 注意：在实际生产环境，密码一定要复杂，否则容易造成安全隐患

​![](assets/wps35-20240717220820-w57zheb.jpg)​

l 创建其它用户，也可以安装成功后，再创建

​![](assets/wps36-20240717220820-hnwlb7u.jpg)​

​![](assets/wps37-20240717220820-hv7z0zu.jpg)​

l 完成后面的设置

​![](assets/wps38-20240717220820-wuymi58.jpg)​

​![](assets/wps39-20240717220820-a3aioe0.jpg)​

l 默认以普通用户登录,可以切换成root, 点击未列出

​![](assets/wps40-20240717220820-wz2o8xg.jpg)​

​![](assets/wps41-20240717220820-sx8lrls.jpg)​

​![](assets/wps42-20240717220820-golo277.jpg)​

​![](assets/wps43-20240717220820-xuvia3i.jpg)​

​![](assets/wps44-20240717220820-1l8j704.jpg)​

​![](assets/wps45-20240717220820-w8rly91.jpg)​

​![](assets/wps46-20240717220820-ip7p5gg.jpg)​

​![](assets/wps47-20240717220820-0u5t2yh.jpg)​

l 连接网络，就可以上网了

​![](assets/wps48-20240717220820-cw23t8j.jpg)​

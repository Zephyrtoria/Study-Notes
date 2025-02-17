# npm设置

> 1.安装

* 安装 node，自动安装 npm 包管理工具！

> 2.配置依赖下载使用阿里镜像

* npm 安装依赖包时默认使用的是官方源，由于国内网络环境的原因，有时会出现下载速度过慢的情况。为了解决这个问题，可以配置使用阿里镜像来加速 npm 的下载速度，具体操作如下：
* 打开命令行终端，执行以下命令，配置使用阿里镜像：
* 原来的 [registry.npm.taobao.org](http://registry.npm.taobao.org) 已替换为 [registry.npmmirror.com](http://registry.npmmirror.com)

```shell
npm config set registry https://registry.npmmirror.com
```

* 确认配置已生效，可以使用以下命令查看当前 registry 的配置：如果输出结果为 `https://registry.npmmirror.com`​，说明配置已成功生效。

```shell
npm config get registry
```

* 如果需要恢复默认的官方源，可以执行以下命令：

```javascript
npm config set registry https://registry.npmjs.org/
```

> 3.配置全局依赖下载后存储位置

* 在 Windows 系统上，npm 的全局依赖默认安装在 `<用户目录>\AppData\Roaming\npm`​ 目录下。
* 如果需要修改全局依赖的安装路径，可以按照以下步骤操作：

  1. 创建一个新的全局依赖存储目录，例如 `D:\GlobalNodeModules`​。
  2. 打开命令行终端，执行以下命令来配置新的全局依赖存储路径：

     ```shell
     npm config set prefix "D:\GlobalNodeModules"
     ```
  3. 确认配置已生效，可以使用以下命令查看当前的全局依赖存储路径：

     ```shell
     npm config get prefix
     ```

> 4.升级 npm 版本

* cmd 输入 npm -v 查看版本
* 如果 node 中自带的 npm 版本过低！则需要升级至 9.6.6！

```shell
npm install -g npm@9.6.6
```

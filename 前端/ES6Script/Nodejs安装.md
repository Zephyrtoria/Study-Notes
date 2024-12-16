# Nodejs安装

1. 打开官网[https://nodejs.org/en下载对应操作系统的](https://nodejs.org/en%E4%B8%8B%E8%BD%BD%E5%AF%B9%E5%BA%94%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F%E7%9A%84) LTS 版本。
2. 双击安装包进行安装，安装过程中遵循默认选项即可(或者参照[https://www.runoob.com/nodejs/nodejs-install-setup.html](https://www.runoob.com/nodejs/nodejs-install-setup.html) )。安装完成后，可以在命令行终端输入 `node -v`​ 和 `npm -v`​ 查看 Node.js 和 npm 的版本号。

​![1687765256680](assets/1687765256680-20240727094826-kzlpg9k.png)​

3. 定义一个app.js文件,cmd到该文件所在目录,然后在dos上通过`node app.js`​命令即可运行

```javascript
function sum(a,b){
    return a+b;
}
function main(){
    console.log(sum(10,20))
}
main()
```

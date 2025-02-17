# HTML

# HTML

[HTML学习网站](https://www.w3school.com.cn/html/index.asp)

用于页面主体的搭建

**超文本**：HTML本质上是文本，但是通过标签引入其他资源到网页中，本身是文本但是最终呈现效果超越了文本

**标记语言**：由一系列标签组成

1. **浏览器**负责解析和展示.html文件
2. .html文件时纯文本工具，一般编辑工具都可以编辑

## 概念词汇

* 标签 tag 页面上的一对（一个）尖角号

  ​`<p>Exusiai</p>`​  双标签

  ​`<input type="text" name="username" />`​  单标签
* 属性 attribute  对标签特征进行设置的一种方式，一般定义开始标签中

  ​`<a href="http"></a>`​中的href

  ​`<input type="password" />`​
* 文本 text  双标签之间的文字
* 元素 element  （开始标签+属性+文本标签+结束标签） = 一个元素

## 基础结构

```HTML
<!--
    1. <html></html>是html文件的根标签，其他所有标签都要放在其中
    2. 根标签中有两个一级子标签：
        <head></head>  头标签：定义不直接展示在页面上，但是有重要作用的内容，如：
                        1. 字符集 <meta charset="utf-8"/>
                        2. css引入
                        3. js引入
                        4. 其他
        <body></body>  体标签：定义要展示到页面主题的标签
-->
<!DOCTYPE html>
<!--HTML5版本的文档声明。因为当前基本都是使用这个版本，所以可以没有-->
<html>
  <head>
    <title>My first page</title>
    <!--标签名-->
    <meta charset="utf-8" />
    <!--字符集，要保持这个html文件的编码方式和这里写的一样-->
  </head>
  <body>
    <h1>Love study</h1>
  </body>
</html>
```

## 语法细节

1. 根标签<html></html>有且只有一个
2. 单标签和双标签都要正确关闭
3. 标签可以嵌套但不能交叉嵌套

    ​`<i><big>Exusiai</big></i>`​或`<big><i>Exusiai</i></big>`​都可以

    但是`<big><i>Exusiai</big></i>`​不允许
4. 注释语法为`<!-- -->`​
5. 属性必须有值，属性值需要加引号
6. 不区分单引号双引号，但是不能混用，引号内部嵌套引号，需要单双引号交替出现
7. 不严格区分大小写，但是开始标签和结束标签需要对应，而且不能大小写混用，必须全为大写或全为小写
8. 不允许出现自定义标签

## 常见标签

### h/p/br/hr标题、段落、换行

```HTML
<!DOCTYPE html>
<!--HTML5版本的文档声明。因为当前基本都是使用这个版本，所以可以没有-->
<html>
  <head>
    <title>My first page</title>
    <!--标签名-->
    <meta charset="utf-8" />
    <!--字符集，要保持这个html文件的编码方式和这里写的一样-->
  </head>
  <body>
    <!--
            标题  h1 - h6
            段落  p
            换行  br
			分割  hr  
        -->
    <h1>Exusiai</h1>
    <h2>Exusiai</h2>
    <h3>Exusiai</h3>
    <h4>Exusiai</h4>
    <h5>Exusiai</h5>
    <h6>Exusiai</h6>
    <hr />
    <p>
      E<br />
      Exusiai<br />
    </p>
  </body>
</html>
```

### ol/ul/li列表标签

列表可嵌套

```HTML
<!DOCTYPE html>
<!--HTML5版本的文档声明。因为当前基本都是使用这个版本，所以可以没有-->
<html>
  <head>
    <title>My first page</title>
    <!--标签名-->
    <meta charset="utf-8" />
    <!--字符集，要保持这个html文件的编码方式和这里写的一样-->
  </head>
  <body>
    <!--
            有序列表  ol
            无序列表  ul
            列表项  li
        -->
    <ol>
      <li>数据类型</li>
      <li>变量</li>
      <li>流程控制</li>
    </ol>
    <ul>
      <li>Java</li>
      <li>C/C++</li>
      <li>Go</li>
    </ul>
  </body>
</html>
```

### a超链接标签

```HTML
<!DOCTYPE html>
<!--HTML5版本的文档声明。因为当前基本都是使用这个版本，所以可以没有-->
<html>
  <head>
    <title>My first page</title>
    <!--标签名-->
    <meta charset="utf-8" />
    <!--字符集，要保持这个html文件的编码方式和这里写的一样-->
  </head>
  <body>
    <!--
            <a>
                href  用于定义要跳转的目标资源的地址
                    1. 完整的url
                    2. 相对路径  以当前资源的所在路径为出发点寻找目标资源
                                相对路径可以以 ./ 开头，当前资源所在路径，可以省略不写
                                或以 ../ 开头，则返回该资源所在的上一层次，可以使用多次 ../../返回上两层
                    3. 绝对路径  无论当前资源在哪里，始终以固定的位置作为出发点去找目标资源
                                以 / 开头
                target  用于定义目标资源的打开方式
                    1. _self  在当前窗口打开目标资源
                    2. _blank  开启新窗口打开目标资源
        -->
    <a href="https://cn.bing.com/" target="_blank">必应</a>
    <a href="b.html" target="_self">b</a>
  </body>
</html>
```

### img/audio/video多媒体标签

```HTML
<!DOCTYPE html>
<!--HTML5版本的文档声明。因为当前基本都是使用这个版本，所以可以没有-->
<html>
  <head>
    <title>My first page</title>
    <!--标签名-->
    <meta charset="utf-8" />
    <!--字符集，要保持这个html文件的编码方式和这里写的一样-->
  </head>
  <body>
    <!--
            img  插入图片
                src  定义图片路径
                    1. url
                    2. 相对路径
                    3. 绝对路径
                title  定义鼠标悬停时提示的文字
                alt  定义图片加载失败时显示的文字
                width  设置宽度
			audio  插入音频
			video  插入视频
        -->
    <img
      src="img/114185356_p0.jpg"
      title="Exusiai"
      alt="能天使"
      width="300px"
    />
  </body>
</html>
```

### table表格标签

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <!--
            table  整张表格
                thaed  表头
                tbody  表体
                tfoot  表尾
                    tr  表格中的一行
                        td  行中的一个单元格
                        th  自带加粗居中效果的td
        -->
    <!--
            可以都不加thead/tbody/tfoot，浏览器解析网页时会自动加上tbody
        -->
    <h3>香草榜</h3>
    <table border="1px" style="margin: 0px; width: 300px">
      <thead>
        <tr>
          <th>排名</th>
          <td>姓名</td>
          <td>分数</td>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>1</th>
          <td>Exusiai</td>
          <td>99999</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Skadi</td>
          <td>88888</td>
        </tr>
      </tbody>
      <tfoot></tfoot>
    </table>
  </body>
</html>
```

#### 单元格跨行

使用`rowspan`​和`colspan`​

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <h3>香草榜</h3>
    <table border="1px" style="margin: 0px; width: 300px">
      <thead>
        <tr>
          <th>排名</th>
          <td>姓名</td>
          <td>分数</td>
          <td>备注</td>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>1</th>
          <td>Exusiai</td>
          <td>99999</td>
          <td rowspan="6">超级香草</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Skadi</td>
          <td>88888</td>
        </tr>
        <tr>
          <th>3</th>
          <td>Surtr</td>
          <td>77777</td>
        </tr>
        <tr>
          <td>总人数</td>
          <td colspan="2">200</td>
        </tr>
        <tr>
          <td>平均分</td>
          <td colspan="2">55555</td>
        </tr>
        <tr>
          <td>及格率</td>
          <td colspan="2">66%</td>
        </tr>
      </tbody>
      <tfoot></tfoot>
    </table>
  </body>
</html>

```

### form表单标签

可以实现让用户在界面上输入各种信息并提交，是向服务器发送数据的主要方式之一

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <!--
            form
                action  定义数据的提交地址
                    1. url
                    2. 相对路径
                    3. 绝对路径
          
                method  定义数据的提交方式
                    GET  
                        1. 参数会以键值对形式放在url后面进行提交 url?key=value&key=value&key=value
                        2. 但是数据会直接暴露在地址栏中
                        3. 且地址栏中的地址长度有限，提交的数据量不大
                        4. 地址栏上只能是字符，不能提交文件
                        5. 相比于post，效率更高
                    POST
                        1. 参数默认不放到url后面
                        2. 数据不会直接暴露在地址栏上，相对安全
                        3. 数据时单独打包通过请求体发送，提交的数据量可以很大
                        4. 请求体中可以是字符，也可以是字节数据，可以提交文件
                        5. 相比于get，效率略低（但可以忽略）
                    PUT
                    DELETE
                    ...

            表单项标签
            一定要定义name属性，用于明确提交时的参数名
            value属性，用于明确提交时的实参，不写则一定要手动输入，写了则为默认值
                input
                    type= 输入信息的表单项类型
                        text  单行普通文本框
                        password  密码框
                        submit  提交按钮
                        reset  重置按钮
        -->
    <form action="welcome.html" method="get">
      <!-- 添加表单项标签（用户输入信息的标签） -->
      Username:<input type=""text" name="username" value="Exusiai"/> <br />
      Password:<input type="password" name="password" value="123456" /> <br />
      <input type="submit" value="Sign In" />
      <input type="reset" value="Clear" />
    </form>
  </body>
</html>

```

#### input/textArea/select更多表单标签

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <!--
        input
            type 输入信息的表单项类型
                text  单行普通文本框
                password  密码框
                submit  提交按钮
                reset  重置按钮
                radio  单选框：
                        1. 多个单选框使用相同的name属性值，就会有互斥效果
                        2. 需要手动指定value值作为传递参数
                        3. checked="checked"或checked，代表默认勾选，一般只在其中一项写就行了
                checkbox  复选框
                hidden  隐藏域：不显示在页面上，但是提交时会携带。
                            希望用户提交一些特定信息，但是考虑安全问题或用户操作问题，不希望该数据发生改变
                file  文件
            name
            value
            readonly  只读：不可修改，但是会进行传递
            disabled  不可用：不可修改，也不会传递


        textArea  文本域、多行文本框
                没有value属性

        select  下拉框
            option  代表一个选项
            value  代表传递信息，不写的话传递<option>包裹的文本
            selected  默认选择
    -->
    <form action="welcome.html" method="get">
      <!-- 添加表单项标签（用户输入信息的标签） -->
      <input type="hidden" name="id" value="1224" /><br />
      <input type="text" name="pid" value="4221" readonly /> <br />
      <!-- 只读：不可修改，但是会进行传递 -->
      <input type="text" name="tid" value="1234" disabled /> <br />
      <!-- 不可用：不可修改，也不会传递 -->
      Username:<input type=""text" name="username" value="Exusiai"/> <br />
      Password:<input type="password" name="password" value="123456" /> <br />
      Gender:
      <input type="radio" name="gender" value="1" checked /> Male
      <input type="radio" name="gender" value="2" /> Female
      <br />
      Hobby:
      <input type="checkbox" name="hobby" value="1" />Basketball
      <input type="checkbox" name="hobby" value="2" />Football
      <input type="checkbox" name="hobby" value="3" />Baseball
      <br />
      Reseme:
      <textarea name="intro" style="width: 300px; height: 100px"></textarea>
      <br />
      Address:
      <select>
        <option value="1">大陆北方</option>
        <option value="2">大陆南方</option>
        <option value="3">大陆内地</option>
        <option value="0" selected>-请选择-</option>
      </select>
      <br />
      Logo:
      <input type="file" />
      <br />
      <input type="submit" value="Sign In" />
      <input type="reset" value="Clear" />
    </form>
  </body>
</html>
```

### css/div/span页面布局标签

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body style="background-color: antiquewhite">
    <!--
        css  设置样式
            通过元素的style属性进行设置
            style="样式名:样式值; 样式名:样式值; ..."

        div  块元素：自己独占一行（h1-h6也属于块元素）
            块元素的css样式的宽高一般都是生效的

        span  行内元素：不会自己独占一行（img也属于行内元素）
            行内元素的css样式的宽高很多都不生效的
            可以用来对单独某些文本进行修饰
    -->
    <div
      style="
        border: 1px solid red;
        width: 500px;
        height: 200px;
        margin: 10px;
        background-color: cadetblue;
      "
    >
      <span style="font-size: 100px; color: aqua">0</span>123
    </div>
    <div
      style="border: 1px solid red; width: 500px; height: 200px; margin: 10px"
    >
      456
    </div>
    <div
      style="border: 1px solid red; width: 500px; height: 200px; margin: 10px"
    >
      789
    </div>
  </body>
</html>

```

### 字符实体

[字符实体](https://www.w3school.com.cn/charsets/ref_html_8859.asp)

对于html代码来说，某些符号是有特殊含义（成为字符实体）的，如果想要显示这些特殊符号，需要进行转义。一般就是查看文档

​![image](assets/image-20240607213037-zmln23e.png)​

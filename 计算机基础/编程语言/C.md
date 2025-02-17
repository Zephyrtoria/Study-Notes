# C

# 环境配置

# 

[C/C++ VScode环境配置](https://zhuanlan.zhihu.com/p/87864677 "C/C++ VScode环境配置")

## VSCode简介

VSCode是一款微软出的轻量级编辑器，它本身只是一款文本编辑器而已，所有的功能都是以插件扩展的形式所存在，想用什么功能就安装对应的扩展即可，非常方便，同时也支持非常多的主题和图标，外观比较好看，重要的是VSCode支持各大主流操作系统，包括Windows、Linux和Mac OS。所以就选择它作为自己的一款主要的编辑器来使用。

## 一、下载

首先，我们直接去[VSCode官网](https://link.zhihu.com/?target=https%3A//code.visualstudio.com/)下载对应操作系统版本的安装包即可。因为我使用的是64位的Windows，所以下载的是64位的exe文件。此处需要注意一下，现在官网上给出了User Installer和System Installer两个安装版本，分别叫用户和系统级别的安装版本，参考官网给出的解释，区别在于安装User Installer版本不需要管理员权限，安装的位置是在用户的本地AppData目录，而System Installer的安装是需要管理员权限的，是安装在Program Files目录下的。我不清楚微软为什么要分User和System两个版本，可能是有自己的考虑吧。如果在官网首页处点击方框的下载按钮，默认下载的是User Installer版本。如果想要下载System版本的，可以点击右上角Download按钮，进而选择自己想要下载的版本。此处笔者下载的是System Installer版本。

​![](https://pic1.zhimg.com/80/v2-288149ad02ef1505e7a5275f86cef51c_720w.webp)​

## 二、安装

直接打开下载好的.exe文件进行安装即可。

​![](https://pic2.zhimg.com/80/v2-6999967dc8d4d3438879fd15ccaca8e5_720w.webp)​

此处选择安装位置，默认的是如图中位置，凭个人习惯即可，笔者仅将盘符改为D盘，其余保持不变。

​![](https://pic2.zhimg.com/80/v2-55cb90244dcee54ddc961dacf9f3b06d_720w.webp)​

​![](https://pic3.zhimg.com/80/v2-f1cfa4ce883349a765e12c8a08c24f2a_720w.webp)​

此处是设置一些额外功能，勾选上的话，以后在文件或者目录上单击鼠标右键会出现“通过Code打开”选项，会方便使用，大家可自行选择。最后一项是默认勾选的，可以在控制台打开VSCode，建议勾选。笔者此处除了“添加到PATH”默认的勾选项外，只额外勾选了“创建桌面快捷方式”选项。

​![](https://pic2.zhimg.com/80/v2-187ba8e3d18b45b518a7acf9c2b72a4d_720w.webp)​

接下来就是安装过程中的信息了，最后至此已成功安装VSCode。

​![](https://pic4.zhimg.com/80/v2-05eb13a53f8f092a65161e34cb9da6e7_720w.webp)​

## 三、设置中文环境

打开VSCode后，首先是欢迎界面。可以看到，这里默认的是英文环境。

​![](https://pic2.zhimg.com/80/v2-a176e699a27f34bd81cd2d486c281f3d_720w.webp)​

可能有人看着英文界面比较难受，下面介绍如何设置中文环境。现在中文环境也是通过安装扩展来实现，如下图，先点击侧边栏的扩展，然后在搜索框中输入language，选择“中文(简体)”进行安装，完成后重启VSCode即可。笔者这里只是实验一下步骤而已，实际使用过程中还是使用的英文界面，主要是笔者的英文水平太差，纯粹为了锻炼自己的英文习惯能力啦。

​![](https://pic1.zhimg.com/80/v2-f21191dcc3f14d0890328be18a48a3f0_720w.webp)​

​![](https://pic2.zhimg.com/80/v2-5128323a0e3608444d635c726b296ae5_720w.webp)​

## 四、完全卸载

如果大家之前有安装过VSCode，然后只是简单卸载的话，再次安装之后，是还出现之前的配置信息，包括打开的文件夹、安装过的扩展等，这是因为之前并没有完全将VSCode卸载干净。如果想干净卸载掉VSCode再重新安装的话，就需要在卸载之后再删除掉两个目录的内容。分别是：

* C:\Users\$用户名\.vscode
* C:\Users\$用户名\AppData\Roaming\Code【注】这里的“$用户名”根据自己的用户名而定。

删除掉这两个目录的内容之后，如果再安装VSCode的话，就相当于是全新安装了，即不会出现之前的相关配置信息了。

## 五、配置C/C++环境

前面已经介绍过，VSCode只是一款文本编辑器，不仅需要安装对应编程语言的扩展，还需要安装相应的编译器或者解释器。笔者这里首先需要的是C/C++的环境，所以先介绍如何配置C/C++的开发环境。如果后续笔者需要其他语言开发环境的时候，笔者再进行相应的记录并分享出来。 首先先创建一个文件夹，用来存放代码。此处建议不同的编程语言采用不同的文件夹，因为VSCode打开文件夹（称作工作目录）之后，如果进行一定的配置之后，会在该文件夹下产生一个叫".vscode"的文件夹，该文件夹中存放的是一些.json的配置文件，这些配置文件是对工作目录中的代码文件产生作用的。所以以后需要相同开发环境的时候，不用每次都去创建配置文件并进行相关配置，直接拷贝.vscode文件夹即可，但是第一次还是需要手动配置出自己所需的环境。

## 1.安装MinGW编译器

C/C++的编译器有很多种，大家可自行选择，笔者这里选择开源的MinGW编译器。大家可以从[sourceforge的mingw项目](https://link.zhihu.com/?target=https%3A//sourceforge.net/projects/mingw-w64/files/mingw-w64/mingw-w64-release/)上下载64位的编译器，直接打开进行安装，下图的笔者所选的选项。其中版本选最新版本，对语言的新特性有较好的支持；构架是32位和64位的选择，32位请选择x86；线程部分选择win32，如果是Linux请选择posix；异常模型部分选择默认的seh就好；最后一项只能选0。选好之后点击下一步。

​![](https://pic1.zhimg.com/80/v2-3aae1eb09e5b78b306706ee3ed8693ac_720w.webp)​

这里**要求**修改路径名称，确保路径中不包含**空格**和**中文**字符，尤其是空格，因为默认位置上有空格的，一定要修改相应安装的路径。因为官方文档中要求安装路径中不能含有空格，实际上也是如此，笔者之前有过编译器的路径存在空格字符，然后配置VSCode会无法识别出路径而导致失败（就是因为路径中包含空格字符）。

​![](https://pic3.zhimg.com/80/v2-ccdc30f87b6ebcd77858122300c7c04a_720w.webp)​

这是笔者设置的安装路径。

​![](https://pic3.zhimg.com/80/v2-8b6b4bde7374140965ec691c95825516_720w.webp)​

设置好安装路径之后，点击下一步就开始安装了。因为这是在线安装的，根据网速的大小时间会有所不同。安装好之后，就是熟悉的**配置环境变量**步骤，如下图：

​![](https://pic4.zhimg.com/80/v2-54e2f5cad1e2561ae1704450c11b9afb_720w.webp)​

最后，打开cmd，输入*gcc -v*验证是否成功即可。

## 2.安装C/C++扩展

用VSCode打开之前建立好的文件夹，可直接通过欢迎界面的*Open folder*打开，也可通过菜单栏的*File*-->*Open Folder*打开。笔者这里的文件夹目录是E:\Cpp。 在该文件夹下新建一个hello.cpp文件，马上右下角会出现安装C/C++的提示，可直接点击install按钮进行安装。

​![](https://pic4.zhimg.com/80/v2-25abea771f3b4c197c5b66af4b1a44bb_720w.webp)​

当然也可自行搜索C/C++扩展进行安装。

​![](https://pic1.zhimg.com/80/v2-dbbea9091e7ad31148e02d5a8940b134_720w.webp)​

下图是正在安装C/C++扩展的过程，需要一段时间，请静心等待。等右下角的提示消失了，说明安装成功，此时最好重启VSCode让扩展生效。

​![](https://pic2.zhimg.com/80/v2-b0e60d48a4d0111d6184870e03ac2db5_720w.webp)​

重启之后编写好hello.cpp文件后，如下图：

​![](https://pic1.zhimg.com/80/v2-cd6a0fed3e9250306f7c71e6eee7685c_720w.webp)​

## 3.配置C/C++环境

### (1).配置编译器

接下来配置编译器路径，按快捷键Ctrl+Shift+P调出命令面板，输入C/C++，选择“Edit Configurations(UI)”进入配置。这里配置两个选项： - 编译器路径：D:/mingw-w64/x86_64-8.1.0-win32-seh-rt_v6-rev0/mingw64/bin/g++.exe

```text
这里的路径根据大家自己安装的Mingw编译器位置和配置的环境变量位置所决定。
```

* IntelliSense 模式：gcc-x64

​![](https://pic4.zhimg.com/80/v2-cc609819e54faaa011535b8a1d78729f_720w.webp)​

​![](https://pic2.zhimg.com/80/v2-dd25492f14ef601faff48615533f8f39_720w.webp)​

​![](https://pic2.zhimg.com/80/v2-6285c8669d61d80a9b72b255e7d5c915_720w.webp)​

配置完成后，此时在侧边栏可以发现多了一个.vscode文件夹，并且里面有一个c_cpp_properties.json文件，内容如下，说明上述配置成功。现在可以通过Ctrl+<`快捷键打开内置终端并进行编译运行了。

```json
{
    "configurations": [
        {
            "name": "Win32",
            "includePath": [
                "${workspaceFolder}/**"
            ],
            "defines": [
                "_DEBUG",
                "UNICODE",
                "_UNICODE"
            ],
            //此处是编译器路径，以后可直接在此修改
            "compilerPath": "D:/mingw-w64/x86_64-8.1.0-win32-seh-rt_v6-rev0/mingw64/bin/g++.exe",
            "cStandard": "c11",
            "cppStandard": "c++17",
            "intelliSenseMode": "gcc-x64"
        }
    ],
    "version": 4
}
```

​![](https://pic3.zhimg.com/80/v2-3e36e62f0afac74b0961d7dd74cb800e_720w.webp)​

​![](https://pic3.zhimg.com/80/v2-305226dc6bf7198f2cad2686b511cc02_720w.webp)​

### (2).配置构建任务

接下来，创建一个tasks.json文件来告诉VS Code如何构建（编译）程序。该任务将调用g++编译器基于源代码创建可执行文件。 按快捷键Ctrl+Shift+P调出命令面板，输入tasks，选择“Tasks:Configure Default Build Task”：

​![](https://pic1.zhimg.com/80/v2-0f6d57783c5bfb9fe5c6c525ec2771e8_720w.webp)​

再选择“C/C++: g++.exe build active file”：

​![](https://pic1.zhimg.com/80/v2-91eedecc78231abd8d85e19998b2c3a4_720w.webp)​

此时会出现一个名为tasks.json的配置文件，内容如下：

```json
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558 
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "type": "shell",
            "label": "g++.exe build active file",//任务的名字，就是刚才在命令面板中选择的时候所看到的，可以自己设置
            "command": "D:/mingw-w64/x86_64-8.1.0-win32-seh-rt_v6-rev0/mingw64/bin/g++.exe",
            "args": [//编译时候的参数
                "-g",//添加gdb调试选项
                "${file}",
                "-o",//指定生成可执行文件的名称
                "${fileDirname}\\${fileBasenameNoExtension}.exe"
            ],
            "options": {
                "cwd": "D:/mingw-w64/x86_64-8.1.0-win32-seh-rt_v6-rev0/mingw64/bin"
            },
            "problemMatcher": [
                "$gcc"
            ],
            "group": {
                "kind": "build",
                "isDefault": true//表示快捷键Ctrl+Shift+B可以运行该任务
            }
        }
    ]
}
```

​![](https://pic3.zhimg.com/80/v2-8a3cb801cbccd4b25edfed14690e3982_720w.webp)​

### (3).配置调试设置

这里主要是为了在.vscode文件夹中产生一个launch.json文件，用来配置调试的相关信息。点击菜单栏的*Debug*-->*Start Debugging*：

​![](https://pic3.zhimg.com/80/v2-d3101a91ccf15d8313d670b204cecf1a_720w.webp)​

选择C++(GDB/LLDB)：

​![](https://pic3.zhimg.com/80/v2-a17abdb3713ab16406b4a62fb286bdce_720w.webp)​

紧接着会产生一个launch.json的文件：

​![](https://pic3.zhimg.com/80/v2-80ceb20669ebf4f88b733a820228752e_720w.webp)​

这里笔者遇到一个问题，如果是在编写好的c++代码文件页面进行上述过程，会一直报"Unable to create 'launch.json' file inside the '.vscode' folder (Cannot read property 'name' of undefined)."的错误，网上也没有找到相关的解决办法，就自己琢磨了半天，最后发现如果在之前已经创建好的json文件页面进行创建launch.json文件的过程，是可以正常进行的。笔者也没有弄懂这到底是什么原因。  *【注】如果大家在进行 tasks.json 和 launch.json 的配置时遇到问题，比如上述笔者所遇到的无法构建的问题，还请不要气馁，可以对所遇到的错误进行搜索查找，看看是否有解决方案，如果实在没有的话，大家可以直接在.vscode文件夹下手动创建这两个文件，并将相应内容复制进去，也可完成环境配置。*

接下来读者可以点击Add Configuration按钮自己添加配置，也可以直接将笔者配置好的json文件内容复制过去，因为些配置对新手不是特别友好，相关具体细节还是需要参考官方文档。下面是笔者的launch.json文件的内容：

```json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [

        {
            "name": "(gdb) Launch",
            "preLaunchTask": "g++.exe build active file",//调试前执行的任务，就是之前配置的tasks.json中的label字段
            "type": "cppdbg",//配置类型，只能为cppdbg
            "request": "launch",//请求配置类型，可以为launch（启动）或attach（附加）
            "program": "${fileDirname}\\${fileBasenameNoExtension}.exe",//调试程序的路径名称
            "args": [],//调试传递参数
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": true,//true显示外置的控制台窗口，false显示内置终端
            "MIMode": "gdb",
            "miDebuggerPath": "D:\\mingw-w64\\x86_64-8.1.0-win32-seh-rt_v6-rev0\\mingw64\\bin\\gdb.exe",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ]
        }
    ]
}
```

现编写一个debug.cpp文件测试调试，设置断点后，按下F5进入调试，如图成功调试， 左侧为变量内容：

​![](https://pic4.zhimg.com/80/v2-cc066b77f8e4a60d4e3c7ed50fd10a0b_720w.webp)​

## 六、结语

至此，VSCode的C/C++开发环境已经配置完成，建议大家配置成功后，将.vscode文件夹备份一份，以后需要的时候直接复制即可，不用再花时间进行配置了。 相信有了配置C/C++环境的基础，大家以后配置其他语言环境的时候就不会那么发怵了，赶快去体验VSCode这款好用的编辑器吧！

‍

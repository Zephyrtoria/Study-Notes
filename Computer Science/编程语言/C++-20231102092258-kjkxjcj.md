# C++

# debug

不确定是不是版本更新的缘故 现在创建完*.cpp(c++源代码)后，不需要按照原文【运行】【添加配置...】，而是按一下F5(【运行】【启动调试】) 然后直接选择"g++.exe - 生成和调试活动文件"就可以生成task.json并且自动开始调试了。

尽管launch.json并没有生成，后续都可以按F5一键进入调试了  
顺带一提

"g++.exe - 生成和调试活动文件"的配置能够同时调试C/C++(没有task.json时创建*.cpp文件按下F5时可选的配置)

"gcc.exe - 生成和调试活动文件"的配置仅能够调试C(没有task.json时创建*.c文件按下F5时可选的配置)

如果想要使用gcc的配置调试C++需要在task.json的args中后面加上 "-lstdc++"(注意要在上一项，比如"${fileDirname}\\${fileBasenameNoExtension}.exe"后面加上逗号)

# 输入优化

ios::sync_with_stdio(false)

用了之后cin cout和printf scanf不能共用

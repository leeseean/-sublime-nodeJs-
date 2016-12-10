# -sublime-nodeJs-
在sublime上搭建nodeJs环境
喜欢用sublime，而sublime里面也有编译系统 Build System，在sublime菜单上找到Tools ---> Build System，里面就列出了一些默认自带的Build System，但是没有nodejs。

新建nodejs Build System：

在sublime菜单上找到Tools ---> Build System ---> new Build System，复制下面的配置内容：
{
"cmd": ["node", "$file"],
"file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
"selector": "source.js",
"encoding":"utf-8",
// "encoding": "cp936",根据自己需要编码格式，防止乱码。
"shell":true,
"windows":
{
"cmd": ["taskkill","/F", "/IM", "node.exe","&","node", "$file"] 
},
"linux":
{
"cmd": ["killall node; node", "$file"]
}
}
然后保存，直接保持到默认目录即可，名字改为NodeJs.sublime-build。最后在菜单上找到Tools ---> NodeJs ，就代表已经生效。

编译方式：

在sublime打开需要编译的文件，直接快捷键CTRL B即可编译，在底部会显示log

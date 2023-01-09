
#  A、集成至Visual Studio

1）首先生成配置

//每个工程单独配置

.\vcpkg integrate project

//全局配置，暂时不用全局，因为各个工程各异可能有的工程想用其他版本的库

.\vcpkg integrate install

执行命令成功后会在“\scripts\buildsystems”目录下，生成nuget配置文件.

2）配置Nuget
在工程中点击菜单“工具”， 选择"NuGet 包管理器->程序包管理器设置".
添加新的源, 选择vcpkg目录下的“scripts\buildsystems”目录，然后点击右侧的“更新”按钮。点击“确定”按钮，关闭对话框。


#  B、查看支持的选项  
.\vcpkg.exe help triplet

#  C、安装包  
//json  
.\vcpkg.exe install jsoncpp:x64-windows-static-md  

//ffmpeg  
.\vcpkg.exe install ffmpeg:x64-windows  
.\vcpkg.exe install ffmpeg:x64-windows-static  
.\vcpkg.exe install ffmpeg:x64-windows-static-md  

#  D、直接引入  
可以看到在vs工程属性中多了一个 vcpkg 选项，不需要额外配置附加包含目录和库目录，把需要用到的库在上面的步骤中用vcpkg.exe安装好就可以了。

![image](https://user-images.githubusercontent.com/12092721/211269544-56789bcf-f6eb-4d28-a1fd-7e320ef6fcb7.png)

假设编译的是MD的静态库，则  
#include <json/json.h>  
#pragma comment(lib,"jsoncpp.lib")

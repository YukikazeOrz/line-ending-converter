# 使用说明
## 功能介绍
- 支持在不同操作系统上运行。
- 可将文件或目录中的文本文件的换行符统一转换为指定的系统所用的格式，如Windows（CRLF）、Linux（LF）、macOS(LF)。
- 支持跳过隐藏文件/文件夹或系统文件/文件夹或非纯文本文件。
- 生成详细的转换报告，包括每个文件转换前后的路径、转换状态、耗时等信息。
## 系统要求
- **操作系统：** Windows,Linux,macOS
- **编译器：** gcc,Visual Studio
## 编译及运行
- 1.在Windows上编译和运行
  
  · 使用Visual Studio创建新的C语言项目
  
  · 将所有文件添加到项目中
  
  · 编译并运行项目
  
- 2.在Linux上编译和运行

```Bash
$ sudo apt update
$ sudo apt install build-essential
$ cd /path/to/line-ending-converter
$ gcc -o line-ending-converter main.c file_utils.c line_ending_converter.c file_processor.c arg_parser.c -lm
$ ./line-ending-converter <input_path> <output_path> <system>
```
## 使用方法
```Bash
line-ending-converter <input_path> <output_path> <system>
```
- <input_path>: 输入文件或目录的路径。
- <output_path>: 输出文件或目录的路径。
- <system>: 要转换的系统换行符类型，可选值为 Windows, Linux, macOS。
***
# 软件结构图

***
# 软件流程图
![image](https://github.com/StairJumperWei/line-ending-converter/assets/42022174/37497064-4c33-45cb-b312-648908f43438)
***
# 测试报告
## 测试环境
- **测试系统：** Windows11，Ubuntu24.04
- **编译器：** Visual Studio 2022，GCC 11
## 测试用文件树状图
```Diff
input
├─.git
│      Setup.exe
│      SetupEngine.dll
│      SetupUi.dll
│
├─.ssh
│      Setup.exe
│      SetupEngine.dll
│      SetupUi.dll
│
├─Music
│      My Song.mp3
│
├─Picture
│      My Pet.jpg
│
├─System32
│      input.txt
│      input_Linux.txt
│      long_text.txt
│
├─Texture
│  │  .abc
│  │  input.txt
│  │  input_Linux.txt
│  │  long_text.txt
│  │
│  └─C Project
│          .git
│          Hello World.c
│
└─Video
        My Vlog.mp4
```
## 测试结果
- 1.不输入参数
![image](https://github.com/StairJumperWei/line-ending-converter/assets/42022174/6b858365-a5bd-43a6-90f1-107393d3da4f)
- 2.参数输入错误（路径名错误、系统名错误）
![image](https://github.com/StairJumperWei/line-ending-converter/assets/42022174/9d048a4f-203e-4ca2-9ea2-61cdba2ace32)
![image](https://github.com/StairJumperWei/line-ending-converter/assets/42022174/9d0a09d3-9b8c-4aaa-9ffe-db5421ef69e8)
- 3.正常运行

生成的文件树状图
```Diff
output
├─Music
├─Picture
├─Texture
│  │  input.txt
│  │  input_Linux.txt
│  │  long_text.txt
│  │
│  └─C Project
│          Hello World.c
│
└─Video
```
**生成的报告文件：**
![image](https://github.com/StairJumperWei/line-ending-converter/assets/42022174/30600de0-fd9e-4135-86b5-0e21a0328608)

**转换结果：**
![屏幕截图 2024-07-02 021648](https://github.com/StairJumperWei/line-ending-converter/assets/42022174/e5e7a545-28ca-4045-9af9-94291fc0f421)
***
- [x] 使用C语言编写应用程序，实现Windows、Linux、MacOS系统间的换行符格式转换。
- [x] 除换行符格式外，原文件中的文件内容不能改变。
- [x] 支持的文件格式包括.txt、.c、.cpp、.h、.hpp、Makefile、.log等纯文本格式。
- [x] 系统和隐藏目录和文件应忽略，如System32、.svn、.ssh、.gitconfig等。
- [x] 编写软件结构图、流程图，测试报告以及必要的使用说明（ReleaseNote）。
- [x] 应自行编写应用程序，禁止抄袭或在程序中直接调用三方软件实现该功能。
- [x] 应进行适当的函数封装，各函数/模块应遵循高内聚低耦合的设计原则。
- [x] 统一的编码格式和规范，代码整洁、美观、可读性高。
- [x] 支持批量（目录/子目录）转换。
- [x] 转换结束后，生成统计报告（包括源/目标文件全路径，转换前后的换行符格式，转换过程的执行结果[已转换/不需要转换/不支持的文件格式/错误]，耗时等信息）。
- [x] 基于模块化的设计，实现转换业务和系统平台分离，达到跨平台目的，即该程序可以在Windows（vs）和Ubuntu（gcc）上编译和运行。

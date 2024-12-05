
目录* [fliter 视图](https://github.com)
* [输出文件位置设置](https://github.com)
* [查看预处理结果](https://github.com)
* [将目标文件转换为可读的汇编](https://github.com):[豆荚加速器](https://yirou.org)
* [自定义程序入口](https://github.com)
* [调试时查看变量在内存中的具体值](https://github.com)
* [查看代码的反汇编](https://github.com)

# fliter 视图


visual studio默认是filter视图（中文为筛选器）


![image](https://img2024.cnblogs.com/blog/2594030/202412/2594030-20241204194151010-699515717.png)


项目下的是filter而非硬盘目录里实际的文件夹，这时新建的也是filter


![image](https://img2024.cnblogs.com/blog/2594030/202412/2594030-20241204194230025-1263093070.png)


想要查看硬盘目录里实际的文件夹，点击按钮“show all files（显示所有文件）”即可


![image](https://img2024.cnblogs.com/blog/2594030/202412/2594030-20241204194340472-1146530969.png)


# 输出文件位置设置


自定义输出文件位置：


右键项目，选择“Properties（属性）”\-\>“General”\-\>“Output Directory”“Intermediate Directory”（图中展示选项的中文）


![image](https://img2024.cnblogs.com/blog/2594030/202412/2594030-20241204195045853-1192575041.png)


注意“Configuration（配置）“为”All Configurations（所有配置）”，“Platform（平台）”为“All Platforms（所有平台）”


这边也给出大佬们喜欢用的设置：


Output Directory：`$(SolutionDir)bin\$(Platform)\$(Configuration)\`


Intermediate Directory：`$(SolutionDir)bin\intermediates\$(Platform)\$(Configuration)\`


如果你看不懂其指代的具体路径，对路径选择“Edit（编辑）”\-\>“Macros”即可查看


![image](https://img2024.cnblogs.com/blog/2594030/202412/2594030-20241204195956431-840800281.png)


应用后可以右键解决方案，选择“Clean Solution（清理解决方案）”即可去掉旧文件


# 查看预处理结果


首先简答介绍一下编译器的工作原理：编译器首先处理预处理语句，将头文件内容全部复制到代码文件中；其次编译器将所有C\+\+代码转化为机器码，每个cpp文件都被编译成一个目标文件（.obj）；最后将独立的目标文件合并成一个可执行文件


Visual Studio默认不输出预处理的结果，想要查看预处理结果需要在“Properties（属性）”\-\>“C/C\+\+”\-\>“Preprocessor”中，将“Preprocess to File”设置为“Yes”（确保编辑的是当前的配置），编译后机会输出预处理文件（.i）


![image](https://img2024.cnblogs.com/blog/2594030/202412/2594030-20241204201022988-1882197137.png)


# 将目标文件转换为可读的汇编


编译器编译文件时，每个cpp文件都被编译成一个目标文件（.obj），出于一些调试需求，我们可能需要阅读编译出的汇编语言


在“Properties（属性）”\-\>“C/C\+\+”\-\>“Output Files”中，修改“Assembler Output”即可


![image](https://img2024.cnblogs.com/blog/2594030/202412/2594030-20241204201623767-1892801913.png)


# 自定义程序入口


一个可执行文件一定是以main函数为入口吗？答案是否定的


在“Properties（属性）”\-\>“Linker”\-\>“Advanced”中，可以自定义Entry Point


![image](https://img2024.cnblogs.com/blog/2594030/202412/2594030-20241204202025720-971991799.png)


# 调试时查看变量在内存中的具体值


最常见的是用autos，locals和watch监视变量：


* autos（自动变量窗口）：显示当前行和前几行代码中使用的变量，以及下一个将要执行的行中的变量
* locals（局部变量窗口）：显示当前作用域中的所有局部变量及其值
* watch（监视窗口）：允许手动添加并监视任意变量、表达式或内存地址


![image](https://img2024.cnblogs.com/blog/2594030/202412/2594030-20241204202845955-1920727662.png)
（这里对象p的成员变量Name没有赋值）


一个更高级的方法是查看变量在内存中的具体值：“DEBUG”\-\>“Windows”\-\>“Memory”\-\>“Memory 1”


![image](https://img2024.cnblogs.com/blog/2594030/202412/2594030-20241204203327376-805657729.png)


在“Address”中输入变量的内存地址（别忘了使用`&`取址）即可找到变量在内存中的具体值


![image](https://img2024.cnblogs.com/blog/2594030/202412/2594030-20241204204039562-410933150.png)


这里我输入了一个字符串指针，其指向字面量`"hello"`，可以发现内存存储的内容对应了"hello"的 ASCII 编码，只不过由于是64位，因此字符串指针默认为8字节


![image](https://img2024.cnblogs.com/blog/2594030/202412/2594030-20241204204156891-601059671.png)


# 查看代码的反汇编


在调试时，右键“Go To Disassembly”


![image](https://img2024.cnblogs.com/blog/2594030/202412/2594030-20241204205349007-619193929.png)


![image](https://img2024.cnblogs.com/blog/2594030/202412/2594030-20241204205438426-823924806.png)



> 如文章有误或疏漏，欢迎评论指出
> 如有帮助，欢迎关注我的博客，后续也会更新其他的技术内容（坚持日更ing）



> 特别推荐 Cherno 的C\+\+课程，可以去某管订阅他的频道，B站也有转载



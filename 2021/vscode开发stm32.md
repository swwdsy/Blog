# 用vscode开发keil工程

## 开发环境

最近准备重新上手stm32的开发，但是keil使用起来非常令人恼火，跳转搜索之类的功能做的真的拉。所以找了几种避开keil编辑器的开发方式。

1. keil进行编译烧录，用一个好用的编辑器进行代码编辑。
2. vscode中配置好cmake 和 gcc以及 openocd，完成代码编辑，编译，仿真，烧录。
3. cubeide， 一款st自己推出的ide，好像是基于eclipse开发的。

权衡利弊之后，我选择了第一种方案。先说一说其他两种的优缺点。

第二种我是非常看好的，但是涉及的东西太多，现在没有太多精力折腾，先种个草，以后有空了研究一下。

第三种也是不错的选择，内置cubemx，可以完成很多自动化配置。缺点是DAPLink支持可能不是很好，而且更换ide对我来说还是有一定的试错成本的。

## 编辑器选择

选择了第一种方案之后，编辑器的选择就是下一个问题。网上用的比较多的是VSCode和SourceInsight。

虽然sourceInsight的文件架构显示和搜索功能更胜一筹，但是在VSCode颜值上的碾压一下子就抹平了上述差距。更何况在插件的支持下，选择VSCode就是选择了未来。

## Keil Assistant

[Keil Assistant](https://marketplace.visualstudio.com/items?itemName=CL.keil-assistant)这个插件给我了很大的惊喜。最初我的想法是，在VSCode中加上 c/c++ 插件，在c_cpp_properties.json中添加了keil中的include和宏之后，就行了。

但是遇到了Assistant这个插件，实现了上述所有功能，并且能调用keil的api在VSCode中进行编译，烧录。而且解决了VSCode会将工程文件一股脑地加到文件列表里，层级混乱的问题。Assistant中会用keil的工程结构打开，这点很赞。

Assistant也有一点小小的问题，编译和烧录的快捷键是没办法使用的。所以我搜了下，发现是插件本身的bug，作者在github的源码里应该是修复了，但是并没有更新到vscode插件商店里。![image-20211108171355328](vscode%E5%BC%80%E5%8F%91stm32.assets/image-20211108171355328.png)

并且表示插件停止更新，有些可惜。

![image-20211108172006124](vscode%E5%BC%80%E5%8F%91stm32.assets/image-20211108172006124.png)
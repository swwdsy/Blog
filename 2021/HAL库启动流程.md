# HAL库 启动流程

用cubeMX给我的blue-pill小板子生成了一个空白程序。以这个程序为例子，一路调试，研究了一下他的启动流程。

## 启动文件 startup_stm32f103xb.s

启动文件由汇编语言编写，进行堆栈初始化，中断向量表初始化，和复位中断处理Reset_Handler.以及我还不太清楚具体是做什么的Dummy Exception Handlers。

启动流程如下：

![image-20211109190231126](https://raw.githubusercontent.com/swwdsy/Blog_Image/master/imagesimage-20211109190231126.png)

这里内容相对底层，我也是一句一句查的，没有太多自己的理解，所以不再复述，直接引用安富莱用户手册中的内容了（硬汉写手册的时候没关语法检查，这个红线很惹眼哈哈哈）。

查资料的时候发现，启动这里很多东西都是《cortex-m3权威》指南上有系统描述。先挖个坑，以后有机会回去看一看的，学了之后再写一篇博客分享。

## main.c

先上图：

![image-20211109192127751](https://raw.githubusercontent.com/swwdsy/Blog_Image/master/imagesimage-20211109192127751.png)

## 总结

main()函数中执行了HAL_Init()和SystemClock_Config()，两个函数，后面就是外设初始化和用户函数。

### HAL_Init()

复位所有外设，初始化 Flash接口 和 系统心跳。

### SystemClock_Config()

执行此函数之前一直使用HSI作为各个Clock的振荡源，在这里进行晶振和时钟的配置。配置结束后会重设系统心跳，使其依然保持1000Hz。


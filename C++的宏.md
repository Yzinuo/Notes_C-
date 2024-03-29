预处理部分包括引进头文件和宏定义。

 
![](attachments/C++的宏_image_0.png)

宏的错误使用：
按照自己的想法定义一行代码，这样在大工程中是迷惑行为。

正确使用：
利用宏来定义函数

![](attachments/C++的宏_image_1.png)

利用宏实现某些代码在debug中存在，在release模式中不存在。
在属性的preprocessor中加入自己的PR—DEBUG
![](attachments/C++的宏_image_2.png)


![](attachments/C++的宏_image_3.png)
快速删除代码

在宏中，使用转义符/加enter实现enter。不然的话，计算机会始终认为都在一行。
lambda在过程中生成的代码，用完即毁。

![](attachments/lambda_image_0.png)

![](attachments/lambda_image_1.png)

```
void PrintValue(int value)
{
	std::cout << value << std::endl;
}
lambda表达式：
[](int a){std::cout <<a << std::endl;}
```
[]这是capture 捕获的意思，  如果是[] 空的话，代表是封闭的函数。 如果是[ = ]代表是拷贝外面所有的值传进函数，[&]则是代表引用传入函数，也可以特定指某个元素[ =a ]
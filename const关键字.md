
![](attachments/const关键字_image_0.png)
const使变量变成只读变量（常量）

对指针运用const 关键字的时候，我们不能修改这个指针指向的变量的值，但是可以修改指针本身。
```
const int *a;
int * const a;
```
在指针前面加const，代表指针指向的值不能被改变。
而在指针后加const 代表 这个指针本身不能被修改。


<font color= "#111111">函数参数的</font>const<font color= "#111111">修饰符是给函数内部看的，而不是给函数调用者看的。它告诉编译器和阅读代码的人，这个函数不会修改它的参数。而在调用函数时，你可以传入任何类型匹配的变量，无论它是否被声明为</font>
const<font color= "#111111">。</font>

对类的方法使用const时，含义是这个方法不允许改变类中变量名。

## mutable
mutable提供了一种在const对象的const方法中修改成员的方法。
<font color= "#07133e">const关键字可以确保类的成员变量不会被意外修改。这有助于维护数据的完整性和一致性。 </font>
<font color= "#07133e">const类对象又仅仅能调用const方法，const方法是不能修改类成员的。</font>
<font color= "#07133e">如果我想在const类中改变类成员变量的值呢？ 我们可以把这个成员变量声明前加mutable关键字。</font>
<font color= "#07133e">const方法：</font>
```
<font color= "#07133e">const std::string name Getname</font>()const
{
}
```

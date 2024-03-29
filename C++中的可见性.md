类中方法和变量的可见性，主要是三个修饰符。
private，protected，public。
private是私有的，外部不可见的。private的东西在main函数和子类中是不可以使用的。但是可以在友元中使用。
protected:
在子类是可见的，在main是不可见的。
就是说可以在子类中使用，但是也不能由子类在main中调用。
public是都可见。

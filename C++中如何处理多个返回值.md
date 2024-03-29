首先明确，C++中是不能一次性返回多个返回值的，我们需要怎么操作呢？

## 使用引用
引用可以在函数中通过直接修改引用的值到达返回值的目的。这是通过修改函数参数解决的。

## 返回值
我们可以返回pair，tuple，vector， arr来解决。
tupe和pair不限容器内放的是什么类型的，直接加。
当从中取元素的时候：int vs = std::get<0>(sources);表示source数组的0索引。pair中可以：source.first这样调用。但是这样调用有个缺点，我们不知道调用的变量的变量名，这可能会给我们带来不便。

所以，我们可以使用struct，结构体。把要返回的东西，放在结构体内，这样调用，取出的时候更加清晰。

## C++17:
我们可以使用tie
```
std::tuple<std::string. int>Creatperson()
{
    return ["cherno",24];
}
string name;
int age;
std::tie[name,age] = CreatePerson;
```

这样还是麻烦了，我们可以使用结构化绑定
函数返回值还是tuple；
```
auto[name,age] = CreatePerson;
name....
age....
```

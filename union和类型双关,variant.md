类型双关：
我们可以把一个int类型的内存，当作其他类型来使用。
```
int a = 5;
double& value = *(double*)&value;
```
但是注意，4内存变8内存会导致差错。

结构体空的话，占一个字节。 如果不是空的话，内存连着分布，类似于数组，因此可以把结构体当作字符流输出。

union的数据共享一个内存，也就是说这个内存可以被看作是多种数据类型来对应处理，很不错。

## Variant
std::Variant 允许我们列出所有可能得类型，然后你可以决定它将是什么。
```
std::variant<type,type> data;
data...
std::get<type>data;
如果data不是type类型就会报错。
我们可以用data.index（）来检查data类型。
```
variant的存储方式和类或结构体一样，不是Union，
```
std::get_if<std::string>(&data)
```
检查data是否是string类型，是的话返回string类型的指针，不是的话空指针。
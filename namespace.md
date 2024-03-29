## 最好不要用using namespace std
1. 如果有两个namespace有共同的函数，那么如果两者都用了using namespace得到话，我们可能会调用错函数，带来很难查找的运行错误。
1. 用std::vector 可以清晰看出函数来自哪一个命名空间。提高可读性。
1. 永远不要在.H头文件使用using namespace

## 什么是namespace

![](attachments/namespace_image_0.png)
C语言无法处理这种情况。
namespace 存在的原因就是避免命名冲突
类本身就是命名空间
using namespace apple 意思是从apple空间内导入所有东西，就相当于未指定命名空间一样。
this 就是一个指向当前对象的指针，是Entity * const 类型的指针

当我们使用构造函数赋初始值的时候，当局部参数名字和成员参数相同时，x = x这样子是无法达到初始化的目的的（初始化列表可以），我们应该要使用this->x = x;

在const的方法里面，this变成了const Entity* cosnt 类型的指针。

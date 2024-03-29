  array只能固定大小，不能像vector一样增长长度。
 和C语言相比只是：
和C语言风格一样
```
int a[5]  == std::array<int,5> a;
```

array的优势在于可以使用,size，.begin(),.end()等。它可以自动做边界检查。同时性能很强。
vector的数据在堆上，array和C语言的数组一样在栈上。
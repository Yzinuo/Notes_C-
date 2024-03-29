## vector为什么可以不限制大小？
vector是可以不限制大小的，当我们往vector里塞进十个数据的时候，我们如果超过了内存限制，那么它就会在内存中创建一个比第一个大的数组，把所有东西都复制到这一个，然后删除旧的那一个。
基本操作：
push_back（）；
用range循环。for(int a ： vector);
clear();
erase();0

## 如何高效的使用vector？
vector的使用方法就是上述，当vector的空间用完后，它会重新分配新的空间。这也是会拖慢代码的重要原因。
<font color= "#F33232">我们可以直接告诉vector，我们想要它存储的大小，这样就不会自动调整大小。</font>
```
<font color= "#F33232">std::Entity</font><int> arr(3);
这不是仅仅告诉arr要预先留这么多空间，而是直接创造了3个int。
arr.reserve(3);是我们需要的
```
我们把元素放入vector中就会有一次时间浪费。我们可以直接在vector 的内存中分配元素的内存。
<font color= "#F33232">可以通过emplace_back来实现</font>
```
<font color= "#F33232">arr.emplace_back</font>(1)； 这样的emplace_back实际上只传递参数，在vector内传递。而不是创造后放进来。
```

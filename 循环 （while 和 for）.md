  做游戏离不开循环，游戏需要利用循环进行一帧一帧的改变渲染。

![](attachments/循环%20（while%20和%20for）_image_0.png)

## 循环的三段内容：
![](attachments/循环%20（while%20和%20for）_image_1.png)

第二段是一种比较落后的bool类型：

![](attachments/循环%20（while%20和%20for）_image_2.png)

第三段是每次循环运行后执行一次。

for循环中可以定义变量  for（int i； ； ）并且循环结束后会自动释放。
while不可以这样，即不可以在循环内部定义变量（会重复定义），也不可以在外面定义后自动释放。

# 控制流

![](attachments/循环%20（while%20和%20for）_image_3.png)

return直接结束函数。
<font color= "#ffffff">   for (int& i : coins)</font>
<font color= "#ffffff">   for (int& i : c</font>
<font color= "#ffffff">oins</font>
```cpp
for (int& i : coins)
这也是个循环，意思是i是个整形的引用“否则是局部变量
，不能改变值。”   这个循环意思就是遍历整个容器。
```

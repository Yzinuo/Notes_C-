
1.  析构函数delete的时候，如果vector是存储了许多指针的vector，那么想一次性delete[] 这个m_data很困难。
![](attachments/Vector%20自己写_image_0.png)
所以我们需要循环显示调用析构函数来完全delete；

2. 
```
tmeplate<typename ...Args>
	T& EmplaceBack(Args&&... args)
	{
		if (m_Size >= m_Capacity)
		{
			ReAlloc(m_Capacity * 2);
		}
		m_Data[m_Size] = T(std::forward<Args>(args)...);
		new(&m_Data[m_Size]) T(std::forward<Args>(args)...);
		return m_Data[m_Size++];
	}
```
学到了emplaceback，例如，我们想插入一个结构体，我们可以在插入的时候只传入参数Args就行了，emplaceback会自动构建这个结构体，然后插入。  当然这里会用到一个拷贝，所以我们也可以用上面的例子new来直接在vector的内存中创建数据，这样就避免了拷贝。


```
#pragma once
#include <cassert>

	template<typename T>
class Vector
{
public:
	Vector()
	{
		ReAlloc(2);	// 2 elements;
	}

	const T& operator[](size_t index)const
	{
		assert(index < m_Size);
		return m_Data[index];
	}

	T& operator[](size_t index)
	{
		assert(index < m_Size);
		return m_Data[index];
	}

	size_t Size()const
	{
		return m_Size;
	}

	void Push_Back(const T& value)
	{
		if (m_Size >= m_Capacity)
		{
			ReAlloc(m_Capacity * 2); 
		}
		m_Data[m_Size] = value;
		m_Size++;
	}

	void Push_Back(T&& value)
	{
		if (m_Size >= m_Capacity)
		{
			ReAlloc(m_Capacity * 2);
		}
		m_Data[m_Size] = std::move(value);
		m_Size++;
	}

	tmeplate<typename ...Args>
	T& EmplaceBack(Args&&... args)
	{
		if (m_Size >= m_Capacity)
		{
			ReAlloc(m_Capacity * 2);
		}
		m_Data[m_Size] = T(std::forward<Args>(args)...);
		new(&m_Data[m_Size]) T(std::forward<Args>(args)...);
		return m_Data[m_Size++];
	}
private:
	void ReAlloc(size_t newCapacity)
	{
		//1. 分配新的内存块
		//2. 复制/move 原来的所有元素进入新的内存块。
		//3. 删除原来的vector；
		T* newBlock = new T[newCapacity];
		
		if (m_Size > newCapacity)
		{
			m_Size = newCapacity;
		}

		for (size_t i = 0; i < m_Size; i++)
		{
			newBlock[i] = std::move(m_Data[i]);
		}
		delete[] m_Data;
		m_Data = newBlock;
		m_Capacity = newCapacity;
	}
private:
	T* m_Data = nullptr;
	size_t m_Size = 0;
	size_t m_Capacity = 0;// 为了避免每次插入都要重新分配内存，每次分配capacity可以翻倍；
};
```


3.	在C++中，当你使用delete[]操作符删除一个动态分配的数组时，它会首先调用每个元素的析构函数，然后释放数组所占用的内存。这意味着，如果你的数组中的元素是一些对象，那么这些对象的析构函数会在内存被释放之前被调用。
然而，需要注意的是，如果你的数组中的元素是一些内置类型（如int、char等），那么这些元素的析构函数就不会被调用，因为内置类型没有析构函数。
所以，在你的Vector类的析构函数中，delete[] m_Data;这行代码会首先调用m_Data数组中每个元素的析构函数（如果存在的话），然后释放m_Data数组所占用的内存。这就是为什么你在PopBack函数中需要显式地调用元素的析构函数，因为当你删除一个元素时，你需要确保它的资源被正确地释放。



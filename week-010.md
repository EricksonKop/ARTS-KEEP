# ARTS第十周（2020年06月20日）
## Algorithm<br/>
<b>题目：</b> [平方数之和](https://leetcode-cn.com/problems/sum-of-square-numbers/)

给定一个非负整数 c ，你要判断是否存在两个整数 a 和 b，使得 a2 + b2 = c。

<b>示例1：</b> 
>输入：5<br>
>输出：True<br>
>解释: 1 * 1 + 2 * 2 = 5

<b>示例2：</b> 
>输入：3<br>
>输出：False

<b>解答：</b>
```Python
class Solution:
    def judgeSquareSum(self, c: int) -> bool:
        i,j = 0, int(c**0.5)
        while i <= j:
            if i*i+j*j == c:
                return True
            elif i*i+j*j < c:
                i += 1
            elif i*i+j*j > c:
                j -= 1
        return False

```
## Review<br/>
[Difference Between Python and Java: Key Features](https://hackernoon.com/difference-between-python-and-java-key-features-oyf3upq)

本文从事实和数据两方面讨论关于Java和Python在实际开发中如何选择的问题。<br/>
在各类编程语言排行榜中，Java和Python几乎不相上下，都排名非常靠前；从薪水角度来看，二者平均水平都在10万刀左右，Python稍高。<br/>
此外，本文列出来影响抉择的关键因素，包括：语法、编译方式、执行速度、多重继承的支持、性能、兼容性、跨平台支持、对数据库的支持、后端框架、开发速度、机器学习库的丰富程度等等。<br/>
总之，新手或者追求开发速度的，选Python；追求程序安全性和健壮性的，选Java。在实际开发中，往往是根据你的需求、预算和项目类型进行选择，二者兼而有之也是常有的事。

## Tip<br/>
Arraylist与LinkedList区别，可以从它们的底层数据结构、效率、开销进行阐述<br/>
ArrayList是数组的数据结构，LinkedList是链表的数据结构。<br/>
随机访问的时候，ArrayList的效率比较高，因为LinkedList要移动指针，而ArrayList是基于索引(index)的数据结构，可以直接映射到。<br/>
插入、删除数据时，LinkedList的效率比较高，因为ArrayList要移动数据。<br/>
LinkedList比ArrayList开销更大，因为LinkedList的节点除了存储数据，还需要存储引用。

## Share<br/>
[推荐一种通过刷leetcode来增强技术功底的方法](https://mp.weixin.qq.com/s?__biz=MzUzNjAxODg4MQ==&mid=2247485355&idx=1&sn=8c5afec64f4a456f001abfd32e340919&chksm=fafded05cd8a64134974423be5c80fbbbcf250c0d9f2abc4d0989f441bd957bf920883684c04&token=773567420&lang=zh_CN#rd)

不管作为面试官还是被面试者，编码题最近越来越流行。而两种角色都需要思考的问题是希望考察什么能力，通过什么题目，需要达到怎样的程度可以说明面试者具有了这样的能力。

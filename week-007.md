# ARTS第七周（2020年1月12日）
## Algorithm<br/>
<b>题目：</b> [从排序数组中删除重复项](https://leetcode-cn.com/explore/interview/card/top-interview-questions-easy/1/array/21/)

给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。<br>
<b>示例1：</b> 
给定数组 nums = [1,1,2], <br>
函数应该返回新的长度 2, 并且原数组 nums 的前两个元素被修改为 1, 2。 <br>
你不需要考虑数组中超出新长度后面的元素。<br>
<b>示例2：</b> 
给定 nums = [0,0,1,1,1,2,2,3,3,4], <br>
函数应该返回新的长度 5, 并且原数组 nums 的前五个元素被修改为 0, 1, 2, 3, 4。 <br>
你不需要考虑数组中超出新长度后面的元素。<br>
<b>说明: </b> 
为什么返回数值是整数，但输出的答案是数组呢?<br>
请注意，输入数组是以“引用”方式传递的，这意味着在函数里修改输入数组对于调用者是可见的。<br>
你可以想象内部操作如下:<br>
```C
// nums 是以“引用”方式传递的。也就是说，不对实参做任何拷贝
int len = removeDuplicates(nums);

// 在函数里修改输入数组对于调用者是可见的。
// 根据你的函数返回的长度, 它会打印出数组中该长度范围内的所有元素。
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```

<b>解答：</b>
```Python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        i = 0
        while True:
            if i >= len(nums):
                break
            elif i == 0 or nums[i] != nums[i-1]:
                i += 1
                continue
            else:
                nums.pop(i)
                continue
        return len(nums)

```
## Review<br/>
[20-predictions-about-software-development-trends-in-2020](https://towardsdatascience.com/20-predictions-about-software-development-trends-in-2020-afb8b110d9a0)<br>
2020软件开发趋势：<br>
基础设施：终将上云、容器化：Kubernetes 将会更酷、软件架构：微服务成为主流、开发：Python 将吞噬世界、企业级开发：Java 和 JVM 为王、
Java 企业级开发：Spring、开发：Rust, Swift, Kotlin, TypeScript 会有一个突破、Web：JavaScript 继续主导、JavaScript Web 框架：React 领先、
APP 跨平台混合开发：React Native、API：REST为主、数据库：SQL 主导，分布式 SQL 崛起、大数据计算：Spark 继续闪耀、大数据流处理：Flink、
字节码：WebAssembly 会开始大量应用。

## Tip<br/>
#### win7虚拟机网络配置
win7虚拟机在修改ipv4网络地址后发现可以往外ping而不能往内ping，猜想可能是防火墙对入站流量做了限制，进入控制面板修改防火墙规则即可；在能够双向ping通后，发现不能远程桌面登陆，进入防火墙设置规则里设置并勾选计算机属性远程设置即可。<br>
#### Jmeter循环压测中生成不重复的实时时间戳
Jmeter在压测过程中，时间戳是在用户定义变量中define的，第一次生成后后续循环读取该值，因此把生成timestamp的逻辑移到前置处理器中：
```Java
var now_date = new Date().getTime();
vars.put("timestamp",now_date.toString());
```

## Share<br/>
[为什么 MongoDB 使用 B 树 · Why's THE Design?](https://draveness.me/whys-the-design-mongodb-b-tree?)<br>
MongoDB 的架构与MySQL非常类似，它们底层都使用了可插拔的存储引擎以满足用户的不同需求，最新版本MongoDB使用了WiredTiger作为默认的存储引擎；
作为非关系型的数据库，MongoDB 对于遍历数据的需求没有关系型数据库那么强，它追求的是读写单个记录的性能；
大多数的数据库面对的都是读多写少的场景，B 树与 LSM 树在该场景下有更大的优势；
总结一下 MongoDB 最终选择使用 B 树的两个原因：<br>
MySQL 使用 B+ 树是因为数据的遍历在关系型数据库中非常常见，它经常需要处理各个表之间的关系并通过范围查询一些数据；但是 MongoDB 作为面向文档的数据库，
与数据之间的关系相比，它更看重以文档为中心的组织方式，所以选择了查询单个文档性能较好的 B 树，这个选择对遍历数据的查询也可以保证可以接受的时延；
LSM 树是一种专门用来优化写入的数据结构，它将随机写变成了顺序写显著地提高了写入性能，但是却牺牲了读的效率，这与大多数场景需要的特点是不匹配的，
所以 MongoDB 最终还是选择读取性能更好的 B 树作为默认的数据结构；

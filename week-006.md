# ARTS第六周（2020年1月5日）
## Algorithm<br/>
<b>题目：</b> [存在重复](https://leetcode-cn.com/explore/interview/card/top-interview-questions-easy/1/array/24/)

给定一个整数数组，判断是否存在重复元素。
如果任何值在数组中出现至少两次，函数返回 true。如果数组中每个元素都不相同，则返回 false。<br>
<b>示例1：</b> 
>输入：[1,2,3,1]<br>
>输出：true<br>
<b>示例2：</b> 
>输入：[1,2,3,4]<br>
>输出：false<br>
<b>示例3：</b> 
>输入：[1,1,1,3,3,4,3,2,4,2]<br>
>输出：true<br>

<b>解答：</b>
```Python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        n = len(nums)
        count_d = {}
        for i in range(n):
            if nums[i] not in count_d:
                count_d[nums[i]] = 1
            else:
                count_d[nums[i]] += 1
        for value in count_d.values():
            if value > 1:
                return True
            else:
                continue
        return False

```
## Review<br/>
[20-predictions-about-software-development-trends-in-2020](https://towardsdatascience.com/20-predictions-about-software-development-trends-in-2020-afb8b110d9a0)<br>
2020软件开发趋势：<br>
基础设施：终将上云、容器化：Kubernetes 将会更酷、软件架构：微服务成为主流、开发：Python 将吞噬世界、企业级开发：Java 和 JVM 为王、
Java 企业级开发：Spring、开发：Rust, Swift, Kotlin, TypeScript 会有一个突破、Web：JavaScript 继续主导、JavaScript Web 框架：React 领先、
APP 跨平台混合开发：React Native、API：REST为主、数据库：SQL 主导，分布式 SQL 崛起、大数据计算：Spark 继续闪耀、大数据流处理：Flink、
字节码：WebAssembly 会开始大量应用。

## Tip<br/>
#### 读取配置文件模块
configparser模块常被用来读取配置文件，还可以用cfg.write()方法；ConfigParser有个容易被忽视的特性，就是它能一次性读取多个配置文件然后合并成一个配置


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

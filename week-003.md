# ARTS第三周（2019年12月15日）
## Algorithm<br/>
<b>题目：</b> [移动零](https://leetcode-cn.com/explore/interview/card/top-interview-questions-easy/1/array/28/)

给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。<br>
说明:<br>
必须在原数组上操作，不能拷贝额外的数组。<br>
尽量减少操作次数。<br>

<b>示例：</b> 
>输入：[0,1,0,3,12]<br>
>输出：[1,3,12,0,0]

<b>解答：</b>
```Python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        iter_times = len([one for one in nums if one == 0])
        for i in range(iter_times):
            index_del = nums.index(0)
            nums.pop(index_del)
            nums.append(0)
```
## Review<br/>
[The Past, Now, and The Future of Web Media Playback](https://medium.com/canal-tech/how-video-streaming-works-on-the-web-an-introduction-7919739f7e1)

这应该是目前写的最为完整的关于 Web 视频播放的文章。从简单的 Video 元素到 MSE 直播的应用，作者给出了具体的代码，文章由浅入深，普及现代 Web 播放技术的前前后后。

从原生视频API到带Video标签，从Media Source Extensions到Source Buffers，从切片到自适应码流Adaptive Streaming，从切换语言到最新的网络直播流媒体，视频直播正
在变得越来越复杂，因为视频播放器必须支持许多功能：必须下载并解析某种清单文件；必须猜测当前的网络状况；需要注册用户首选项（例如，首选语言）；必须至少根据前两个要点知道要下载哪个段
它必须管理一个段管道以在正确的时间顺序下载正确的段（同时下载每个段的效率很低：您需要最早的一个比下一个要早）；它也必须处理字幕，通常完全由 JS 管理；
一些视频播放器还管理缩略图轨道，将鼠标悬停在进度条上时通常可以看到；许多服务也需要 DRM 管理，还有很多其他事情。复杂的，与Web兼容的视频播放器的核心仍然都是基于 MediaSource 和 SourceBuffers。
这就是为什么这些任务通常由第三方库执行的原因。



## Tip<br/>

在工作中碰到在这样一个问题，用Python脚本批量提交本地图片到oracle数据库，但是查看oracle的表里并没有成功更新数据，很是尴尬，为什么会出现这种不一致的情况呢？

经过同事提醒可能是锁表了，于是查了一大堆oracle锁表的处理方法，最后还是没有成功。最后，终于发现原来是因为我执行命令后没有commit提交，所以通过plsql看到的是之前的数据。

SQL语言分为五大类：
DDL(数据定义语言) - Create、Alter、Drop 这些语句自动提交，无需用Commit提交。

DQL（数据查询语言）- Select查询语句不存在提交问题。

DML(数据操纵语言) - Insert、Update、Delete 这些语句需要Commit才能提交。

DTL(事务控制语言) - Commit、Rollback 事务提交与回滚语句。

DCL(数据控制语言) - Grant、Revoke 授予权限与回收权限语句。

执行完DML语句，若没有commit再执行DDL语句，也会自动commit未被commit的数据。

如果打开自动提交，DML操作后也不需要手动提交：SET AUTOCOMMIT ON;

## Share<br/>
[为什么MySQL使用B+树](https://draveness.me/whys-the-design-mysql-b-plus-tree?)

为什么 MySQL 使用 B+ 树是面试中经常会出现的问题，很多人对于这个问题可能都有一些自己的理解，但是多数的回答都不够完整和准确，大多数人都只会简单说一下 B+ 树和 B 树的区别，
但是都没有真正回答 MySQL 为什么选择使用 B+ 树这个问题，而这篇文章中就会深入分析 MySQL 选择 B+ 树背后的一些原因。

 MySQL 默认的存储引擎选择 B+ 树而不是哈希或者 B 树的原因：

哈希虽然能够提供 O(1) 的单数据行操作性能，但是对于范围查询和排序却无法很好地支持，最终导致全表扫描；
B树能够在非叶节点中存储数据，但是这也导致在查询连续数据时可能会带来更多的随机 I/O，而 B+ 树的所有叶节点可以通过指针相互连接，
能够减少顺序遍历时产生的额外随机 I/O；从今天的角度来看，B+ 树可能不是 InnoDB 的最优选择，但是它一定是能够满足当时设计场景的需要，
从 B+ 树作为数据库底层的存储结构到今天已经过了几十年的时间，我们不得不说优秀的工程设计确实有足够的生命力。而我们作为工程师，在选择数据库时也应该非常清楚地知道不同数据库适合的场景，因为软件工程中没有银弹。


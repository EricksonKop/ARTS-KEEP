# ARTS第四周（2019年12月22日）
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
[](https://mp.weixin.qq.com/s/UYLAmNJ8_2Eoa4MuRRvjZA)

这应该是目前写的最为完整的关于 Web 视频播放的文章。从简单的 Video 元素到 MSE 直播的应用，作者给出了具体的代码，文章由浅入深，普及现代 Web 播放技术的前前后后。

从原生视频API到带Video标签，从Media Source Extensions到Source Buffers，从切片到自适应码流Adaptive Streaming，从切换语言到最新的网络直播流媒体，视频直播正
在变得越来越复杂，因为视频播放器必须支持许多功能：必须下载并解析某种清单文件；必须猜测当前的网络状况；需要注册用户首选项（例如，首选语言）；必须至少根据前两个要点知道要下载哪个段
它必须管理一个段管道以在正确的时间顺序下载正确的段（同时下载每个段的效率很低：您需要最早的一个比下一个要早）；它也必须处理字幕，通常完全由 JS 管理；
一些视频播放器还管理缩略图轨道，将鼠标悬停在进度条上时通常可以看到；许多服务也需要 DRM 管理，还有很多其他事情。复杂的，与Web兼容的视频播放器的核心仍然都是基于 MediaSource 和 SourceBuffers。
这就是为什么这些任务通常由第三方库执行的原因。



## Tip<br/>
之前同事在测试环境的虚拟机中误操作rm -rf /* 导致虚拟机崩溃，在克隆重装的过程中发现隐藏的坑不少，在修改网卡绑定IP地址后无论是修改删除/etc/udev/rules.d/70-persistent-net.rules文件，
还是修改hostname，亦或是修改被克隆虚拟机的网卡名为eth0，都无济于事。最后发现该宿主机上的虚拟机都是采用Custom网络连接方式，于是删除网卡，添加新网卡并修改其为桥接，然后重新生成mac地址，
然后设置固定IP和mac地址，最终成功ping通虚拟机和宿主机。

## Share<br/>
[分布式ID生成器](https://mp.weixin.qq.com/s/UYLAmNJ8_2Eoa4MuRRvjZA)
分布式 ID 生成器有哪些要求？

1. 全局唯一性：不能出现重复的 ID 号，既然是唯一标识，这是最基本的要求。<br/>
2. 递增：比较低要求的条件为趋势递增，即保证下一个 ID 一定大于上一个 ID，而比较苛刻的要求是连续递增，如1001，1002，1003 等等。根据我们自己的业务，我们选择的是趋势递增（连续递增，会暴露出系统实际订单量）。<br>
3. 高可用：ID 生成事关重大，一旦挂掉会导致整个系统崩溃，给公司带来巨大的损失，需要保证 ID 的正常、稳定生成。<br>
4. 高性能：必须要在压测下表现良好，如果达不到要求则在高并发环境下依然会导致系统瘫痪。<br>
5. 灵活多变：每个业务场景对 ID 的要求也各不相同，ID 生成要做到灵活多变可配置，尽可能多的满足需求。<br>
后面介绍了几种可行的方案，包括UUID生成法，雪花算法SnowFlake方案，数据库自增法，基于Zookeeper和本地缓存的方案以及基于数据库双Buffer的优化方案。



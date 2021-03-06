# ARTS第四周（2019年12月22日）
## Algorithm<br/>
<b>题目：</b> [加一](https://leetcode-cn.com/explore/interview/card/top-interview-questions-easy/1/array/28/)

给定一个由整数组成的非空数组所表示的非负整数，在该数的基础上加一。
最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。
你可以假设除了整数 0 之外，这个整数不会以零开头。<br>
<b>示例1：</b> 
>输入：[1,2,3]<br>
>输出：[1,2,4]<br>
>解释：输入数组表示数字 123。

<b>解答：</b>
```Python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        digit_num = 0
        n = len(digits)
        for i in range(n):
            temp = digits[i] * (10 ** (n - 1 - i))
            digit_num += temp
        digit_num += 1
        ret_list = []
        digit_str = str(digit_num)
        for j in range(len(digit_str)):
            ret_list.append(digit_str[j])
        return ret_list
```
## Review<br/>
[The Dark Side of Blockchain](https://hackernoon.com/the-dark-side-of-blockchain-46666adb8061)

这是一篇关于区块链的另一面或者说是短板、缺点的文章。作者以脍炙人口的星战系列为引子，讲述了天资卓绝的“The Chosen One”Anakin如何因为自身的复杂性格，缺乏自律以及经验的匮乏导致最终一步步走向堕落，引出了目前被各路资本舆论吹捧的区块链的一系列潜在的问题。包括1、技术上落地的复杂性，政府态度普遍倾向保守以及黑客对代码漏洞的挖掘会威胁到链上的永固数据；2、可伸缩性，包括对算力资源和网络资源的巨量耗损与需求以及对生态不友好的一致性算法，尽管目前这些都在逐步得到解决；3、去中心化的架构带来管理上难题，如何在去中心化即没有权威的情况下应对达成契约过程前后所出现的一系列问题，对于政府来说尤其如此；4、区块链可以被设计的难以追踪匿名交易，这使得网上洗钱毒品交易等犯罪活动变得猖獗，典型例子就是数次被灭的暗网网站丝绸之路；5、区块链带来了新的安全问题，典型的51%洪水攻击；6、不成熟、不稳定、不被制度约束和不被实体货币绑定的特点让区块链货币的涨跌幅度远超出实际货币，这也使得它成为很多机构割韭菜的圣地；最后，作者总结自己的观点，即认为虽然现在区块链的热度有点类似于以前的互联网泡沫时期，不过即将到来的泡沫破灭对于市场回归理性有好处，最终成为仲裁者的将是合理的价值，而非被炒作起来的市场价格。他认为如果说区块链有问题，那被暴露的越早越好，毕竟，这事关每一个信息在未来将被上链的人，你和我，不是吗？<br>
这篇文章作于2018年10月。

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



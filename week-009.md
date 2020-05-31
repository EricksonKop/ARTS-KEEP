# ARTS第九周（2020年5月26日）
## Algorithm<br/>
<b>题目：</b> [Nim 游戏](https://leetcode-cn.com/problems/nim-game/)

你和你的朋友，两个人一起玩 Nim 游戏：桌子上有一堆石头，每次你们轮流拿掉 1 - 3 块石头。 拿掉最后一块石头的人就是获胜者。你作为先手。

你们是聪明人，每一步都是最优解。 编写一个函数，来判断你是否可以在给定石头数量的情况下赢得游戏。

<b>示例：</b> <br>
><b>输入：</b>4<br>
><b>输出：</b>false<br>
><b>解释：</b>如果堆中有 4 块石头，那么你永远不会赢得比赛；
     因为无论你拿走 1 块、2 块 还是 3 块石头，最后一块石头总是会被你的朋友拿走。<br>

<b>解答：</b>
```Python3
class Solution:
    def canWinNim(self, n: int) -> bool:
        return False if n % 4 == 0 else True
```
## Review<br/>
[free-speech-pleasemark-zuckerberg-profits-from-rage-as-much-as-donald-trump-does](https://hackernoon.com/automating-instagram-api-with-python-gain-followers-u115322z)<br>
这篇文章的作者毫无疑问是个反川分子，用the Prince of Darkness，evil等词来形容trump，同时指出本应持民主党观点的扎克伯格为何却一反常态的支持trump及其支持者的言论而不进行管控（是的，他们也有管控，而且一点也不少），本质上在于他是个十足的商人，至少这一点上和川普很像，他的目的在于通过两派言论的不断传播，升级，掐架从而带来流量和广告。

## Tip<br/>
#### 打印出占用Linux机器内存资源最多的10个进程：

ps -auxf | sort -nr -k 4 | head 10<br>
#### 打印出占用Linux机器CPU资源最多的10个进程：

ps -auxf | sort -nr -k 3 | head 10<br>

## Share<br/>
### [为什么腾讯QQ的大数据平台选择了这款数据库？](https://mp.weixin.qq.com/s/cqsNlhZ9yD5jfO3xyEa_Kg)<br>
为了解决海量监控数据场景的问题，该团队引入高性能的开源时序数据库InfluxDB，基于源码的基础进行二次开发，且文章把InfluxDB和其他被用作时序存储的系统（如ElasticSearch、MongoDB、OpenTSDB）做简要的对比，凸出了该款数据库在时序数据场景下的巨大优势。

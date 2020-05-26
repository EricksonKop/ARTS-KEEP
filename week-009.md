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
[Automating Instagram API Using Python: Gain Active Followers](https://hackernoon.com/automating-instagram-api-with-python-gain-followers-u115322z)<br>


## Tip<br/>
#### 打印出占用Linux机器内存资源最多的10个进程：

ps -auxf | sort -nr -k 4 | head 10<br>
#### 打印出占用Linux机器CPU资源最多的10个进程：

ps -auxf | sort -nr -k 3 | head 10<br>

## Share<br/>
### <br>


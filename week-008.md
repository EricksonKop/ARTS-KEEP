# ARTS第八周（2020年1月19日）
## Algorithm<br/>
<b>题目：</b> [两数之和](https://leetcode-cn.com/explore/interview/card/top-interview-questions-easy/1/array/29/)

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。<br>
<b>示例：</b> 
给定 nums = [2, 7, 11, 15], target = 9<br>
因为 nums[0] + nums[1] = 2 + 7 = 9<br>
所以返回 [0, 1]<br>

<b>解答：</b>
```Python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            num = nums[i]
            minus = target - num
            if minus in nums[i+1:]:
                result = [i, i+nums[i+1:].index(minus)+1]
                print(result)
                return result
            else:
                continue

```
## Review<br/>
[Automating Instagram API Using Python: Gain Active Followers](https://hackernoon.com/automating-instagram-api-with-python-gain-followers-u115322z)<br>
利用非官方的InsAPI来自动化ins操作让自己“涨粉” <br>
利用第三方提供的Instagram API接口，帮助建立一个使自己Ins账号“涨粉”的小应用，其基本策略如下：
1. 找一个特定领域的有影响力的账号，通过该账号最近一次post，爬取所有点了赞的人；
2. 遍历上面爬取到的账号，如果他们不在自己账号的following列表里面，则关注；
3. 一段时间后，查看自己的followers列表，如果自己的following列表里面有账号不在follwers列表里，则取关（这里应该有个策略就是过滤掉一些肯定不会关注自己的很有影响力的而自己又必然不会取关的账号）。<br>
你觉得这个策略可行吗？

## Tip<br/>
#### linux机器source命令失效
Linux虚拟机在修改完/etc/hosts文件后打算输入source命令即时生效，提示command not found，使用locate source /etc/hosts方法可破。<br>
#### Spring Boot Admin在开启过程中遇到的问题
在使用spring-boot-admin过程中遇到application无法注册的问题，保证hostname解析正确，开启jar时制定初始堆和最大堆大小，开启监控和被监控应用。

## Share<br/>
### 小灰的算法之旅：字符串匹配算法<br>
字符串RK匹配算法：讲述了字符串匹配问题中的原始暴力算法（BF）和原理和缺点，在此基础上改进的优化算法RK算法，及其改进的核心————哈希算法，决定了改进后算法的复杂度。

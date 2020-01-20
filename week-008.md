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
[7-habits-of-highly-effective-programmers](https://dev.to/seattledataguy/7-habits-of-highly-effective-programmers-inspired-by-an-ex-google-techlead-humor-4b4k)<br>
高效程序员的七个习惯 <br>
软件工程师花费大量时间通过练习leet code问题和完善简历来获得更好的面试通过可能。一旦他们最终被谷歌、亚马逊或其他公司录用，他们可能会发现：过去用来得到这份工作的技能与他们日常工作中需要的技能并不匹配。
我们的团队受到 TechLead 创建的高效程序员七项技能的启发。我们想提供我们自己对这个话题的看法。以下是我们总结的高效程序员的七项技能。
1. 学习如何阅读别人的代码：你需要确保在阅读他人代码时尽可能多地找出问题所在；您的代码应该设计得非常好，不需要任何文档；这一切都来自于对所有代码的良好理解以及能够阅读以往的代码。阅读别人的代码会让你变得有价值，因为这项技能甚至可以让你接手那些让别人难堪的过度工程化的系统。
2. 对坏项目的感觉：有许多技能需要花时间去学习。我们认为值得了解的技能之一是理解什么项目不值得做，什么项目显然是行尸走肉。

## Tip<br/>
#### linux机器source命令失效
Linux虚拟机在修改完/etc/hosts文件后打算输入source命令即时生效，提示command not found，使用locate source /etc/hosts方法可破。<br>
#### Spring Boot Admin在开启过程中遇到的问题
在使用spring-boot-admin过程中遇到application无法注册的问题，保证hostname解析正确，开启jar时制定初始堆和最大堆大小，开启监控和被监控应用。

## Share<br/>
### 小灰的算法之旅：字符串匹配算法<br>
字符串RK匹配算法：讲述了字符串匹配问题中的原始暴力算法（BF）和原理和缺点，在此基础上改进的优化算法RK算法，及其改进的核心————哈希算法，决定了改进后算法的复杂度。

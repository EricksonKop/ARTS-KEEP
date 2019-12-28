# ARTS第五周（2019年12月29日）
## Algorithm<br/>
<b>题目：</b> [只出现一次的数字](https://leetcode-cn.com/explore/interview/card/top-interview-questions-easy/1/array/25/)

给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。<br>
说明：<br>
你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？<br>
<b>示例1：</b> 
>输入：[2,2,1]<br>
>输出：1<br>
<b>示例2：</b> 
>输入：[4,1,2,1,2]<br>
>输出：4<br>

<b>解答：</b>
```Python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        n = len(nums)
        count_d = {}
        for i in range(n):
            if nums[i] not in count_d:
                count_d[nums[i]] = 1
            else:
                count_d[nums[i]] += 1
        for k,v in count_d.items():
            if v == 1:
                return k
            elif v > 1:
                continue
        return 0
# 因为需要保证函数的时间复杂度为n，而list的index、count等方法的复杂度均为O(n)，因此采用dict的数据结构。注：dict的get/search/set方法均为O(1)
```
## Review<br/>
[The Dark Side of Blockchain](https://hackernoon.com/the-dark-side-of-blockchain-46666adb8061)

这是一篇关于

## Tip<br/>
关于

## Share<br/>
[用“升层思维”解决问题](https://mp.weixin.qq.com/s/2Cs8ybu5Kg9QYr5Jgyu6VA)
阿里资深技术专家张荣华从问题的本质入手，用“升层思维”解决问题，告诉我们创新的核心，给出高效工作的途径。

一、问题的本质<br/>
二、准确定义问题是成功的开始<br>
三、问题的严重程度<br>
四、问题的分类<br>
五、问题定义中的常见问题:<br>
1.误把方法/手段当“问题”<br>
2.误把挑战当"问题"<br>
3.思考问题时缺少时间维度<br>
六、升层思考及升维思考:缺乏升层思考的升维思考是不完整的自顶向下
七、是新问题还是新技术解决老问题？
八、小结:区分手段和问题;明确问题定义;对问题背后的问题进行升层思考;对问题的分解进行升维思考

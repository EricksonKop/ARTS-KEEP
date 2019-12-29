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
[I hacked 40,000 passwords with Python. Yours might've been one of them.](https://hackernoon.com/i-cracked-40000-passwords-with-python-yours-might-have-been-one-of-them-3fr32je)

这是一篇关于账户安全普及的文章，主要介绍了主流的网站密码加密储存方法，如明文储存，哈希储存以及，加盐哈希。随后作者就使用python撞库攻击做了个大致介绍，就是通过黑掉网站系统管理员得到数据库的访问权限，从而得到储存在库上的密码，随后和黑客自身拥有的字典库（彩虹表诸如此类）进行compare，从而得到想要的用户密码。最后作者给出了保证密码安全的建议，如保证自己的常用邮箱处于最高等级安全防护，不要重用密码，使用有意义的短语类密码，使用1Password这样的密码管理软件。

## Tip<br/>
关于BLOB写操作
现在我有3个python的数据，分别是：
```Python
    date_forecast = ‘2011-06-29’
    filename = ‘aurora.jpg’’
    file = open('aurora.jpg', 'rb')’
    content = fp.read()
    fp.close()
```
网上的资料说，插入包含blob的记录，需要先插入空的blob对象，然后再update该记录——这意味着，一次INSERT操作，至少要访问3次数据库。但是，这里面有个问题无法解决：python如何给Oracle的blob对象赋值？仔细阅读Oracle的文档，发现在SQL语句中，可以使用占位符冒号（:）来定义变量，而cx_Oracle模块中也的确有cx_Oracle.BLOB对象。至此，可以整理出这样的一个思路：

sqlStr = "INSERT INTO aurora (date_forecast, filename, content) VALUES ('%s', '%s', :blobData)" % (date_forecast, filename)
请注意blobData前边的冒号，是定义了一个叫做blobData的Oracle变量。然后：<br>
cursor.setinputsizes(blobData=cx_Oracle.BLOB)
将blobData变量定义为cx_Oracle.BLOB的实例，终于让python和Oracle握手了。接下来，就是水到渠成的事情了：<br>
cursor.execute(sqlStr, {'blobData':content})<br>
cursor.execute('commit')


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

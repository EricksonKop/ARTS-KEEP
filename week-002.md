# ARTS第二周（2019年12月8日）
## Algorithm<br/>
<b>题目：</b> [字符串中的第一个唯一字符串](https://leetcode-cn.com/explore/interview/card/top-interview-questions-easy/5/strings/34/)

给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。

注意事项：您可以假定该字符串只包含小写字母。

<b>示例：</b> 
>输入：s = "leetcode"<br>
>输出：返回 0.

<b>解答：</b>
```Python
class Solution:
    def firstUniqChar(self, s: str) -> int:
        n = 0
        comp_list = []
        for i in range(len(s)):
            if s[i] not in s[i+1:] and s[i] not in comp_list:
                return i
            else:
                n += 1
                comp_list.append(s[i])
                continue
        if n == len(s):
            return -1

```
## Review<br/>
[Scan and extract text from an image using Python libraries](https://developer.ibm.com/technologies/python/tutorials/document-scanner)

Learn how to extract and classify text from an document image using Python libraries such as cv2 and PIL.<br/>
这篇文章介绍了如何使用Python从图片中提取文本，包括重定义扫描图片尺寸，然后从中提取文本，用OTSU二值化算法进行分类；最后还讲了把pdf文件转换为png图片的简要方法。
本文所用到的库包括wand, pytesseract, cv2, and PIL.

## Tip<br/>

grant 语句会同时修改数据表和内存，判断权限的时候使用的是内存数据。因此，规范地使用 grant 和 revoke 语句，是不需要随后加上 flush privileges 语句的。flush privileges 语句本身会用数据表的数据重建一份内存权限数据，所以在权限数据可能存在不一致的情况下再使用。
而这种不一致往往是由于直接用 DML 语句操作系统权限表导致的，所以尽量不要使用这类语句。

## Share<br/>
[2019开源的现状](https://lingxiankong.github.io/2019-08-02-opensource-in-2019.html)

这篇文章讨论了目前开源世界存在的一些问题，具体来说，一些大公司对于开源项目的垄断已经违背了自由软件运动最初的精神，我认为典型的有mysql，在被大公司掌控之后未来走向何方依然
是个未知数；能够理解以赚钱和利润为第一目标的公司，做开源是有其自身的目的，人家不会无偿为你们这些韭菜做奉献，他们认为那不是个人机构该干的事，哪怕是最早拥抱开源的谷歌这样的企业，
也不可避免的要基于自身利益甚至政治因素做出与开源相违背的事情。无论如何，不要指望开源能解决一切问题。

1.
```
class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        d = {}
        for num in nums:
            if num in d:
                return True
            else:
                d[num] = 1
        return False
 ```
 2.
 ```
 class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        d = {}
        for num in nums:
            if num in d.keys():
                return True
            else:
                d[num] = 1
        return False
 ```
 Code block 2 gave time limit exceeded error but code bloc 1 did not. Difference? 
 The only difference is in the line `if num in d.keys():` vs `if num in d:`
 
 Ref: https://leetcode.com/problems/contains-duplicate/submissions/958483481/

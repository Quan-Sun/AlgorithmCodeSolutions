Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).

The replacement must be in-place and use only constant extra memory.

Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the right-hand column.

1,2,3 → 1,3,2
3,2,1 → 1,2,3
1,1,5 → 1,5,1

***03/01/2019***
```python
class Solution(object):
    def nextPermutation(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        if nums is None:
            return None

        i = len(nums) - 1
        while i > 0 and nums[i - 1] >= nums[i]: i -= 1
        if i > 0:
            j, pre = len(nums) - 1, nums[i - 1]
            while j >= i and nums[j] <= pre: j -= 1
            nums[i - 1], nums[j] = nums[j], nums[i - 1]
        k = len(nums) - 1
        while i < k:
            nums[i], nums[k] = nums[k], nums[i]
            i, k = i + 1, k - 1
```
The time complexity is O(n<sup>2</sup>).

We are given a linked list with head as the first node.  Let's number the nodes in the list: `node_1, node_2, node_3, ... etc`.

Each node may have a next larger value: for `node_i`, next_larger(`node_i`) is the `node_j.val` such that `j > i`, `node_j.val > node_i.val`, and `j` is the smallest possible choice.  If such a `j` does not exist, the next larger value is `0`.

Return an array of integers answer, where `answer[i] = next_larger(node_{i+1})`.

Note that in the example inputs (not outputs) below, arrays such as [2,1,5] represent the serialization of a linked list with a head node value of 2, second node value of 1, and third node value of 5.

Example:

```
Input: [2,1,5]
Output: [5,5,0]
```

```
Input: [2,7,4,3,5]
Output: [7,0,5,5,0]
```

```
Input: [1,7,5,1,9,2,5,1]
Output: [7,9,9,9,0,5,0,0]
```

***NOTE***:

 - 1 <= node.val <= 10<sup>9</sup> for each node in the linked list.
 - The given list has length in the range [0, 10000].
 
 
***04/02/2019***
 
**Reverse + Monotonic Stack**

**Idea**: Create a stack; iterate the reversed linkedlist, if the node value in stack is less than or equal to the node value in linkedlist, remove(pop) it from stack.
 
```python
 # Definition for singly-linked list.
class ListNode(object):
    def __init__(self, x):
        self.val = x
        self.next = None

class Solution(object):
    def nextLargerNodes(self, head):
        """
        :type head: ListNode
        :rtype: List[int]
        """
        if head is None:
            return
        
        linkedlist = []

        while head:
            linkedlist.append(head.val)
            head = head.next

        ans = [0 for i in range(len(linkedlist))]
        stack = []
        num = len(linkedlist)-1
        
        for i in range(num, -1, -1):
            while stack and linkedlist[i] >= linkedlist[stack[-1]]:
                stack.pop()
            if stack:    
                ans[i] = linkedlist[stack[-1]]    
            stack.append(i)

        return ans
```
The time complexity is O(n).

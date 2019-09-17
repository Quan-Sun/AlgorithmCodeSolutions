## 问题描述

给定 2 个字符串 a, b. 编辑距离是将 a 转换为 b 的最少操作次数，操作只允许如下 3 种：

1. 插入一个字符，例如：fj -> fxj
2. 删除一个字符，例如：fxj -> fj
3. 替换一个字符，例如：jxj -> fyj

## 思路

用分治的思想解决比较简单，将复杂的问题分解成相似的子问题

假设字符串 a, 共 m 位，从 `a[1]` 到 `a[m]`
字符串 b, 共 n 位，从 `b[1]` 到 `b[n]`
`d[i][j]` 表示字符串 `a[1]-a[i]` 转换为 `b[1]-b[j]` 的编辑距离

那么有如下递归规律（`a[i]` 和 `b[j]` 分别是字符串 a 和 b 的最后一位）：

1. 当 `a[i]` 等于 `b[j]` 时，`d[i][j] = d[i-1][j-1]`, 比如 fxy -> fay 的编辑距离等于 fx -> fa 的编辑距离
2. 当`a[i]`不等于`b[j]`时，`d[i][j]`等于如下 3 项的最小值：
   - `d[i-1][j]` + 1（删除 `a[i]`）， 比如 fxy -> fab 的编辑距离 = fx -> fab 的编辑距离 + 1
   - `d[i][j-1]` + 1（插入 `b[j]`)， 比如 fxy -> fab 的编辑距离 = fxyb -> fab 的编辑距离 + 1 = fxy -> fa 的编辑距离 + 1
   - `d[i-1][j-1]` + 1（将 `a[i]` 替换为 `b[j]`）， 比如 fxy -> fab 的编辑距离 = fxb -> fab 的编辑距离 + 1 = fx -> fa 的编辑距离 + 1

递归边界：

1. `a[i][0] = i`, b 字符串为空，表示将 `a[1]-a[i]` 全部删除，所以编辑距离为 i
2. `a[0][j] = j`, a 字符串为空，表示 a 插入 `b[1]-b[j]`，所以编辑距离为 j

## 代码

按照上面的思路将代码写下来

```python
class Solution(object):
  def edit_distance(self,strA, strB):
    m, n = len(strA), len(strB)
    dp = [[0 for _ in range(n)] for _ in range(m)]
    for i in range(m):
      dp[i][0] = i
    for j in range(n):
      dp[0][j] = j
    for i in range(m):
      for j in range(n):
        if strA[i] == strB[j]:
          dp[i][j] = dp[i-1][j-1]
        else:
          dp[i][j] = min(dp[i-1][j]+1, dp[i][j-1]+1, dp[i-1][j-1]+1)
    return dp[-1][-1]
```

时间复杂度为$O(mn)$.
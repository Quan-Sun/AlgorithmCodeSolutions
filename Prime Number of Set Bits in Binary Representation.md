Given two integers `L` and `R`, find the count of numbers in the range [`L`, `R`] (inclusive) having a prime number of set bits in their binary representation.

(Recall that the number of set bits an integer has is the number of 1s present when written in binary. For example, `21` written in binary is `10101` which has `3` set bits. Also, `1` is not a prime.)

Example:
```
Input: L = 6, R = 10
Output: 4
Explanation:
6 -> 110 (2 set bits, 2 is prime)
7 -> 111 (3 set bits, 3 is prime)
9 -> 1001 (2 set bits , 2 is prime)
10->1010 (2 set bits , 2 is prime)
```

```
Input: L = 10, R = 15
Output: 5
Explanation:
10 -> 1010 (2 set bits, 2 is prime)
11 -> 1011 (3 set bits, 3 is prime)
12 -> 1100 (2 set bits, 2 is prime)
13 -> 1101 (3 set bits, 3 is prime)
14 -> 1110 (3 set bits, 3 is prime)
15 -> 1111 (4 set bits, 4 is not prime)
```

**NOTE**:
  - `L`, `R` will be integers `L` <= `R` in the range [1, 10<sup>6</sup>].
  - `R - L` will be at most 10000.
  
***04/09/2019***

Idea: The biggest possible integer is 10<sup>6</sup>, so number of bits is 20 at most, and we know prime numbers within 20 are [2, 3, 5, 7, 11, 13, 17, 19]. We firstly transfer the integers to binary numbers; secondly, counting the number of '1'; lastly, if the counting number is int the prime number list, return True, otherwise return False.

**solution 1**
```python
class Solution(object):
    def countPrimeSetBits(self, L, R):
        """
        :type L: int
        :type R: int
        :rtype: int
        """
        if not L or not R:
            return
        count = 0
        prime = [2, 3, 5, 7, 11, 13, 17, 19]
        for n in range(L, R+1):
            bn = bin(n)
            bits = bn.count('1')
            if bits in prime:
                count += 1
        return count
```
The time complexity is O(R-L).

**solution 2**
```python
class Solution(object):
    def countPrimeSetBits(self, L, R):
        """
        :type L: int
        :type R: int
        :rtype: int
        """
        # binary mask -> 0b10100010100010101100 is the bit wise representation of 665772
        if not L or not R:
            return
        # count bits (when we do bitwise operations, the integers are transferred into binary numbers, such as 1 == 001)
        #def bits(n):
        #     s = 0
        #      while n != 0:
        #         s += n & 1
        #         n >>= 1
        #     return s
        def bits(n):
            s = 0
            while n != 0:
                n &= n - 1;
                s += 1
            return s

        ans = 0
        while L <= R:
            if (665772 >> bits(L)) & 1 > 0: ans += 1
            L += 1
        return ans
```
The time complexity is O(R-L).

**solution 3: very fast**
```python
class Solution(object):
    def countPrimeSetBits(self, L, R):
        """
        :type L: int
        :type R: int
        :rtype: int
        """
        if not L or not R: return

        def under(m):
            prime = {2, 3, 5, 7, 11, 13, 17, 19}
            cnt1_m = 0
            count = 0
            K = 0;
            for n in range(19, -1, -1):
                if m & (1 << n):
                    cnt1_m += 1
                    nCk = 1
                    for k in range(n+1): # combinatorial
                        if k + K in prime:
                            count += nCk
                        nCk = nCk * (n-k) / (k+1)
                    K += 1
            return count if cnt1_m not in prime else count + 1
        
        return under(R) - under(L-1)
```
The time complexity is O(19*20*2).

Maximum Product Subarray

[https://oj.leetcode.com/problems/maximum-product-subarray/](https://oj.leetcode.com/problems/maximum-product-subarray/)

* 遍历数组，想象我们记录一个sub array, 这个sub array里面元素的乘积就对应当前已知的极值。每次访问一个元素时，我们需要更新这个sub array和极值，有两种选择：
  * 把该元素放入考虑的sub array中
  * 抛弃之前累积的sub array, 把该元素当做新的sub array
* 考虑到数组中的数字有正有负，我们必须同时关注（正的）最大值和（负的）最小值。

```javascript
public int maxProduct(int[] A) {
  assert A.length > 0;
  int max = A[0], min = A[0], maxAns = A[0]; 
  for (int i = 1; i < A.length; i++) {
      int mx = max, mn = min;
      max = Math.max(Math.max(A[i], mx * A[i]), mn * A[i]);
      min = Math.min(Math.min(A[i], mx * A[i]), mn * A[i]);
      maxAns = Math.max(max, maxAns);
  }
   return maxAns;
}
```

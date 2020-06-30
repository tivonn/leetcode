## link

https://leetcode.com/problems/container-with-most-water/

## description

```
Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container and n is at least 2.

The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.

Example:

Input: [1,8,6,2,5,4,8,3,7]
Output: 49
```

## solution

面积=长*宽，使用双指针找高度的瓶颈

```javascript
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function (height) {
  var getMax = function (start, end) {
    return (end - start) * Math.min(height[start], height[end])
  }
  var start = 0,
      end = height.length - 1,
      max = 0,
      current = 0
  while (start < end) {
    current = getMax(start, end)
    if (current > max) {
      max = current
    }
    if (height[start] < height[end]) {
      start++
    } else {
      end--
    }
  }    
  return max
}
```
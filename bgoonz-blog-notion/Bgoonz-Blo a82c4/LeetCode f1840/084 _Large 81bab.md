# 084._Largest_Rectangle_in_Histogram

## [84. Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/description/)

### Problem:

Given *n* non-negative integers representing the histogram's bar height where the width of each bar is 1, find the area of largest rectangle in the histogram.

![https://leetcode.com/static/images/problemset/histogram.png](https://leetcode.com/static/images/problemset/histogram.png)

histogram.png

Above is a histogram where width of each bar is 1, given height = `[2,1,5,6,2,3]`.

![https://leetcode.com/static/images/problemset/histogram_area.png](https://leetcode.com/static/images/problemset/histogram_area.png)

histogram_area.png

The largest rectangle is shown in the shaded area, which has area = `10` unit.

**Example:**

```
Input: [2,1,5,6,2,3]
Output: 10
```

### Solution:

The height of a rectangle is determined by the lowest bar inside of it. So the core idea is, for each bar, assume it is the lowest bar and see how far it can expand. Then we have `len(heights)` rectangles. Return the max area.

For a bar `b` whose height is `h`, find the closest bar `b1` on the left that is lower than `h`, and `b2` on the right. The area of the rectangle is `h * (i2 - i1 - 1)`.

Notice that if we just loop the bars from left to right, `b1` and `b2` of each bar may overlap.

[Untitled](084%20_Large%2081bab/Untitled%20D%20db53e.csv)

Observe how `i1` and `i2` changes depending on the height.

To reduce O(*n^2*) to O(*n*), we use a stack to store incremental `b`s. Because `b1` and `b2` are both lower than `b`, whenever we reach a bar that is lower than the top of the stack, we know it's a `b2`. So stack top is a `b`. Second top is a `b1`. Keep popping the `b` to calculate areas until `b2` is no longer lower than stack top.

```
/** * @param {number[]} heights * @return {number} */let largestRectangleArea = function (heights) {  const stack = [-1];  let max = 0;  for (let i2 = 0; i2 <= heights.length; i2++) {    while ((heights[i2] || 0) < heights[stack[stack.length - 1]]) {      const i = stack.pop();      const i1 = stack[stack.length - 1];      max = Math.max(max, heights[i] * (i2 - i1 - 1));    }    stack.push(i2);  }  return max;};
```

---

☆*: .｡. o(≧▽≦)o .｡.:*☆☆*: .｡. o(≧▽≦)o .｡.:*☆☆*: .｡. o(≧▽≦)o .｡.:*☆

---

---

☆*: .｡. o(≧▽≦)o .｡.:*☆☆*: .｡. o(≧▽≦)o .｡.:*☆

---

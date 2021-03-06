
## 柱状图中最大的矩形
> 给定 n 个非负整数，用来表示柱状图中各个柱子的高度。每个柱子彼此相邻，且宽度为 1 。          
> 求在该柱状图中，能够勾勒出来的矩形的最大面积。   

![avatar](https://raw.githubusercontent.com/chenqf/technical-summary/master/src/leetCode/QA/084.largestRectangleArea/img.png)
> 以上是柱状图的示例，其中每个柱子的宽度为 1，给定的高度为 [2,1,5,6,2,3]。   

![avatar](https://raw.githubusercontent.com/chenqf/technical-summary/master/src/leetCode/QA/084.largestRectangleArea/img1.png)
> 图中阴影部分为所能勾勒出的最大矩形面积，其面积为 10 个单位。

### 示例 1
> 输入: [2,1,5,6,2,3]     
> 输出: 10        


### 解法
```javascript 1.8
let largestRectangleArea = function(heights) {
    let res = 0;
    let st = [];
    heights.push(0);
    for (let i = 0; i < heights.length; ++i) {
        if (!st.length || heights[st[st.length - 1]] < heights[i]) {
            st.push(i);
        } else {
            let cur = st.pop();
            res = Math.max(res, heights[cur] * (!st.length ? i : (i - st[st.length - 1] - 1)));
            --i;
        }
    }
    return res;
};
```

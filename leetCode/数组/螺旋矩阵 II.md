# 59. 螺旋矩阵 II
给你一个正整数 n ，生成一个包含 1 到 n2 所有元素，且元素按顺时针顺序螺旋排列的 n x n 正方形矩阵 matrix 。
```javascript
/**
 * @param {number} n
 * @return {number[][]}
 */
var generateMatrix = function(n) {
    let dp = new Array(n).fill([]);
    dp = dp.map(ele=>{
        return new Array(n).fill(0);
    });
    let i = 0, j= 0, flag = true, res = 0;
    while(i<n && j<n){
        res++;
        dp[i][j] = res;
        if((dp[i][j-1] === undefined || dp[i][j-1] > 0) && (dp[i-1]=== undefined || dp[i-1][j]>0) && dp[i][j+1] ===0) {
            j++
        } else if((dp[i-1] === undefined || dp[i-1][j] > 0) && (dp[i][j+1]=== undefined || dp[i][j+1]>0) &&dp[i+1]&&dp[i+1][j]===0 ){
           i++;
        } else if((dp[i+1] === undefined || dp[i+1][j] > 0) && (dp[i][j+1]=== undefined || dp[i][j+1]>0) && dp[i][j-1] ===0){
            j--;
        } else if((dp[i+1] === undefined || dp[i+1][j] > 0) && (dp[i][j-1]=== undefined || dp[i][j-1]>0) &&dp[i-1]&&dp[i-1][j]===0 ){
            i--;
        } else {
            return dp
        }
    }
};
```
## 2022-3-11

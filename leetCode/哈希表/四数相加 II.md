# 454. 四数相加 II
给你四个整数数组 nums1、nums2、nums3 和 nums4 ，数组长度都是 n ，请你计算有多少个元组 (i, j, k, l) 能满足：

0 <= i, j, k, l < n
nums1[i] + nums2[j] + nums3[k] + nums4[l] == 0

```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @param {number[]} nums3
 * @param {number[]} nums4
 * @return {number}
 */
var fourSumCount = function(nums1, nums2, nums3, nums4) {
    let map1 = new Map(), map2 = new Map(), res = 0;
    for(let i=0;i<nums1.length;i++){
        for(let j=0;j<nums2.length;j++){
            map1.set([i,j], nums1[i] + nums2[j])
        }
    }
    for(let i=0;i<nums3.length;i++){
        for(let j=0;j<nums4.length;j++){
            let val = nums3[i] + nums4[j];
            if (map2.has(val)) {
                map2.set(val, map2.get(val) + 1);
            } else {
                map2.set(val, 1);
            }
        }
    }
    for(let key1 of map1.keys()){
        let item = map1.get(key1);
        if(map2.has(0-item)){
            res += map2.get(0-map1.get(key1));
        }
    }
    return res;
};
```
## 2022-3-25

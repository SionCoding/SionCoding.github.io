title: List.add 方法注意点
author: Sion
tags:
  - 算法
  - LeetCode
categories:
  - 技术
date: 2019-08-06 18:24:00
---
- 在Java中，往list中添加元素时，如果是基础类型数据，则直接存储在栈中；
- 如果添加的是引用类型对象时，则将对象的引用传给放在了list中，该引用指向的对象发生变化时，那么对应的list里的内容也就跟着发生变化了。
- 因此，在将结果集循环放入到对象中，要特别注意每次循环都需要new一个新对象。

<!-- more -->

例：

```java

/* 
 * LeetCode: [46] 全排列
 *
 * 给定一个没有重复数字的序列，返回其所有可能的全排列。
 * 
 * 示例:
 * 
 * 输入: [1,2,3]
 * 输出:
 * [
 * ⁠ [1,2,3],
 * ⁠ [1,3,2],
 * ⁠ [2,1,3],
 * ⁠ [2,3,1],
 * ⁠ [3,1,2],
 * ⁠ [3,2,1]
 * ]
 * 
 */
 
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> tmpList = new ArrayList<>();
        backTrack(res, tmpList, nums);
        return res;
    }

    private void backTrack(List<List<Integer>> res, List<Integer> tmpList, int[] nums) {
        if (tmpList.size() == nums.length) {
            res.add(new ArrayList<>(tmpList));//注意此处不能直接res.add(tmpList);
        } else {
            for (int i = 0; i < nums.length; i++) {
                if (tmpList.contains(nums[i]))
                    continue;
                tmpList.add(nums[i]);
                backTrack(res, tmpList, nums);
                tmpList.remove(tmpList.size() - 1);
            }
        }
    }
}

```
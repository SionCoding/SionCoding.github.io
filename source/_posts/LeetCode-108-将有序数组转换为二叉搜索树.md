title: 'LeetCode: 108.将有序数组转换为二叉搜索树'
author: Sion
tags:
  - 算法
  - LeetCode
categories:
  - 技术
date: 2019-08-08 10:09:00
---
#### [108] 将有序数组转换为二叉搜索树
- 将一个按照升序排列的有序数组，转换为一棵高度平衡二叉搜索树。
- 本题中，一个高度平衡二叉树是指一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过 1。

<!-- more -->

```java

 /* 
 * 示例:
 * 
 * 给定有序数组: [-10,-3,0,5,9],
 * 
 * 一个可能的答案是：[0,-3,9,-10,null,5]，它可以表示下面这个高度平衡二叉搜索树：
 * 
 * ⁠     0
 * ⁠    / \
 * ⁠  -3   9
 * ⁠  /   /
 * ⁠-10  5
 * 
 * 
 */
 
 class Solution {
    public TreeNode sortedArrayToBST(int[] nums) {
        return sortedArrayToBST(nums, 0, nums.length - 1);
    }

    private TreeNode sortedArrayToBST(int[] nums, int left, int right) {
        if (left > right) return null;
        int mid = left + (right - left) / 2;
        TreeNode root = new TreeNode(nums[mid]);
        root.left = sortedArrayToBST(nums, left, mid - 1);
        root.right = sortedArrayToBST(nums, mid + 1, right);
        return root;
    }
}

```

##### 两个注意点
- `int mid = (left + right) / 2;` 会产生溢出，所以应该用 `int mid = left + (right - left) / 2;` 代替
- ` / 2` 可以用 ` >> 1` 向右移位代替
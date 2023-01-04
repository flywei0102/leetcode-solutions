/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean flipEquiv(TreeNode root1, TreeNode root2) {
        if(root1 == root2) return true;
        if(root1 == null || root2 == null || root1.val != root2.val) return false;
        return (flipEquiv(root1.left, root2.left) && flipEquiv(root1.right, root2.right)) || (flipEquiv(root1.left, root2.right) && flipEquiv(root1.right, root2.left));
    }
}

// 若是对两个左右子结点分别调用递归函数均返回 true，说明整个肯定是返回 true 的没有问题，
// 即便返回 false 了也不要紧，因为这里还可以利用交换子结点的性质再调用一遍递归函数，此时 root1 的左子结点对应 root2 的右子结点，root1 的右子结点对应 root2 的左子结点，这个若返回 true 的话也行
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
    int sum = 0;
    public int sumNumbers(TreeNode root) {
        recurseTree(root, 0);
        return sum;
    }

    public void recurseTree(TreeNode node, Integer curSum){
        if( node == null) return;
        curSum = curSum * 10 + node.val;    // need attention
        if(node.left == null && node.right == null){
            sum += curSum;
        }
        this.recurseTree(node.left, curSum);
        this.recurseTree(node.right, curSum);
    }
}
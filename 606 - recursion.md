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
    public String tree2str(TreeNode root) {
        StringBuilder res = new StringBuilder();
        this.recurseTree(root, res);
        return res.toString();
    }

    private void recurseTree(TreeNode node, StringBuilder res){
        if(node == null) return;
        res.append(Integer.toString(node.val));
        if(node.left == null && node.right == null) return;
        res.append("(");
        this.recurseTree(node.left, res);
        res.append(")");
        if(node.right != null){
            res.append("(");
            this.recurseTree(node.right, res);
            res.append(")");
        }

    }
}


// DFS - recursion

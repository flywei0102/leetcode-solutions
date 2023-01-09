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

    Stack<TreeNode> stack = new Stack<>();
    public TreeNode convertBST(TreeNode root) {
        inorder(root);   // store the value of nodes in the list
        // starting from the end of the list to build the great tree
        int sum = 0;
        while(!stack.isEmpty()){
            TreeNode cur = stack.pop();
            cur.val = cur.val + sum;
            sum = cur.val;
        }
        return root;
    }
    // inorder traversal: left - root - right
    public void inorder(TreeNode root){
        if(root == null)return;
        this.inorder(root.left);
        this.stack.push(root);
        this.inorder(root.right);
    }
}


// inorder traversal : left - root - right
// no need to use pair<>
// my solution
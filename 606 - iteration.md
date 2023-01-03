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
        if(root == null) return "";
        Stack<TreeNode> stack = new Stack<>();
        stack.push(root);
        Set<TreeNode> visited = new HashSet<>();  // Set - Map
        StringBuilder res = new StringBuilder();

        while(!stack.isEmpty()){
            root = stack.peek();
            if(visited.contains(root)){
                stack.pop();
                res.append(")");
            }else{
                visited.add(root);
                res.append("(" + root.val);
                if(root.left == null && root.right != null) res.append("()");
                if(root.right != null) stack.push(root.right);
                if(root.left != null) stack.push(root.left);
            }
        }
        return res.substring(1, res.length() - 1);
    }
}


// DFS - iteration
// set 一维数组 - map 二维数组[[key, value],[key, value]...], 都不能含有重复的元素，都是由linkedlist实现
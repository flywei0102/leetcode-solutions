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
    public int sumNumbers(TreeNode root) {
        if(root == null) return 0;
        int sum = 0;
        Deque<Pair<TreeNode,Integer>> queue = new ArrayDeque<>();
        queue.push(new Pair(root, 0));
        int curSum = 0;

        while(!queue.isEmpty()){
            Pair<TreeNode, Integer> node = queue.pop();
            root = node.getKey();
            curSum = node.getValue();
            if(root != null){
                curSum = curSum * 10 + root.val;
                if(root.left == null && root.right == null){
                    sum += curSum;
                }else{
                    queue.push(new Pair(root.left, curSum));
                    queue.push(new Pair(root.right, curSum));
                }
                
            }
            
        }       
        return sum;
    }
    
}


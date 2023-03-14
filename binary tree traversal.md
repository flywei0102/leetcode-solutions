**Level-order traversal**
Breadth-First-Search(BFS)

class Solution{
        public List<List<Integer>> bfs(TreeNode root){
                List<List<Integer>> ans = new ArrayList<>;
                if(root == null) return ans;
                Queue<TreeNode> queue = new LinkedList<>();  
                queue.offer(root);
                int level = 0;
                while(!queue.isEmpty()){
                        List<Integer> eachLevel = new ArrayList<>();
           //             ans.add(new ArrayList<Integer>());
                        int levelLength = queue.size();
                        for(int i = 0; i < levelLength; i++){
                                TreeNode curr = queue.poll();
                                eachLevel.add(curr.val);
            //                    ans.get(level).add(curr.val);
                                if(curr.left != null) queue.offer(curr.left);
                                if(curr.right != null) queue.offer(curr.right);
                        }
                        level ++;
                }
                return ans;
        }
}
-------------------------------------------------------------------------

**pre-order traversal**
<root - left - right>
**iterative solution**
class Solution{
        public List<Integer>  preorderTraversal(TreeNode root){
                Stack<TreeNode> stack = new LinkedList<>();
                List<Integer> output = new LinkedList<>();
                if(root == null) return output;
                stack.add(root);  
                while(!stack.isEmpty){
                        TreeNode curr = stack.poll();
                        output.add(curr.val); 
                        if(curr.right != null) stack.push(curr.left);
                        if(curr.left != null) stack.push(curr.right);
                }
                return output;
         }
}

**recursive solution**
class Solution{
        // main method
        public List<>() preorderTraversal(TreeNode root){
                List<Integer> output = new ArrayList<>();
                preorderTra(root, output);
                return output; 
        }
        // helper preorder traverse method
        private void preorderTra(TreeNode root, List<Integer> output){
                if(root == null) return;
                output.add(root.val);
                preorderTra(root.left, output);       // traverse the left subtree
                preorderTra(root.right, output);     // traverse the right subtree
        }
}

-------------------------------------------------------------------------

**in-order traversal**
<left - root - right>

**iterative solution**
class Solution{
        public List<Integer> inorderTraversal(TreeNode root){
                Stack<TreeNode> stack = new LinkedList<>();
                List<Integer> output = new LinkedList<>();
                if(root == null) return output;
                TreeNode curr = root;
                while(!stack.isEmpty() || curr != null){
                        while(curr != null){
                                stack.push(curr);
                                curr = curr.left;
                        }
                        curr = stack.pop();
                        output.add(cur.val);
                        curr = curr.right;
                }
                return output;
        }
}

**recursive solution**
class Solution{
        public List<Integer> inorderTraversal(TreeNode root){
                List<Integer> output = new ArrayList<>();
                inorderTra(root, output);
                return output;
        }
        private void inorderTra(TreeNode root, List<Integer> output){
                if(root == null) return;
                inorderTra(root.left, output);       // traverse left subtree
                output.add(root.val);                    // root
                inorderTra(root.right, output);     // traverse right subtree
        }
}

-------------------------------------------------------------------------

**postorder traversal**
<left - right - root>

**iterative solution**
class Solution{
        public List<Integer> postorderTraversal(TreeNode root){
                Stack<TreeNode> stack = new LinkedList<>();
                List<Integer> output = new LinkedList<>();
                if(root == null) return output;
                stack.add(root);
                while(!stack.isEmpty()){
                        TreeNode curr = stack.pop();
                        output.add(0, curr.val);    //  linkedlist add(index, value), equals to insert method
                        if(curr.left != null) stack.push(curr.left);
                        if(curr.right != null) stack.push(curr.right);
                }
                return output;
        }
}


**recursive solution**
class Solution{
        public List<Integer> postorderTraversal(TreeNode root){
                List<Integer> output = new ArrayList<>();
                postorderTra(root, output);
                return output;
        }
        private void postorderTra(TreeNode root, List<Integer> output){
                if(root == null) return;
                postorderTra(root.left, output);       // traverse left subtree
                postorderTra(root.right, output);    // traverse right subtree
                output.add(root.val);                        // root
        }
}

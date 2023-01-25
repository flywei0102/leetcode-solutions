class Solution {
    public int[] nextGreaterElements(int[] nums) {
        int[] res = new int[nums.length];
        Stack<Integer> stack = new Stack<>();

        for(int i = 2 * nums.length - 1; i >= 0; --i){
            while(!stack.isEmpty() && nums[stack.peek()] <= nums[i % nums.length]){
                stack.pop();
            }
            res[i % nums.length] = stack.empty() ? -1 : nums[stack.peek()];
            stack.push(i % nums.length);
        }
        return res;
    }
}

// a little bit difficult to understand
// stack
// here we double the nums, and now index = [i % nums.length]  
// the key of this solution: when we try to find the next greater number fo the ith number.
// when nums[i+1] <= nums[i], what to do next? -> check nums[i+2]... nums[0]...

// A better way is to check the next greater number of nums[i+1],
// if the next greater number of nums[i+1] <= nums[i], then go on to check the next greater number (stack.pop())

class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        Stack<int[]> stack = new Stack<>();
        Stack<int[]> stack2 = new Stack<>();
        int[] ans = new int[temperatures.length];
        stack.push(new int[]{0, temperatures[0]});
        for(int i = 1; i < temperatures.length; i ++){
            if(temperatures[i] <= stack.peek()[1]){
                stack.push(new int[]{i, temperatures[i]});
            }else{
                int count = 1;
                while(!stack.isEmpty() && temperatures[i] > stack.peek()[1]){
                    ans[stack.peek()[0]] += count;
                    stack.pop();
                    count ++; 
                }
                // 要把stack上剩余元素对应的ans[] + 此时的count值
                while(!stack.isEmpty()){
                    ans[stack.peek()[0]] += count -1;
                    stack2.push(stack.pop());
                }
                while(!stack2.isEmpty()){
                    stack.push(stack2.pop());
                }
                stack.push(new int[]{i, temperatures[i]});
            }

        } 
        stack.pop();
        while(!stack.isEmpty()){            
            ans[stack.peek()[0]] = 0;
            stack.pop();
        } 
        return ans;      
    }
}

// 超时了
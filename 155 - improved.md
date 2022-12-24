class MinStack {
    Stack<Integer> stack1; 
    Stack<int[]> minStack;


    public MinStack() {
        stack1 = new Stack<Integer>(); 
        minStack = new Stack<int[]>();    
    }
    
    public void push(int val) {
        stack1.push(val);
        if(minStack.isEmpty() || val < minStack.peek()[0] ){
            minStack.push(new int[]{val, 1});
        }else if(val == minStack.peek()[0]){
            minStack.peek()[1]++;
        }
    }
    
    public void pop() {     
        if(stack1.peek().equals(minStack.peek()[0])){
            minStack.peek()[1]--;
            if(minStack.peek()[1] == 0){
                minStack.pop();
            }
        }
        stack1.pop();
    }
    
    public int top() {
        return stack1.peek();
    }
    
    public int getMin() {
        return minStack.peek()[0];        
    }
}

// bug? 这里可以直接更改int[]里某一个元素的值

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(val);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
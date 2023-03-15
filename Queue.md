** circular queue**
// The implementation of the dequeue() method on a normal queue will waste space before the head pointer
// However, using a circular queue can solve this problem

class MyCircularQueue {
    int[] queue;
    int head;
    int tail;
    int size;
    public MyCircularQueue(int k) {
        queue = new int[k];
        head = -1;
        tail = -1;
        size = k;  
    }
    
    public boolean enQueue(int value) {
        if(isFull() == true) return false;
        if(isEmpty()  == true) head = 0;
        tail = (tail + 1) % size;
        queue[tail] = value;
        return true;
    }
    
    public boolean deQueue() {
        if(isEmpty()  == true) return false;
        // if there is only one element left, the array will be empty after deQueue() 
        if(head == tail){
            head = -1;
            tail = -1;
            return true;
        }
        head = (head + 1) % size;  // move the head pointer to the next index
        return true;
    }
    
    public int Front() {
        if(isEmpty() == true) return -1;
        return queue[head];
    }
    
    public int Rear() {
        if(isEmpty() == true) return -1;
        return queue[tail];
    }
    
    public boolean isEmpty() {
        return head == -1;
    }
    
    public boolean isFull() {
        return ((tail + 1) % size) == head;
    }
}

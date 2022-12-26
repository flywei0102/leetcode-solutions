/*
// Definition for a Node.
class Node {
    int val;
    Node next;
    Node random;

    public Node(int val) {
        this.val = val;
        this.next = null;
        this.random = null;
    }
}
*/

class Solution {
    public Node copyRandomList(Node head) {
        if(head == null) return null;
        Node cur = head;
        while(cur != null){
            Node newNode = new Node(cur.val);   // clone the current Node and insert it after the current node
            newNode.next = cur.next;
            cur.next = newNode;
            cur = newNode.next;
        }
        cur = head;
        while(cur != null){
            cur.next.random = (cur.random != null) ? cur.random.next : null;    // cloned node‘s random 指向其original node的Random node 的cloned node的
            cur = cur.next.next;
        }
        // apart the list to the original list and its cloned list
        Node curOld = head;
        Node curNew = head.next;
        Node headNew = head.next;

        while(curOld != null){
            curOld.next = curOld.next.next;
            curNew.next = (curNew.next != null) ? curNew.next.next : null;
            curOld = curOld.next;
            curNew = curNew.next;
            
        }
        return headNew;
    }
}

// time complexity -> O(N); space complexity -> O(1)
// 1485 类似: clone binary tree with random pointer




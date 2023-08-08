/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode cur = head;
        int size = 0;
        // reverse the list
        while(cur != null){
            cur = cur.next;
            size ++;
        }
        if(size == n) return head.next;
        // reach to the previous node of the last node
        cur = head;
        int steps = size - n -1 ;
        while(cur.next != null && steps != 0){
            cur = cur.next;
            steps --;
        }
        // remove 
        if(cur.next != null){
            cur.next = cur.next.next;
        }
        return head;
    }
}

// two traversal 

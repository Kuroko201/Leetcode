## Leetcode 24 Swap Nodes in pairs, C++
we can just simply move the pointer.

<img src="https://github.com/Kuroko201/DSA-note/blob/main/Linked_List/pic/leetcode%2024.png?raw=true">

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
        if(head == NULL)return head;
        else if(head->next == NULL)return head;
        ListNode* dummy = new ListNode(0,head);
        ListNode* curr = dummy;

        while(curr->next != NULL && curr->next->next != NULL){
           ListNode* first = curr->next; 
           ListNode* second = curr->next->next;
           first->next = second->next; // swap, just like M1 point to M3 in the example
           second->next = first; // swap, just like M2 point to M1 in the example
           curr->next = second; // curr is [0,1,2,3,4], it will point to 1. now the sequence has change to [0,2,1,3,4] in loop 1, curr should point to 2.
           curr=curr->next->next; // swap every two steps
        }
        return dummy->next;
    }
};
```

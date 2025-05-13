# C++

## 1. Using vector:
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
    ListNode* reverseList(ListNode* head) {
        if (head == NULL)return NULL;
        vector<int> list = {};
        while(head != NULL){
            list.push_back(head->val);
            head = head->next;
        }
        ListNode* reverse = new ListNode();
        ListNode* curr = reverse;

        for(int i = list.size()-1; i > -1; i--){
            curr->next = new ListNode(list[i]);
            curr = curr->next;
        }
        ListNode* ans = reverse->next;
        delete reverse;
        return ans;
    }
};
```
### 2. Using prev
<img src="https://github.com/Kuroko201/DSA-note/blob/main/Linked_List/pic/leetcode206.png?raw=true">
<img src="https://github.com/Kuroko201/DSA-note/blob/main/Linked_List/pic/leetcode206(2).png?raw=true">

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
    ListNode* reverseList(ListNode* head) {  // assume that the node is [1,2,3,4,5]
        ListNode* prev = NULL; // END of the node is NULL
        ListNode* curr = head;

        while(curr != NULL){
           ListNode* nextNode = curr->next; // record the next node first.
           curr->next = prev; // link backward 
           prev = curr; // update the prev(changing the starting point of prev).
           curr = nextNode; // move to the next node
        }
        return prev;
    }
};
```

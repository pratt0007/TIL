# Odd Even Linked List
https://leetcode.com/problems/odd-even-linked-list/
### Put first all the elements at odd ind and then all the elements at the even ind in a linked list
# Method 1-
```CPP
Make 2 different linked list where one is of odd and other is of even and at last merge
SPACE COMP = 0(N)
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
    ListNode* oddEvenList(ListNode* head) {
        ListNode l1(0), l2(0);
        ListNode* p1 = &l1;
        ListNode* p2 = &l2;

        unsigned index = 1;
        while (head) {
            if (index++ % 2 == 1)
                p1 = p1->next = head;
            else
                p2 = p2->next = head;
            head = head->next;
        }

        p1->next = l2.next;
        p2->next = nullptr;
        return l1.next;
    }
};
```
# Method 2 0(1) space comp
```cpp
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
    ListNode* oddEvenList(ListNode* head) {

        if(head == NULL)
            return head;

        ListNode* odd = head;
        if(odd->next == NULL)
            return head;
        
        ListNode* even = odd->next;
        if(even->next == NULL)
            return head;

        ListNode* temp = even->next;

        while(even->next) {
            even->next = temp->next;
            temp->next = odd->next;
            odd->next = temp;

            odd = odd->next;
            even = even->next;
            if(even == NULL)
                return head;
            temp = even->next;
        }

        return head;

    }
};
```

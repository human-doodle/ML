## Determine if linked list has a cycle

To determine if a linked list has a cycle, you can use the "Floyd's Cycle Detection Algorithm" (also known as the "tortoise and hare algorithm"). This algorithm uses two pointers, a slow pointer (tortoise) and a fast pointer (hare), to traverse the linked list.

Here's the step-by-step approach to detect a cycle in a linked list:

Initialize both the slow and fast pointers to the head of the linked list.
Move the slow pointer one step at a time by setting it to slow = slow.next.
Move the fast pointer two steps at a time by setting it to fast = fast.next.next.
If there is a cycle in the linked list, the slow and fast pointers will eventually meet at the same node.
If the fast pointer reaches the end of the linked list (i.e., it becomes None), then there is no cycle.
Return true if the slow and fast pointers meet, indicating the presence of a cycle. Otherwise, return false.

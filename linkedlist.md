# Basic Algorithms
## Reversing a linked list
```cpp
ListNode* prev = nullptr;
ListNode* curr = head;
while (curr) {
  ListNode* next = curr->next;
  curr->next = prev;
  prev = curr;
  curr = next;
}
```
`prev` will hold the head

## Get start of second half
### When the last element is needed
We want to make sure fast pointer `d` does not go null as we want to derive last element from it.
`s = head, d = aux, while (d && d.next && d.next.next)`
```
ODD    EVEN
A d    A d
0   s  0   s
1 d s  1 d s
2   s  2   s
3 d    3 d
4
If first half should get mid node, do (if d.next: s = s.next) 
```
### When the last element is not needed 
We can ditch the `d.n.n` and `aux` setup
#### When first half should get the mid element
`s = head, d = head, while (d)`
```text
ODD     EVEN
0 d s   0 d s 
1   s   1   s
2 d s   2 d s
3   s   3
4 d     N d
N d
```
#### When second half should get the mid element
`s = head, d = head.next, while (d)`
```
ODD     EVEN
0   s   0 d s 
1 d s   1   s
2   s   2 d s
3 d     3
4       N d
N d
```
# Problems
## 143. Reorder List
Get second half beginning, reverse it and string them together

## 1669. Merge In Between Linked Lists
Get a-1, b+1, m-1 nodes and string them together.

## 2130. Maximum Twin Sum of a Linked List
Reverse half. If adventurous reverse slow ptr while getting mid.

## 2487. Remove Nodes From Linked List
Monotonic stack, rebuilding the list at the same time.


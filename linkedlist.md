# Get start of second half
### When the last element is not needed and the first half should get the mid element
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
### When the last element is not needed and the second half should get the mid element
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
### When the last element is needed
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

# 1669. Merge In Between Linked Lists
* Get a-1, b+1, m-1 nodes and string them together

# 2487. Remove Nodes From Linked List
* monotonic stack, rebuilding the list at the same time


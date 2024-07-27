# Algorithms
* BFS have time O(n+e),space(v) = max number of item in queue
# Problems
## 802. Find Eventual Safe States
`bool dfs` with state `set<int> visited`.
Cyclic means node is not ESS, parent is ESS if no children is not ESS.
## 1129. Shortest Path with Alternating Colors
bfs with state `vector<int> ansFromRed,ansFromBlue`

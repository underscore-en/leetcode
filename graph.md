# Problems
## 802. Find Eventual Safe States
`bool dfs` keeping `set<int> visited`.
Cyclic means node is not ESS, parent is ESS if no children is not ESS.

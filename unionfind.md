```cpp
vector<int> rank(n);
vector<int> id(n); for (int i=0;i<n;i++) id[i]=i;
function<int(int)> find = [&](int a) {
    int parent = id[a];
    if (parent == a) return a;
    id[a] = find(parent);
    return id[a];
};
auto unify = [&](int a, int b) {
    int pa=find(a), pb=find(b);
    if (pa == pb) return true;
    if (rank[pa] >= rank[pb]) {
        rank[pa] == rank[pb] ? rank[pa]++ : 0;
        id[pb] = pa;
    } else id[pa] = pb;
    return false;
};
```
With path compression the algorithm takes O(mα(n)) ~ O(4m); m operation, n elements.

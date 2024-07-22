```cpp
#include <iostream>
#include <vector>
using namespace std;
struct Foo {
    Foo(int n) : parents(vector<int>(n)), rank(vector<int>(n, 0)) {
        for (int i=0; i<n; i++) {
            parents[i] = i;
        }
    }
    vector<int> parents;
    vector<int> rank; // only rank of root matters
    int find(int i) {
      int parent = parents[i];
      if (parent == i) return i;
      parents[i] = find(parent); // point all along the path to root
      return parents[i];
    }
    
    void unify(int i, int j) {
      int p1 = find(i);
      int p2 = find(j);
      if (p1 == p2) return;
      if (rank[p1] >= rank[p2]) { // larger one become parent to minimize depth
        if (rank[p1] == rank[p2]) rank[p1]++;
        parents[p2] = p1;
      } else {
        parents[p1] = p2;
      }
    }
};

int main() {
    Foo f(5);
    auto printResult = [&]() { for (int i=0;i<5; i++) { cout << f.find(i) << ","; } cout << endl;};
    f.unify(0,1); f.unify(1,2); f.unify(3,4); printResult(); // 0,0,0,3,3
    f.unify(0,2); f.unify(1,4);               printResult(); // 0,0,0,0,0
    return 0;
}
```

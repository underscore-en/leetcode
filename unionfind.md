```cpp
#include <iostream>
#include <vector>
using namespace std;
struct Foo {
    Foo(int n) : id(vector<int>(n)), rank(vector<int>(n, 0)) {
        for (int i=0; i<n; i++) {
            id[i] = i;
        }
    }
    vector<int> id;
    vector<int> rank; // only rank of root matters
    int find(int i) {
      int parent = id[i];
      if (parent == i) return i;
      id[i] = find(parent); // path compression
      return id[i];
    }
    
    void unify(int i, int j) {
      int p1 = find(i);
      int p2 = find(j);
      if (p1 == p2) return;
      if (rank[p1] >= rank[p2]) { // larger one become parent to minimize depth
        if (rank[p1] == rank[p2]) rank[p1]++;
        id[p2] = p1;
      } else {
        id[p1] = p2;
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
With path compression the algorithm takes O(mα(n)) ~ O(4m); m operation, n elements.

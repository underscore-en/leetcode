```cpp
#include <iostream>
#include <vector>
using namespace std;
struct Foo {
    Foo(int n) : parents(vector<int>(n)), size(vector<int>(n, 0)) {
        for (int i=0; i<n; i++) {
            parents[i] = i;
        }
    }
    vector<int> parents;
    vector<int> size; // only size of root matters
    int findset(int i) {
      int parent = parents[i];
      if (parent == i) return i;
      parents[i] = findset(parent); // point all along the path to root
      return parents[i];
    }
    
    void unify(int i, int j) {
      int p1 = findset(i);
      int p2 = findset(j);
      if (p1 == p2) return;
      if (size[p1] >= size[p2]) { // larger one become parent to minimize depth
        if (size[p1] == size[p2]) size[p1]++;
        parents[p2] = p1;
      } else {
        parents[p1] = p2;
      }
    }
};

int main() {
    Foo f(5);
    auto printResult = [&]() { for (int i=0;i<5; i++) { cout << f.findset(i) << ","; } cout << endl;};
    f.unify(0,1); f.unify(1,2); f.unify(3,4); printResult(); // 0,0,0,3,3
    f.unify(0,2); f.unify(1,4);               printResult(); // 0,0,0,0,0
    return 0;
}
```

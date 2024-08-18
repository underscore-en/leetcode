# Problems

## 49. Group Anagrams

Use counting sort on string for computing the key.

```cpp
class Solution {
public:
    string sort(const string& sv, vector<int>& v) {
        std::fill(v.begin(), v.end(), 0);
        for (auto& c: sv) {
            v[c-'a']++;
        }
        string s;
        for (int j=0;j<26;j++) {
            for (int i=0;i<v[j];i++) {
                s.push_back(j+'a');
            }
        }
        return s;
    }
    
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        unordered_map<string, vector<string>> m;
        vector<int> count(26);

        for (auto& str: strs) {
            string key = sort(str, count);
            if (!m.contains(key)) {
                m[key] = vector<string>();
            } 
            m[key].push_back(str);
        }

        vector<vector<string>> ans;  
        for (auto&p: m) {
            ans.push_back(std::move(p.second));
        }

        return ans;
    }
};
```

Time Complexity `O(NMlgM), M= MAX(strlen)`

Space Complexity `O(NM)`

## 304. Range Sum Query 2D - Immutable

Caching sum from (0,0) to (i,j)

```cpp
class NumMatrix {
public:
    vector<vector<int>> sum;
    NumMatrix(vector<vector<int>>& matrix) {
        int R = matrix.size();
        int C = matrix[0].size();
        for (int i=0;i<R;i++) {
            sum.emplace_back(C, 0);
        }
        function<int(int,int)> access = [&](int r, int c) {
            if (r < 0 || c < 0) {
                return 0;
            }
            return sum[r][c];
        };
        for (int r=0;r<R;r++) {
            for (int c=0;c<C;c++) {
                sum[r][c] = matrix[r][c] + access(r-1, c) + access(r, c-1) - access(r-1,c-1);
            }
        }
    }
    
    int sumRegion(int row1, int col1, int row2, int col2) {
        function<int(int,int)> access = [&](int r, int c) {
            if (r < 0 || c < 0) {
                return 0;
            }
            return sum[r][c];
        }; 
        return sum[row2][col2] - access(row1-1,col2) - access(row2,col1-1) + access(row1-1,col1-1);

    }
};

/**
 * Your NumMatrix object will be instantiated and called as such:
 * NumMatrix* obj = new NumMatrix(matrix);
 * int param_1 = obj->sumRegion(row1,col1,row2,col2);
 */
```

Time (construction) and Space Complexity are both `O(MN)`

## 624. Maximum Distance in Arrays
Distance in either MAX-MIN, MAX-min, max-MIN.
## 280. Wiggle Sort
Invariant: `ans[0:k]` is compliant. If `a[k-1], a[k]` is compliant, continue. Else swapping can still maintain compliant `a[k-2], a[k-1], a[k]`.

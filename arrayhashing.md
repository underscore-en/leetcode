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

Time Complexity `O(NMlgM)`, `M=length`

Space Complexity `O(MN)`

## 624. Maximum Distance in Arrays
Distance in either MAX-MIN, MAX-min, max-MIN.
## 280. Wiggle Sort
Invariant: `ans[0:k]` is compliant. If `a[k-1], a[k]` is compliant, continue. Else swapping can still maintain compliant `a[k-2], a[k-1], a[k]`.

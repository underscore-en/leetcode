# Non-trivial algorithms

## Boyer–Moore Majority Vote Algorithm

Given a list of int, we can find the mode with O(1) space.

```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int counter = 0;
        int candidate;

        for (const auto& n: nums) {
            if (counter == 0) {
                candidate = n;
            }
            counter += (n == candidate) ? 1 : -1;
        }
        return candidate;
    }
};
```

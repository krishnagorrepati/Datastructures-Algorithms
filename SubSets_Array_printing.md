#  Print all sub set of a given array:-

Given a set of **distinct** integers, *nums*, return all possible subsets (the power set).

**Note:** The solution set must not contain duplicate subsets.

**Example:**

```
Input: nums = [1,2,3]
Output:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```





### Solutions 1 (Cascading):-

```
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>> output;
        vector<int> v;
        output.push_back(v);
        for(int i = 0; i < nums.size(); i++)
        {
            int m = output.size();
            for(int j = 0; j < m; j++)
            {
                v = output[j];
                v.push_back(nums[i]);
                output.push_back(v);
            } 
        }
        return output;
    }
};
```



## Solution2 (Using BFS ):-

```
   vector<vector<int>> subsets(vector<int>& nums) {
        if(nums.empty())
            return vector<vector<int>>();
        vector<vector<int>> result;
        queue<tuple<vector<int>, int>> Q;
        int n = static_cast<int>(nums.size());
        for(int idx = 0; idx < n; ++idx) {
            Q.push({{nums[idx]}, idx});
        }
        result.push_back(vector<int>());
        while(!Q.empty()) {
            auto [subset, curr_index] = Q.front();
            Q.pop();
            result.push_back(subset);
            for(int next = curr_index + 1; next < n; ++next) {
                subset.push_back(nums[next]);
                Q.push({subset, next});
                subset.pop_back();
            }
        }
        return result;
    }
```



## Solution 3 (Uisng DFS):-

```
   vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>> result;
        stack<tuple<vector<int>, int>> st;
        st.push({{},0});
        while(!st.empty()) {
            auto [subset, start] = st.top();
            st.pop();
            result.push_back(subset);
            for(size_t idx = start; idx < nums.size(); ++idx) {
                subset.push_back(nums[idx]);
                st.push({subset, idx + 1});
                subset.pop_back();
            }
        }
        return result;
    }
```



## Solution 4 (Bit masking):-

```
std::vector<std::vector<int>> res;
size_t size = nums.size();
std::vector<bool> bitmask(size + 1, false);
while (false == bitmask.back())
{
    std::vector<int> subset;
    for (size_t i = 0; i < size; i++)
    {
        if (bitmask[i])
            subset.push_back(nums[i]);
    }
    res.push_back(subset);
    size_t j = 0;
    bool carry = true;
    while (carry)
    {
        bitmask[j] = !bitmask[j];
        carry = !bitmask[j++];
    }
}
return res;
```



## Solution 5 (using Recursion and Backtracking):-

class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<int> path;
        vector<vector<int>> result;
        printSubSets(nums,result, path,0, nums.size());
        
        return result;
    }
    void printSubSets(vector<int>& nums, vector<vector<int>> &result, vector<int> &path, int pos, int n){
        if(pos == n) {
            result.push_back(path);
            return;
        }
        path.push_back(nums[pos]);
        printSubSets(nums,result, path,pos +1, n);
        path.pop_back();
        printSubSets(nums,result, path,pos +1, n);
        return;
    }
}; 
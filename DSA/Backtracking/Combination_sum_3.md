<h1> For loop inside recursion </h1>
https://leetcode.com/problems/combination-sum-iii/description/
CODE:
class Solution {
public:
    void generateCombos(int idx, int k, int n, vector<int>& temp, vector<vector<int>>& sol){
        if(!k||!n){
            if(!k&&!n) sol.push_back(temp);
            return;
        }

        for(int i=idx;i<=9;i++){
            if(n<i) return;
            
            temp.push_back(i);
            generateCombos(i+1, k-1, n-i, temp, sol);
            temp.pop_back();
        }
    }

    vector<vector<int>> combinationSum3(int k, int n) {
        vector<int> temp;
        vector<vector<int>> sol;

        generateCombos(1, k, n, temp, sol);
        return sol;
    }
};

```
class Solution {
public:
    void f(int k, int curr, int sum, vector<int>& v, vector<vector<int>>& ans) {
        if (curr > 9 || sum < 0) {
            return;
        }

        if (k == 0) {
            if (sum == 0) {
                ans.push_back(v);
            }
            return;
        }

        v.push_back(curr);
        f(k - 1, curr + 1, sum - curr, v, ans);
        v.pop_back();
        f(k, curr + 1, sum, v, ans);
    }

    vector<vector<int>> combinationSum3(int k, int n) {
        vector<int> v;
        vector<vector<int>> ans;

        f(k, 1, n, v, ans);
        return ans;
    }
};
```

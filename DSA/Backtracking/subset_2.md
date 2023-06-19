https://leetcode.com/problems/subsets-ii/description/

1.Loop inside recursion


class Solution {
public:
    void solve(int i,int &n,vector<int> &v,vector<int> &tmp,vector<vector<int>> &ans){
        if(i>=n){
            ans.push_back(tmp);
            return;
        }
        tmp.push_back(v[i]);
        solve(i+1,n,v,tmp,ans); 
        tmp.pop_back();
        while(i+1<n&&v[i+1]==v[i])i++;
        solve(i+1,n,v,tmp,ans);
    }
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        vector<vector<int>> ans;
        vector<int> tmp;
        int n = nums.size();
        solve(0,n,nums,tmp,ans);
        // sort(ans.begin(),ans.end());
        return ans;
    }
};
![image](https://github.com/pratt0007/TIL/assets/100209212/0a3c5fb9-304c-426e-836e-de87d4d64f55)




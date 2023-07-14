```c++
class Solution {
  public:
  void f(int ind ,vector<vector<int>>&ans , vector<int> &candidates, vector<int>&res,int target ){
      if(target==0) {
          ans.push_back(res);
          return;
      }
      if (ind<0 || ind >=candidates.size()|| target<0) return;
      res.push_back(candidates[ind]);
     f(ind + 1, ans, candidates, res, target - candidates[ind]);

      res.pop_back();
      
      while(ind<candidates.size()-1 && candidates[ind] == candidates[ind+1]){
          ind++;
      }
      
      f(ind+1 , ans , candidates , res , target);
  }
    vector<vector<int>> combinationSum2(vector<int> &candidates, int target) {
        sort(candidates.begin() , candidates.end());
        vector<vector<int>>ans;
        vector<int>res;
        f(0 , ans , candidates , res , target);
        return ans;
        // Write your code here
    }
};
```
<h3>STRIVER SOLUTION  -- WHEN AN INDEX IS not picked then all the indexes after the non pick if same should be removed from that recursion</h3>

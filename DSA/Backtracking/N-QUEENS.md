https://leetcode.com/problems/n-queens/
'''c++
class Solution {
public:

    bool checkValid(vector<string> &board, int row, int col, int size){

        // check straight up 
        for(int i = row-1;i>=0; i--){
            if(board[i][col] == 'Q'){
                return false;
            }
        }

        // check diagonals
        for(int i = 1; i<=row; i++){
            if(col-i>=0){
                // left diagonal
                if(board[row-i][col-i] == 'Q'){
                    return false;
                }
            }
            if(col+i <size){
                // right diagonal
                if(board[row-i][col+i] == 'Q'){
                    return false;
                }
            }
        }
        return true;
    }


    void helper(vector<string> &board,vector<vector<string>> &ans, int row, int size){
        if(row == size){
            ans.push_back(board);
            return;
        }

        for(int i = 0; i<size; i++){
            if(checkValid(board, row, i, size)){
                board[row][i] = 'Q';
                helper(board, ans, row+1, size);
                board[row][i] = '.'; // backtrack
            }
        }
    }

    vector<vector<string>> solveNQueens(int n) {
        string str;
        str.append(n, '.');
        vector<string> board(n, str);
        vector<vector<string>> ans;
        helper(board, ans, 0, n);
        return ans;
    }
};
<h2>OPTIMIZATION</h2>
<h3>The optimization can be made in the checking part for placing the queen by making a hash table of (2n-1) length and checking out the ones which are placed. By this we will not have to use while loop inside the isSafe function. </h3>
![image](https://github.com/pratt0007/TIL/assets/100209212/98049c98-5e7b-442a-b93c-945e7fc0be85)

'''c++
class Solution {
public:
    void solve(int i,int& n,vector<string> &tmp, vector<vector<string>> &ans,vector<bool> &c,vector<bool> &md,vector<bool> &td){
        if(i==n){
            ans.push_back(tmp);
            return;
        }
        string str(n,'.');
        for(int j = 0; j < n; j++){
            if((c[j]==false&&md[i-j+n]==false&&td[i+j]==false)){
                str[j] = 'Q';
                c[j] = true;md[i-j+n]=true;td[i+j] = true;
                tmp.push_back(str);
                solve(i+1,n,tmp,ans,c,md,td);
                tmp.pop_back();
                str[j] = '.';
                c[j] = false;md[i-j+n]=false;td[i+j] = false;
            }
        }
    }
    int totalNQueens(int n) {
        vector<vector<string>> ans;
        vector<string> tmp;
        vector<bool> c(n,false),md(2*n+3,false),td(2*n+3,false);
        solve(0,n,tmp,ans,c,md,td);
        return ans.size();
    }
};


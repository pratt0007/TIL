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

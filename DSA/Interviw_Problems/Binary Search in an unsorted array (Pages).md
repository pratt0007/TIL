```
https://practice.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1
```
```cpp
class Solution 
{
    public:
    int sum(int start , int end , int arr []){
        int ans = 0;
        for(int i = start ; i<= end ;i++){
            ans += arr[i];
            
        }   
        return ans;
        
        
    }
    //Function to find minimum number of pages.
    int findPages(int A[], int N, int M) 
    {
        if(M>N) return -1; 
        if(M==1) return sum(0 , N-1 , A);
        if(N==1) return A[0];
        
        int res = INT_MAX;
        for(int i = 1 ; i<N ; i++){
            res = min(res , max(findPages(A , i , M-1) , sum(i , N-1 , A)));
        }
        if(res==0) return -1;
        return res;
        
        //code here
    }
};
```
```
Easy solution me prefix sum nikalte jao and then take min(ans , max(k , n-k)) iska ans jo ayega vo min book that can be alloted to a person hoga. Ye galt 
```
```
class Solution 
{
    public:
   
    //Function to find minimum number of pages.
    int findPages(int A[], int N, int M) 
    {
        if(M>N) return -1; 
        
        
        int total_sum = 0;
        for(int i = 0 ; i<N ; i++){
            total_sum += A[i];
        }
        
        int res = INT_MAX;
        int csum = 0;
        for(int i = 0 ; i< N-1 ; i++){
            csum += A[i];
            res = min(res , max(csum , (total_sum - csum)));
            
        }
        return res;
        
        //code here
    }
};
IS APPROCH SE SIRF 2 ME DIVIDE KAREGA - JO SABSE PEHLE DIMAG ME AYA OR BOHT GALT
```


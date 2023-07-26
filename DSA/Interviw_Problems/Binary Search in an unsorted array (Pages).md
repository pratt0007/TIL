```
https://practice.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1
```
```
https://leetcode.com/problems/minimized-maximum-of-products-distributed-to-any-store/description/
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

```cpp

class Solution 
{
    public:
    //Function to find minimum number of pages.
    
    bool is_possible(int A[],int mid, int N, int M)
    {
        int sum_pages = 0;
        int students=1;
        for(int i=0; i < N;i++ )
        {
            if(sum_pages + A[i]<= mid )
            {
              sum_pages += A[i];
            }
             
            else
            {
                students++;
                
                if(students > M || A[i] > mid)
                 {
                     return false;
                 }
                sum_pages = A[i];
            }
        }
        return true;
    }
    
    
    
    int findPages(int A[], int N, int M) 
    {
        //code here
       if(N<M)return -1;
        int low=0;
        int sum=0;
        
        for(int i=0;i<N;i++)
        {
            sum += A[i];
        }
        
        int high = sum;
        int ans = -1;
     
        int mid = low + (high - low)/2;
        
        while(low<=high)
        {
            if(is_possible(A, mid, N, M ))
            {
                ans = mid;
                high = mid - 1 ;
            }
            else {
                
                low = mid + 1;
            }
            
            mid = low + (high - low)/2;
        }
        
    return ans;    
        
    }
};
```
```
Using bianry search in an unsorted array in such a way that we get min pages alloted to a person,
```


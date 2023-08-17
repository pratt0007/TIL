# Merge Sort Algo
### This is a divide and merge algo where we divide the array into halves till the point only one elemenet is left and then we compare the adjacent elements and merge returning the array.
### There are 2 finction one is of merge sort which divides till the single element is present and then it compares to get in ascending order

```
class Solution {
public:
    void merge(int arr[], int l, int m, int r) {
        vector<int> temp;
        int left = l;
        int right = m + 1; // Corrected this to m + 1

        while (left <= m && right <= r) { // Corrected this condition
            if (arr[left] <= arr[right]) {
                temp.push_back(arr[left]);
                left++;
            } else {
                temp.push_back(arr[right]);
                right++;
            }
        }

        // Add the remaining elements from the left and right subarrays
        while (left <= m) {
            temp.push_back(arr[left]);
            left++;
        }
        while (right <= r) {
            temp.push_back(arr[right]);
            right++;
        }

        // Copy the merged elements back to the original array
        for (int i = l, j = 0; i <= r; i++, j++) {
            arr[i] = temp[j];
        }
    }

    void mergeSort(int arr[], int l, int r) {
        if (l < r) {
            int mid = l + (r - l) / 2;
            mergeSort(arr, l, mid);
            mergeSort(arr, mid + 1, r);
            merge(arr, l, mid, r);
        }
    }
};
```

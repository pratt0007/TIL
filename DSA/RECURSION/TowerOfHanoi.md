# Tower of Hanoi

```
 The idea is to use the helper node to reach the destination using recursion. Below is the pattern for this problem:

1.Shift ‘N-1’ disks from ‘A’ to ‘B’, using C.
2.Shift last disk from ‘A’ to ‘C’.
3.Shift ‘N-1’ disks from ‘B’ to ‘C’, using

We have also seen that for n disks, a total of  2n – 1 moves are required. 
```
## CODE
### Rec Sol
```cpp
class Solution{
    public:



int count = 0;
    long long toh(int N, int from, int to, int aux) {
        // Your code here
        
        if(N==0)
        {
            return count;
        }
        
    toh(N-1,from,aux,to);
    cout<<"move disk "<<N<<" from rod "<<from<<" to rod "<<to<<endl;
    count = count+1;
    toh(N-1,aux,to,from);
    
    }

};

```

### Iterative sol
```
https://www.geeksforgeeks.org/iterative-tower-of-hanoi/
1. Calculate the total number of moves required i.e. "pow(2, n)
   - 1" here n is number of disks.
2. If number of disks (i.e. n) is even then interchange destination 
   pole and auxiliary pole.
3. for i = 1 to total number of moves:
     if i%3 == 1:
    legal movement of top disk between source pole and 
        destination pole
     if i%3 == 2:
    legal movement top disk between source pole and 
        auxiliary pole    
     if i%3 == 0:
        legal movement top disk between auxiliary pole 
        and destination pole 
```
```cpp
// C++ Program for Iterative Tower of Hanoi using STL

#include <iostream>
#include <vector>
#include <stack>
using namespace std;

char rod[]={'S', 'A', 'D'};
vector<stack<int>> stacks(3); // 3 stacks for 3 rods

void moveDisk(int a, int b)
{
	if (stacks[b].empty() || (!stacks[a].empty() && stacks[a].top() < stacks[b].top()))
	{
		cout << "Move disk " << stacks[a].top() << " from rod " << rod[a] << " to rod " << rod[b] << "\n";
		stacks[b].push(stacks[a].top());
		stacks[a].pop();
	}
	else
		moveDisk(b, a);
}

void towerOfHanoi(int n)
{
	cout << "Tower of Hanoi for " << n << " disks:\n";

	int src = 0, aux = 1, dest = 2;
	for (int i = n; i > 0; i--)
		stacks[src].push(i);

	int totalMoves = (1 << n) - 1;
	if (n % 2 == 0)
		swap(aux, dest);

	for (int i = 1; i <= totalMoves; i++)
	{
		if (i % 3 == 0)
			moveDisk(aux, dest);
		else if (i % 3 == 1)
			moveDisk(src, dest);
		else
			moveDisk(src, aux);
	}
}

int main()
{
	int n = 3; // number of disks
	towerOfHanoi(n);
	return 0;
}
```


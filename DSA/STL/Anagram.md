f// CPP program to check whether two strings
// are anagram of each other
// using std :: is_permutation
#include <iostream>
#include <algorithm>

/*Driver Code*/
int main()
{
	std :: string A = "SILENT";
	std :: string B = "LISTEN";
	
	/*Checking if B is a permutation of A*/
	if ( is_permutation ( A.begin(), A.end(), B.begin() ) )
	{
		std :: cout << "Anagrams" ;
	}
	
	else
	{
		std :: cout << "Not Anagrams" ;
	}
	return 0;
}

To check Anagram using is_permutation

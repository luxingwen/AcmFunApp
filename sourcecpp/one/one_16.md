**语法:** void qp(int Array[],int begin,int end);
**注意:**当参与全排列的数字稍大的时候将会有很大的计算量
```cpp
#include <iostream>
using namespace std;
const int	MaxNum = 20;
static int	a[MaxNum];
void qp( int Array[], int begin, int end );


int main()
{
	int i;
	for ( i = 0; i < MaxNum; i++ )
		a[i] = i + 1;
	/* 初始化数组为:1,2,3.. */
	qp( a, 0, 10 );
	return(0);
}


void qp( int Array[], int begin, int end )
{
	int i;
	if ( begin >= end )
	{
		for ( i = 0; i < end; i++ )
			cout << Array[i] << "\t";
		cout << endl;
	}else for ( i = begin; i < end; i++ )
		{
			swap( a[begin], a[i] );
			qp( a, begin + 1, end );
			swap( a[begin], a[i] );
		}
}


/* stl里面的全排列生成函数next_permutation */
#include <iostream>
#include <algorithm>
using namespace std;

int main()
{
	int	i;
	int	A[] = { 0, 1, 2, 3 };
	while ( next_permutation( A, A + 4 ) == true ) /* prev_permutation(A, A+4); */

	{
		for ( i = 0; i < 4; i++ )
			cout << A[i] << "\t";
		cout << endl;
	}
}



```
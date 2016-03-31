**语法：**result=weekday(int N,int M,int d)
**参数：**
-      N,M,d：年月日，例如：2003,11,4


**返回值：**0：星期天，1星期一……
**注意：** 需要math.h，适用于1582年10月15日之后, 因为罗马教皇格里高利十三世在这一天启用新历法.
**源程序：**
```cpp
int weekday( int N, int M, int d )
{
	int m, n, c, y, w;
	m = (M - 2) % 12;
	if ( M >= 3 )
		n = N;
	else n = N - 1;
	c	= n / 100;
	y	= n % 100;
	w	= (int) (d + floor( 13 * m / 5 ) + y + floor( y / 4 ) + floor( c / 4 ) - 2 * c) % 7;
	while ( w < 0 )
		w += 7;
	return(w);
}
```
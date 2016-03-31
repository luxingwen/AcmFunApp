**语法：**result=P(long n,long m);  result=long C(long n,long m);
**参数：**
-      m：排列组合的上系数
-      n：排列组合的下系数

**返回值：**排列组合数
**注意：** 符合数学规则：m<＝n
**源程序：**
```cpp
long P( long n, long m )
{
	long p = 1;
	while ( m != 0 )
	{
		p *= n; n--; m--;
	}
	return(p);
}


long C( long n, long m )
{
	long i, c = 1;
	i = m;
	while ( i != 0 )
	{
		c *= n; n--; i--;
	}
	while ( m != 0 )
	{
		c /= m; m--;
	}
	return(c);
}



```
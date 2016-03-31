**语法：**result=integral(double a,double b);
**参数：**
-  a：积分上限
-      b：积分下限
-      function f：积分函数


**返回值：**f在（a,b）之间的积分值
**注意：** function f(x)需要自行修改，程序中用的是sina(x)/x，需要 math.h，默认精度要求是1e-5
**源程序：**
```cpp
double f( double x )
{
	return(sin( x ) / x); /* 在这里插入被积函数 */
}


double integral( double a, double b )
{
	double	h	= b - a;
	double	t1	= (1 + f( b ) ) * h / 2.0;
	int	k	= 1;
	double	r1, r2, s1, s2, c1, c2, t2;
loop:
	double s = 0.0;
	double x = a + h / 2.0;
	while ( x < b )
	{
		s	+= f( x );
		x	+= h;
	}
	t2	= (t1 + h * s) / 2.0;
	s2	= t2 + (t2 - t1) / 3.0;
	if ( k == 1 )
	{
		k++; h /= 2.0; t1 = t2; s1 = s2;
		goto loop;
	}
	c2 = s2 + (s2 - s1) / 15.0;
	if ( k == 2 )
	{
		c1	= c2; k++; h /= 2.0;
		t1	= t2; s1 = s2;
		goto loop;
	}
	r2 = c2 + (c2 - c1) / 63.0;
	if ( k == 3 )
	{
		r1	= r2; c1 = c2; k++;
		h	/= 2.0;
		t1	= t2; s1 = s2;
		goto loop;
	}
	while ( fabs( 1 - r1 / r2 ) > 1e-5 )
	{
		r1	= r2; c1 = c2; k++;
		h	/= 2.0;
		t1	= t2; s1 = s2;
		goto loop;
	}
	return(r2);
}


 
```


**语法：**result=js(int s[][],int n)
**参数：**
-      s[][]：行列式存储数组
-      n：行列式维数，递归用


**返回值：**行列式值
**注意：** 函数中常数N为行列式维度，需自行定义
**源程序：**
```cpp
int js( s, n )
int s[][N], n;
{
	int	z, j, k, r, total = 0;
	int	b[N][N]; /*b[N][N]用于存放，在矩阵s[N][N]中元素s[0]的余子式*/
	if ( n > 2 )
	{
		for ( z = 0; z < n; z++ )
		{
			for ( j = 0; j < n - 1; j++ )
				for ( k = 0; k < n - 1; k++ )
					if ( k >= z )
						b[j][k] = s[j + 1][k + 1];
					else
						b[j][k] = s[j + 1][k];
			if ( z % 2 == 0 )
				r = s[0][z] * js( b, n - 1 );  /*递归调用*/
			else r = (-1) * s[0][z] * js( b, n - 1 );
			total = total + r;
		}
	}else if ( n == 2 )
		total = s[0][0] * s[1][1] - s[0][1] * s[1][0];
	return(total);
}

```
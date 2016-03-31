```cpp
#include <stdio.h>
#include <string.h>
bool	g[201][201];                    /* 为边之间的关系,如g[0][1]==true表示为左边0点可与右边1点相连. */
int	n, m, ans;                      /* n左边的点,m右边的点,ans为最大匹配的边数. */
bool	b[201];                         /* b[i]表示该点是否有左边的点连上 */
int	link[201];
bool init()
{
	int _x, _y;
	memset( g, 0, sizeof(g) );      /* 对二维数组也可以这样初始化! */
	memset( link, 0, sizeof(link) );
	ans = 0;
	if ( scanf( "%d%d", &n, &m ) == EOF )
		return(false);
	for ( int i = 1; i <= n; i++ )  /* n左边的点,m右边的点 */
	{
		scanf( "%d", &_x );
		for ( int j = 0; j < _x; j++ )
		{
			scanf( "%d", &_y );
			g[i][_y] = true;
		}
	}
	return(true);
}


bool find( int a )
{
	for ( int i = 1; i <= m; i++ )
	{
		if ( g[a][i] == true && !b[i] )
		{
			b[i] = true;
			if ( link[i] == 0 || find( link[i] ) )
			{
				link[i] = a;
				return(true);
			}
		}
	}
	return(false);
}


int main()
{
	while ( init() )
	{
		for ( int i = 1; i <= n; i++ )
		{
			memset( b, 0, sizeof(b) ); /*  */
			if ( find( i ) )
				ans++;
		}
		printf( "%d\n", ans );
	}
}



```
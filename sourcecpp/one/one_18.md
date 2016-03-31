```cpp
#include <cstdio>
#include <queue>
#include <algorithm>
using namespace std;
const int	N	= 301;
const int	INF	= 10000;

class Graph
{
private:
	bool		xckd[N], yckd[N];
	int		n, edge[N][N], xmate[N], ymate[N];
	int		lx[N], ly[N], slack[N], prev[N];
	queue<int>	Q;
	bool bfs();


	void agument( int );


public:
	bool make();


	int KMMatch();
};
bool Graph::make()
{
	int i, j;
	while ( scanf( "%d", &n ) != EOF )
	{
		for ( i = 0; i < n; i++ )
		{
			for ( j = 0; j < n; j++ )
			{
				scanf( "%d", &edge[i][j] );
			}
		}
		return(true);
	}
	return(false);
}


bool Graph::bfs()
{
	while ( !Q.empty() )
	{
		int p = Q.front(), u = p >> 1; Q.pop();
		if ( p & 1 )
		{
			if ( ymate[u] == -1 )
			{
				agument( u ); return(true);
			}else                                                { xckd[ymate[u]] = true; Q.push( ymate[u] << 1 ); }
		} else {
			for ( int i = 0; i < n; i++ )
				if ( yckd[i] )
					continue;
				else if ( lx[u] + ly[i] != edge[u][i] )
				{
					int ex = lx[u] + ly[i] - edge[u][i];
					if ( slack[i] > ex )
					{
						slack[i] = ex; prev[i] = u;
					}
				} else {
					yckd[i] = true; prev[i] = u;
					Q.push( (i << 1) | 1 );
				}
		}
	}
	return(false);
}


void Graph::agument( int u )
{
	while ( u != -1 )
	{
		int pv = xmate[prev[u]];
		ymate[u]	= prev[u]; xmate[prev[u]] = u;
		u		= pv;
	}
}


int Graph::KMMatch()
{
	int i, j;
	memset( ly, 0, sizeof(ly) );
	for ( i = 0; i < n; i++ )
	{
		lx[i] = -INF;
		for ( j = 0; j < n; j++ )
			lx[i] = lx[i] > edge[i][j] ? lx[i] : edge[i][j];
	}
	memset( xmate, -1, sizeof(xmate) ); memset( ymate, -1, sizeof(ymate) );
	bool agu = true;
	for ( int mn = 0; mn < n; mn++ )
	{
		if ( agu )
		{
			memset( xckd, false, sizeof(xckd) );
			memset( yckd, false, sizeof(yckd) );
			for ( i = 0; i < n; i++ )
				slack[i] = INF;
			while ( !Q.empty() )
				Q.pop();
			xckd[mn] = true; Q.push( mn << 1 );
		}
		if ( bfs() )
		{
			agu = true; continue;
		}
		int ex = INF; mn--; agu = false;
		for ( i = 0; i < n; i++ )
			if ( !yckd[i] )
				ex = ex < slack[i] ? ex : slack[i];
		for ( i = 0; i < n; i++ )
		{
			if ( xckd[i] )
				lx[i] -= ex;
			if ( yckd[i] )
				ly[i] += ex;
			slack[i] -= ex;
		}
		for ( int i = 0; i < n; i++ )
			if ( !yckd[i] && slack[i] == 0 )
			{
				yckd[i] = true; Q.push( (i << 1) | 1 );
			}
	}
	int cost = 0;
	for ( i = 0; i < n; i++ )
		cost += edge[i][xmate[i]];
	return(cost);
}


int main()
{
	Graph g;
	while ( g.make() )
	{
		printf( "%d\n", g.KMMatch() );
	}
	return(0);
}



```
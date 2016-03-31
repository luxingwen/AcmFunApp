**语法：**result=lcs_len(char *a, char *b);
**参数：**
-      a,b[]：根据a,b生成最大公共子串


**返回值：**最大公共子串的长度
**注意： **
-       需要 string.h
-       M、N是a,b数组的最大可能长度
-      如果不需要生成公共子串，c[M][N]不可设置为全局变量


**源程序：**
```cpp
      #define M 20
      #define N 20
      int c[M][N]; 
      int lcs_len(char *a, char *b)
      {
      int m=strlen(a),n=strlen(b),i,j;
      for(i=0;i<=m;i++) c[i][0]=0;
      for(j=0;j<=n;j++) c[0][j]=0;
      for(i=1;i<=m;i++)
          for(j=1;j<=n;j++)
          {
          if(a[i-1]==b[j-1])
              c[i][j]=c[i-1][j-1]+1;
          else if(c[i-1][j]>c[i][j-1])
              c[i][j]=c[i-1][j];
          else
              c[i][j]=c[i][j-1];
          }
      return c[m][n];
      }
```
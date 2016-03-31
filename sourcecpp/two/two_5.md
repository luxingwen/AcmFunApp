**语法：**result=build_lcs(char s[], char *a, int blen, int clen);

**参数：**
-      *a：生成公共子串的字符串a,b中的a
-     s[]：接受返回结果的字符串数组
-      blen：生成公共子串的字符串a,b中的b的长度
-      clen：最大公共子串的长度，通过lcs_len函数求得


**返回值：**最大公共子串的长度
**注意：** 
-       需要 string.h
-       需要lcs_len函数求clen并且生成c[M][N]
-       可通过result=build_lcs返回指针或者通过build_lcs(s,a,blen,clen)，用s接受结果


**源程序：**

```cpp
  char *build_lcs(char s[], char *a, int blen, int clen)
      {
      int k=clen,alen=strlen(a),i,j;
      s[k]='\0';
      i=alen,j=blen;
      while(k>0)
          {
          if(c[i][j]==c[i-1][j])
          i--;
          else if(c[i][j]==c[i][j-1])
          j--;
          else
              {
              s[--k]=a[i-1];
              i--;j--;
              }
          }
      return s;
      } 
```
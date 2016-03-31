**语法：**mult(char c[],char t[],int m);
**参数：**c[]：被乘数，用字符串表示，位数不限,t[]：结果，用字符串表示,m：乘数，限定10以内
**返回值：**null
**注意：** 需要 string.h
**源程序：** 
```cpp
  void mult(char c[],char t[],int m)
      {
          int i,l,k,flag,add=0;
          char s[100];
          l=strlen(c);
          for (i=0;i<l;i++)
              s[l-i-1]=c[i]-'0'; 
          for (i=0;i<l;i++)
               {
                  k=s[i]*m+add;
                  if (k>=10)
                  {
                     s[i]=k%10;add=k/10;flag=1;
                  } else 
                   {
                   s[i]=k;
                   flag=0;
                   add=0;
                   }
                 }
          if (flag) 
              {
                 l=i+1;
                 s[i]=add;
              }
          else l=i;
          for (i=0;i<l;i++)
              t[l-1-i]=s[i]+'0';
          t[l]='\0';
      }
```
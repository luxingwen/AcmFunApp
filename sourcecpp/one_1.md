**语法：**int result=factorial(int n);
**参数：**n：n 的阶乘
**返回值：**阶乘结果的位数
**注意：** 本程序直接输出n!的结果，需要返回结果请保留long a[]
**需要** math.h
**源程序：**
```cpp
int factorial(int n)
   {
      long a[10000];
      int i,j,l,c,m=0,w; 
      a[0]=1; 
      for(i=1;i<=n;i++)
          { 
          c=0; 
          for(j=0;j<=m;j++)
              { 
                 a[j]=a[j]*i+c; 
                 c=a[j]/10000; 
                 a[j]=a[j]%10000; 
              } 
          if(c>0) {m++;a[m]=c;} 
      } 

      w=m*4+log10(a[m])+1;
      printf("\n%ld",a[m]); 
      for(i=m-1;i>=0;i--) printf("%4.4ld",a[i]);
      return w;
     } 
```
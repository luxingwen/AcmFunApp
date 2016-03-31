**语法：**cstr(int k,char o[]);
**参数：**
-      k：转换的数字
-     o[]：存储转换结果的字符串


**返回值：**null
**注意：** 
-       需要 math.h


**源程序： **
```cpp
  void cstr(int k,char o[])
      {
          int len,i,t;
          len=log10(k)+1;
          for (i=len;i>0;i--)
              {
              t=k%10;
              k-=t;k/=10;
              o[i-1]='0'+t;
              }
          o[len]='\0';
      }
```
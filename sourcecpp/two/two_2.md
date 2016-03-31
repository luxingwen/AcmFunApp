**语法：**result=strfind(char str[],char key[]);
**参数：**
-      str[]：在此源字符串进行查找操作
-      key[]：被查找的字符串，不能为空串


**返回值：**如果查找成功，返回key在str中第一次出现的位置，否则返回-1
**注意：** 需要 string.h
**源程序：**
```cpp
 int strfind(char str[],char key[])
      {
          int l1,l2,i,j,flag;
          l1=strlen(str);
          l2=strlen(key);
          for (i=0;i<=l1-l2;i++)
              {
              flag=1;
              for (j=0;j<l2;j++)
                  if (str[i+j]!=key[j]) {flag=0;break;}
              if (flag) return i;
              }
          return -1;
      } 
```
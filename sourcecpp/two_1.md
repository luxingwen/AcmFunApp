**语法：**replace(char str[],char key[],char swap[]);
**参数：**
-      str[]：在此源字符串进行替换操作
-      key[]：被替换的字符串，不能为空串
-      swap[]：替换的字符串，可以为空串，为空串表示在源字符中删除key[]


**返回值：**null
**注意：** 
-       默认str[]长度小于1000，如否，重新设定设定tmp大小
-       需要 string.h


**源程序：**
```cpp
  void replace(char str[],char key[],char swap[])
      {
          int l1,l2,l3,i,j,flag;
          char tmp[1000];
          l1=strlen(str);
          l2=strlen(key);
          l3=strlen(swap);
          for (i=0;i<=l1-l2;i++)
              {
              flag=1;
              for (j=0;j<l2;j++)
                  if (str[i+j]!=key[j]) {flag=0;break;}
              if (flag)
                  {
                  strcpy(tmp,str);
                  strcpy(&tmp[i],swap);
                  strcpy(&tmp[i+l3],&str[i+l2]);
                  strcpy(str,tmp);
                  i+=l3-1;
                  l1=strlen(str);
                  }
              }
      }

```
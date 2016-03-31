**语法：**resulet=hcf(int a,int b)、result=lcd(int a,int b)
**参数：**
- a：int a，求最大公约数或最小公倍数
-  b：int b，求最大公约数或最小公倍数

**返回值：**返回最大公约数（hcf）或最小公倍数（lcd）
**注意：** lcd 需要连同 hcf 使用
**源程序：**
```cpp
     int hcf(int a,int b)
      {
          int r=0;
          while(b!=0)
              {
                r=a%b;
                a=b;
                b=r;
              }
          return(a);
      } 
      lcd(int u,int v,int h)
      {
          return(u*v/h);
      }
```

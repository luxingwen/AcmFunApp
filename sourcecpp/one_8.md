**语法：**m_of_n(int m, int n1, int m1, int* a, int head)
**参数：**
-      m：组合数C的上参数
-      n1：组合数C的下参数
-      m1：组合数C的上参数，递归之用
-      *a：1～n的整数序列数组
-      head：头指针


**返回值：**null
**注意：**
-      *a需要自行产生
      初始调用时，m=m1、head=0
      调用例子：求C(m,n)序列：m_of_n(m,n,m,a,0);
            
**源程序：**
```cpp
       void m_of_n(int m, int n1, int m1, int* a, int head) 
      { 
          int i,t; 
          if(m1<0 || m1>n1) return; 
          if(m1==n1) 
              { 
              return; 
              } 
          m_of_n(m,n1-1,m1,a,head); // 递归调用 
          t=a[head];a[head]=a[n1-1+head];a[n1-1+head]=t;
          m_of_n(m,n1-1,m1-1,a,head+1); // 再次递归调用 
          t=a[head];a[head]=a[n1-1+head];a[n1-1+head]=t;
      } 
```
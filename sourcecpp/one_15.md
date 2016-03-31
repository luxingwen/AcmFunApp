**语法:** void gen()
**预置:**Const int Max;
**注意:** (Max一般不能超过22,否则要用高精度计算)**int inta[Max][Max];**
**结果:**inta为杨辉三角序列.inta[1][1]=1;inta[2][1]=1;inta[2][2]=1…
```cpp
void gen()
{
         int i ,j;
         for( i =1 ;i <= Max ;i++)
         {
                 inta[i][1] = 1 ;
                 inta[i][i] = 1 ;
         }
         inta[2][2] = 1   ;
         for( i = 3 ; i<=Max ;i++)
         {
                 for(j =2 ;j<i ; j++ )
                 {
                         inta[i][j] = inta[i-1][j-1] + inta[i-1][j] ;
                 }
         }
}
```
**前十行:**
```cpp
1
1 1
1 2 1
1 3 3 1
1 4 6 4 1
1 5 10 10 5 1
1 6 15 20 15 6 1
1 7 21 35 35 21 7 1
1 8 28 56 70 56 28 8 1
1 9 36 84 126 126 84 36 9 1
```
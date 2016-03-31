**今天老师讲了进制的转换，我用数组做了一个。** 
**语法：**conversion(char a[],char b[],int n,int m);
**参数：**
-      a[]：转换前的数字
-      b[]：转换后的数字
-      n：原进制数
-      m：需要转换到的进制数


**返回值：**null
**注意：** 高于9的位数用大写'A'～'Z'表示，2～16位进制通过验证
**源程序：**
```cpp
#include<iostream>
#include<cstring>
#include<cmath>
using namespace std;
void conversation(char a[],char b[],int n,int m)
{
    int num=0,i,j,t;
	char c;
    int p=strlen(a)-1;
	for(i=0;a[i]!='\0';i++)
	{
	    if(a[i]>='0'&&a[i]<='9')
		{
		   t=a[i]-'0';
		}
		else
		{
		    t=a[i]-'A'+10; 
		}
	//	num=num*n+t;//这个和num+=t*pow(n,p);的效果是一样的，开始我用的是这个。
		num+=t*pow(n,p);//为了方便你们理解，我还是换成了这个
		--p;
	}
    //	cout<<num<<endl;
	i=0;
	while(1)
	{
	 if(num==0)break;
	  t=num%m;
	  if(t<=9)
	  b[i]=t+'0';
	  else
	  b[i]=t+'A'-10; 
	  num/=m;
	  i++;
	}
	for(j=i-1;j>=0;j--)
		cout<<b[j];
	for(j=0;j<=i/2;j++)
	{
	   c=b[j];
	   b[j]=b[i-j];
	   b[i-j]=c;
	}
	b[i+1]='\0';
		cout<<endl;

}

int main()
{
	char a[100],b[100];
	int n,m;
   while(cin>>a>>n>>m)
   {
	conversation(a,b,n,m);
	for(int i=1;b[i]!='\0';i++)
		cout<<b[i];
	cout<<endl;
   }
	return 0;
}
```

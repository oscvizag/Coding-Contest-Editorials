Question:-

![Question](https://raw.githubusercontent.com/oscvizag/Coding-Contest-Editorials/master/cOdeSpeC/Yummy%20and%20the%20Chocolate%20Factory/yummy%20and%20the%20chocolate%20factory.png)



## explanation


The idea is to traverse every array element and find the highest bars on left and right sides. Take the smaller of two heights. The difference between the smaller height and height of the current element is the amount of water that can be stored in this array element.
Algorithm:
Traverse the array from start to end.
For every element, traverse the array from start to that index and find the maximum height (a) and traverse the array from the current index to end and find the maximum height (b).
The amount of water that will be stored in this column is min(a,b) – array[i], add this value to total amount of chocolate stored
Print the total amount of chocolate stored.
Implementation:

```
#include <bits/stdc++.h>
using namespace std;
#define ll long long int
#define mod 1000000007
#define fast_iop ios_base::sync_with_stdio(false);cin.tie(NULL);cout.tie(NULL);
#define endl "\n"
#define test_cases ll t cin>>t while(t--)
int main()
{
fast_iop
test_cases
{
ll n,su=0;
cin>>n;
ll a[n],maxx[n],maxx1[n],mani=INT_MIN;
for(ll i=0;i<n;i++)
{
cin>>a[i];
mani=max(a[i],mani);
maxx[i]=mani;
}
mani=INT_MIN;
for(ll j=n-1;j>=0;j--)
{
mani=max(a[j],mani);
maxx1[j]=mani;
}
for(ll i=0;i<n;i++)
{
ll minn=min(maxx[i],maxx1[i]);
su+=minn-a[i];
}
cout<<su<<"\n";
}
return 0;
}

```

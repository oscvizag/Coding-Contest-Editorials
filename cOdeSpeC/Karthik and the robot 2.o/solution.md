## Question
![Question](https://raw.githubusercontent.com/oscvizag/Coding-Contest-Editorials/master/cOdeSpeC/Karthik%20and%20the%20robot%202.o/Karthik%20and%20the%20robot%202.o.png)
If we want to pick an element at the i-th position in the list (i.e., A[i]), we need to travel either (1 + i) unit distance (if we start from the left end), or (N - i) unit distance (if we start from the right end). Hence, the shortest distance required to pick the i-th element is min(1 + i, N - i). We can denote this value by Si.

If we want to pick an element whose value is x, then we need to find all occurrences of x in the array A, and take the minimum of S values of the corresponding indices. For example, if we want to find the shortest distance to pick an element with value 10, and the element 10 occurs at three times in array A (A[3], A[5], and A[9]), then the shortest distance to pick 10 would be min(S3, S5, S9).

Next, we discuss how to create these values using a single pass, i.e., create an array B, such that B[x] is the shortest distance needed to pick an element with value x. We initialize the array B with infinite (any number greater than N will suffice), and update it as we scan through the array A.
```
B = {INF};
for (int i = 0; i < N; ++i) {
    int x = A[i];
    int d = min(1 + i, N - i);
    
    B[x] = min(B[x], d);
}
```
Now, we have the shortest distance of each element. If one of the picked element is x, then the other picked element must be (k - x), and hence the time needed is max(B[x], B[k - x]) as both robots start at the same time. We need to go through all possible values of x, and take the minimum of max(B[x], B[k - x]). If the minimum value turns out to be INF, then we have no solution, otherwise this minimum value is the desired answer. Since the picked element must be distinct, one should ignore the case when x = k - x.

```
ans = INF;
for (int i = 0; i < N; ++i) {
    int x = A[i];
    if (x != k - x) {
        ans = min(ans, max(B[x], B[k - x]));
    }
}
```
# Solution
```
#include<bits/stdc++.h>
using namespace std;
#define ll long long int
#define IOS                           \
    ios_base::sync_with_stdio(false); \
    cin.tie(NULL);                    \
    cout.tie(NULL);
#define endl "\n"
#define loop1(a,b) for(ll i=a;i<b;i++)
#define loop2(a,b) for(ll j=a;j<b;j++)
#define test \
        ll t; \
        cin>>t; \
        while(t--)
#define present(c,x) (c.find(x)!=c.end())
    
int main()
{
   ll n,k;
   cin>>n>>k;
   vector<ll>vec(n);
   for(int i=0;i<n;i++)
   cin>>vec[i];
   set<ll>st;
   ll x=n-1;
   ll ans=-1;
   for(int i=0;i<=n/2;i++)
   {
        st.insert(vec[i]);
        st.insert(vec[x]);
            
           if(st.find((k-vec[i]))!=st.end() && (vec[i]!=(k-vec[i])))
           {
               ans=i+1;
               break;
           }
           if(st.find((k-vec[x]))!=st.end() && (vec[x]!=(k-vec[x])))
           {
               ans=n-x;
               break;
           }


       
       x--;
   }
   
   cout<<ans<<endl;
}
```

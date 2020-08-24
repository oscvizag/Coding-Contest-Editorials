##question
[Question]
This compleate solution is a greedy and bruteforce solution 
the solution goes like this
1. initlise the count to zero after scanning or taking the input
```
int count=0
```
2. run a while loop until b>=1 and c>=2
3. inside the loop for each one loop increase the count by 3 decrease the count of B by 1 and C by 2
```
while(b>=1 && c>=2)
      {
          count+=3;
                                    
             b-=1;
              c-=2;
      }
```      
4. run another while loop until a>=1 and b>=2
5. inside the loop for each one loop increase the count by 3 decrease the count of A by 1 and B by 2
```
 while(a>=1 && b>=2)
      {
           count+=3;
                                    
             a-=1;
          b-=2;
       }
```       
6. finally print count.
Bingo!
here if u see carefully your doing the second operation first and first opertion second as mentiond int the 
Question above
#solution
```
#include <bits/stdc++.h>
    using namespace std;
    ################################
    #    M.A.Shanawaz              #
    #    Vignan Instute Of         #
    #    Informaton And Tech       #
    #     18L31A05E0               #
    ################################
    int main()
    {
    int t;
    cin>>t;
    while(t--)
    {
    int a,b,c;
   cin>>a>>b>>c;
    int count=0;
                            
     while(b>=1 && c>=2)
      {
          count+=3;
                                    
              b-=1;
              c-=2;
      }
      while(a>=1 && b>=2)
      {
           count+=3;
                                    
             a-=1;
             b-=2;
       }
       cout<<count<<endl;   
    }
    }
```    
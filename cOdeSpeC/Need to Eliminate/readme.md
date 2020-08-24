## Need to Eliminate

![question](https://github.com/oscvizag/Coding-Contest-Editorials/blob/master/cOdeSpeC/Need%20to%20Eliminate/nte1.PNG)

## hint

As far as you read the question you can understand it and the solution for the problem is to find the maximum length of substring of 1s and so you can report it to the command center.

## code

```
#include<bits/stdc++.h>

using namespace std;

typedef long long ll;

int lis(string s)

{
  vector < ll > lis(s.length(), 1);

  if (s[0] == '1') {

    lis[0] = 1;

  }

  for (int i = 1; i < s.length(); i++)

  {

    if (s[i] == '1' && s[i - 1] == '1') {

      lis[i] = lis[i] + lis[i - 1];

    }

  }

  return *max_element(lis.begin(), lis.end());

}

int main() {

  // clock_t time_req;

  // time_req = clock();

  // freopen("input4.txt","r",stdin);

  // freopen("output5.txt","w",stdout);

  ll t;

  cin >> t;

  while (t--) {

    string s;

    cin >> s;

    cout << lis(s) << endl;

  }

  // time_req = clock()- time_req;

  //  cout << (float)time_req/CLOCKS_PER_SEC << " seconds" << endl;

  return 0;

}
```

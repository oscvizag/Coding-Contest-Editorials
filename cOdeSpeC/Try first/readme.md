Question:-

![Question](cOdeSpeC/Try first/try first.PNG)

First download the given [zip](https://drive.google.com/file/d/1467D9kGPJmmUrs3Riv_TbAtssyBUS-IU/view?usp=sharing)

## Merging multiple files

Then extract them into a folder.Open CMD in that folder and run the following code

```
copy * final
```

## Reading the file in code

So the above code merges all the following text files in that folder.
then open your local c++ text editor.

```
#include <bits/stdc++.h>
#include <boost/algorithm/string.hpp>
using namespace std;
int main() {
return 0;
}

```

first read the file final using the following code

```
freopen("final","r",stdin);
```

the above code will provide a stream input from the file final.
now you can take input with cin.

## My way to breaking down the problem

```
#include <bits/stdc++.h>
#include <boost/algorithm/string.hpp>
using namespace std;
int main() {
freopen("final","r",stdin); 		//reading the input
set<long long>s; 			//made a set to store the numbers
string input;   			// initilized a string
getline(cin,input);			//using getline to read the complete line
cout<<"done taking i/p"<<endl;          //debugging feature :smile:
vector<string> result;                  //I have the string now I have to split
boost::split(result, input, boost::is_any_of(" "));    //it where ever I get a space
cout<<result.size()<<"done spliting i/p"<<endl;        //debugging feature :smile:

//the following loop now converts the vector of strings into long long int and inserts into set

for(int i=0;i<result.size();i++){
    stringstream geek(result[i]);
    long long  x = 0;
    geek >> x;
   s.insert(x);
}
//debugging feature
cout<<"done converting i/p"<<endl;
//just adding the sum using foreach loop
long long sum=0;
for(auto x:s){
    sum+=x;
}
//finding the distinct digits
map<int,int>dis;
long long tmp=sum;
while(tmp>0){
dis[tmp%10]++;
tmp/=10;
}
cout<<dis.size()<<" ";
//printing the requred sum
cout<<sum<<"\n";
}

```

the output we get is

```
8 4602454836826033439
```

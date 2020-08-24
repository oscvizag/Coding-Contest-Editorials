Question:-

![Question](https://github.com/oscvizag/Coding-Contest-Editorials/blob/master/cOdeSpeC/Try%20first/try%20first.PNG)

First download the given [zip](https://drive.google.com/file/d/1467D9kGPJmmUrs3Riv_TbAtssyBUS-IU/view?usp=sharing)

# Approach in CPP

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
freopen("final","r",stdin); 		                                //reading the input
set<long long>s; 			                                        //made a set to store the numbers
string input;   			                                        // initilized a string
getline(cin,input);			                                        //using getline to read the complete line
cout<<"done taking i/p"<<endl;                                      //debugging feature :smile:
vector<string> result;                                              //I have the string now I have to split
boost::split(result, input, boost::is_any_of(" "));                 //it where ever I get a space
cout<<result.size()<<"done spliting i/p"<<endl;                     //debugging feature

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

![analytics](https://github.com/oscvizag/Coding-Contest-Editorials/blob/master/cOdeSpeC/Try%20first/snip.PNG)

# Approach in Python

It is similar to the CPP approach. The only difference is language syntax.
Incase of file manipulations and file accessing situations, Python is very cool to use.
Unlike CPP its not necessary to divide our code into multiple parts.
The question is not based on logic. All we need to know is, we need to open the files, take the input and then give the sum of elements (only once).
Our approach is
File open karo, File read karo, File close karo

```
overallFileInputs = []
for i in range(97, 97+6):
    with open(chr(i), "r") as f:                                #to read the file a,b,c,d,e,f
        fileInput = f.readline().split()                        #to read the input from file
        fileInput = list(set(fileInput))                        #by using set() we remove duplicates
        overallFileInputs.extend(fileInput)                     #extend is used to add the list to another list
        overallFileInputs = list(set(overallFileInputs))        #again removing the duplicates
overallFileInputs = list(map(int, overallFileInputs))           #converting all the elements in list from string to integer
print(sum(overallFileInputs))                                   #gives sum of elements
```

As said, its all about syntaxes. :smiley:

### Happy Coding

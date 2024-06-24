## C++ Program to split a string by a delimiter 

```C++

#include <iostream> 
#include <sstream> 
#include <vector> 

using namespace std; 

int main() 
{ 
	// Input string 
	string inputString = "geeks,for,geeks"; 

	// Create a stringstream object with the input string 
	stringstream ss(inputString); 

	// Tokenize the input string by comma delimiter 
	string token; 
	vector<string> tokens; 
	char delimiter = ','; 

	while (getline(ss, token, delimiter)) { 
		tokens.push_back(token); 
	} 

	// Output the string after splitting 
	cout << "String after splitting: " << endl; 
	for (const auto& part : tokens) { 
		cout << part << endl; 
	} 

	return 0; 
}


```

## Java

 

```Java

String str= "Welcome,to,the,word,of,technology"; 

String[] tokens = str.split(",");  

// Welcome  
// to   
// the   
// word  
// of   
// technology  


```


## JavaScript

```JavaScript

let text = "How are you doing today?";
const myArray = text.split(" ");

```

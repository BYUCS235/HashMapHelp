# HashMapHelp
I hope that this tutorial will help you with the hashmap lab.

First, lets instrument the main function so that it will time the hashmap version and the vectormap version of the lab.
```c++
...
#include <ctime>
#include <stdlib.h>
#include <math.h>
...
  clock_t oldtime, newtime; // To time the functions
  double seconds;
  oldtime = clock();
  ...
  newtime = clock();
  seconds = (double)(newtime-oldtime)/CLOCKS_PER_SEC;
  cout << "Vector Map took "<<seconds<<endl;
```
And lets integrate this into the working 
[driver function](https://github.com/BYUCS235/HashMapHelp/blob/master/hashmap.cpp)

Now, lets take the code we discussed for 
[operator overloading](https://github.com/BYUCS235/OperatorOverloading/blob/master/map.cpp)
and add the hash function into HashMap.h

Instead of using index zero every time
```c++
	int hashval = 0; // Compute the hash value for this name, for now assume it is 0
  node *ptr = context_array[hashval];
```
Call the 
[hash function](https://github.com/BYUCS235/HashDetails/blob/master/hash.cpp)
we discussed before.
```c++
	int hashval = hashme(name, CONSIZE); // Compute the hash value for this name, for now assume it is 0
	node *ptr = context_array[hashval];
```
Add the code for the 
[VectorMap](https://github.com/BYUCS235/OperatorOverloading/blob/master/VectorMap.h) 
that we developed earlier into VectorMap.h and the code should compile.

Now lets compare times on 1Nephi.txt and poe.txt (poe.txt has more words, so n is larger).

Try changing the number of words that you create so that the test takes enough time to see a difference.
```c++
for (int i = 0; i < 10000; i++) {
    int ind = rand() % wordmap[state].size();
```

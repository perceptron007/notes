# Competitive Programming Warmup


### Built in Methods worth remembering 

```c++

int a = 7;
int b = 4;

int minimum = min(a,b);
int maximum = max(a,b);

int swapped = swap(a,b); // a = 4, b = 7
```

#### auto keyword
Auto is a nice keyword when you are dealing with complex data-structure for example

```c
vector<pair<pair<int, int> pair<int,int>>> v;

for (pair<pair<int, int> pair<int, int>> it : v)
    
// The above statement could be written as 

for (auto it : v)

```
#### use of Pair instead of struct or class

We can use pair instead of defining struct for simple use cases with 2 data types
For example 

```c
struct Point {
    int x;
    int y;
}
```

This can be simplified as **pair**

> Ways to initialize a pair

```c
pair<int, int> coord = {x, y};
pair<int, int> coord = make_pair(x, y);

// Accessing members of pairs with the help of first and second keyword
int x = coord.first;
int y = coord.second;
```

You can also compose pair inside a pair.
The first and second element of a pair could be anything and even could both be pairs too. 

#### Input and Output in C++ 

Taking input in C style _scanf and printf_
```c
scanf("%d", &x); // read int
scanf("%lld", &x); // read long long int
scanf("%s", &s); // read string
scanf("%f", &d); // read float
```

We can similarly print with printf using the above syntax also. 

Using C++ **IOstream**

```
cin>>x; // read x
cout<<x; // print x

// Putting this on top of your file will make the input and output relatively fast
ios_base::sync_with_stdio(false);
```

You will most probably have issues if you take large number of inputs using C++ _ioStream_ but putting the statement described above will make the code relatively faster but will introduce some unexpected issues if you use cin and scanf (C++ and C style code) at same time in your code.

#### Complexity Analysis

**Logarathmic Runtime**
```c
for (int i = 1; i <= N; i *= 2)
 	x++;

// The complexity of such loop in O(log (n))
```
**Harmonic Series**
```c
for (int i = 1; i <= N; i++)    
    for (int j = i; j <= N; j += i)        
        x++;

// The complexity of such loop is O(N(log (n)))
```

**Non Trivial Runtime**
```c
for (int i = 1; i <= N; i *= 2)
    for (int j = 1; j <= i; j++)
        x++;

```
The complexity of the above loop can be calculated as follows
- The complexity of outer loop as we know can be calculated easily which would turn out to be O(n log(n))
- The inner loop would run for i time respectively
    - For i = 1 , the loop will run for 1 time 
    - For i = 2, the loop will run for 2 time 
     .
     .
     .
    - For i = log(n + 1), the loop will run for 2 to power log(n+1) times

The number of operations forms a _Geometric Progression_ which we will cover in the Number Theory chapter later on.

1+2+4+...+2^(logN+1)

By solving the above series the complexity will come out to be actually **linear** O(log (n))

#### Amortized Analysis
It's used where only a few operations of an algorithms are slow and remaining steps are considerably faster than one step.
We need to prove that the worst case of entire algorithm is slower than the worst case of particular slow operation times the number o	f operations

#### General Rule of Thumb to determin if your solution is acceptable or not ?


10^7 Operations -> O (N) 
10^6 Operations -> O(N log (n))
10^5 Operations -> O(N * log(n)) or O(N * sqRoot(n))
10^4 Operations -> O(N^2)
10^3 Operations -> O(n^2 * log(n))
10^2 Operations -> O(n^3)
20 Operations -> O(2^n)
10 Operations -> O(n!)





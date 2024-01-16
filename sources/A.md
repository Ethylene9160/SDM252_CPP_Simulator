Website Version：https://ethylene9160.github.io/CPP_Simulator

# Basic Concept Statement on CPP

In this term, you're supposted to explain each concept provide. 10 problems are provided, with 2 points each.(Total: 20 score)

## 1 Explain basic principle when initialize a data object.

A name can be any combination of letters, numbers, and the underscore (_), but cannot begin with a number and cannot be a language keyword.



## 2 Explain What is called memory leak, and how could it happen.

When allocating a memory for a variable, the programmer forget to release the memory after using that variable.



## 3 Function declaration

What is called the declaration of a function?

declaration of a function means making function known to compiler.



## 4 Explain Conditional Operator ( ? : )

Take `( expr ? execute_if_expr_is_true : execute_if_expr_is_false );` for example.

If expr evaluates to true, the expression following the question mark is executed. If expr evaluates to false, the expression following the colon is executed

Remark:  Any nonzero value is treated as true.



## 5 What is a pointer?

A pointer holds a memory address, something like, e.g., 0x00a0fb64.



## 6 What is `scope`?

The region of the program in which an object is visible is called its scope.



## 7 Explain: why declare the second parameter as a pointer to an object instead of a reference?

```c++
void bubble_sort(vector<int>& vec, ofstream* ofilptr = 0)
{
	// ......
	if (ofilptr)
        (*ofilptr) << "about to call swap! ix: " << ix << " jx: " << jx
        << "\t swapping: " << vec[ix] << " with " << vec[jx]
        << endl; // debugging output
        // ......
}
```

Reference need to be initialize. If we use reference, then it's not easy for us to judge whether the outputstream is passed outside the function. For example, here the pointer of the outputstream is initialized as a nullpointer, so we can use `if(ofilptr==nullptr)` to do the following operations.



## 8 What is called function overload

Two or more functions can be given the same name if the parameter list of each function is unique either by the type or by the number of parameters.

(Same function name with different parameter list)



## 9 What dose `sentinel` means in this example?

```c++
template <typename elemType>
elemType* find(const elemType* ptr, const elemType* sentinel,
const elemType& value)
{
    while (ptr != sentinel)
    { 
        if (*ptr == value)
    		return ptr;
    	ptr++; 
    }
    return 0;
}
```

the `sentinel` should mark 1 past the last element of the array, to judge wheter the programmer has finished traversing the array.



## 10 What is called iterater?

An iterator is a class object that **points to an element inside the container**



## 11 Why can we access the i-th element in a vector(or an array) using `*(address_of_the_first_elem+i)`?

A vector holds its elements in a **contiguous area** of memory.



## 12 What is the use of `end()` in containers?

returns an iterator that addresses **1 past** the last element.（返回最后一个元素的后面一位的地址，类比题目9.）



## 13 What is a constructor?

Constructors are special member functions that are called to initialize the object.

## 14 What is a copy constructor?

A copy constructor is a member function that initializes an object using another object of the same class.

## 15 What's the usage of the destructor?

 To free resources acquired within the constructor.

## 16 Tell the difference between the shallow copy and deep copy.

Shallow copy only copy values, while deep copy will copy both value of the target object and allocate memory for instances inside the copied target.

## 17 Tell what is public inheritance.

Retains public members of the base class as public and the protected members of the base class as protected in the derived class.

## 18 Tell the usage of keyword `mutable`

The keyword `mutable` is used to make a fine distinction between the essential member variables and the non-essential member variables of a class.

## 19 Stack memory

One day, Li Hua write a function:

```c++
vector<int>& febon(int pos){
    vector<int> v;
    //...
    return v;
}
```

He find the function cannot run successfully. Tell the reason of the problem.

vector `v`  is a local variable, which will be destroyed when the function end.

(The correct way is:)

```c++
vector<int> febon(int pos){
    vector<int> v;
    //...
    return v;
}
```

## 20 What is a static member variable?

A static member variable inside a class is a single and shared member that is accessible to all the objects of that class.

#  Simple Coding

In this quotes, giving 10 problems(2 pit each), fix the code block.

## 1 Swap by Pointers

Impliment a function below, to swap the values of the space the pointers pointing.

```c++
void swap(int *a, int *b){
    //Write down your code.
    
}
```

ANS:

```c++
void swap(int *a, int *b){
    //Write down your code.
    int c = *a;
    *a = *b;
    *b = c;
}
```

## 2 Print an Array

An array (int type), with length `size` as parameter. Print it like: `elem1 elem2 ...`

```c++
void printArary(int*array, int size){
    for(uint32_t i=0; i < size; ++i){
        //write down your code.
        cout << *(array+i) <<" ";
    }
    cout << endl;
}
```

ANS:

```c++
void printArary(int*array, int size){
    for(uint32_t i=0; i < size; ++i){
        //write down your code.
        cout << *(array+i) <<" ";
    }
    cout << endl;
}
```



## 3 Fix a Distructor

When the instance `MyClass` is to be distroied, we need to delete all the instances in the class. Fix the distructor in this example.

```c++
struct Entity{
  	int x;
    int y;
    int z;
    Entity():x(0),y(0),z(0){}
};
class ScopedPtr{
	Entity*e;
    MyClass(Entity*e){
        this->e = e;
    }
    ~Node(){
        //Write down your code.
        
    } 
};
```

ANS:

```c++
struct Entity{
  	int x;
    int y;
    int z;
    Entity():x(0),y(0),z(0){}
};
class ScopedPtr{
	Entity*e;
    MyClass(Entity*e){
        this->e = e;
    }
    ~Node(){
        //Write down your code.
        delete e;
    } 
};
```



## 4 Const and mutable

In class `Triangular`, I hope a variable named `m_next` whose type it int to be modified in const member functions. Declare it.

```c++
class Triangular {
public:
    //write down your code.
    
};
```

ANS:

```c++
class Triangular {
public:
    //write down your code.
    mutable int m_next; // non-essential
};
```



## 5 Initialize a Float

Initialize 1.3 as a float.

```c++
float a;
//assign a as a float.
//Write down your code.
```

ANS:

```c++
float a;
//assign a as a float.
//Write down your code.
a = 1.3f;
```

also, you can write as `a = (float)1.3;`,`a=float(1.3);`,`a=float(13.0/10.0)`.etc.

## 6 Help Li Hua to fix the problem.

In class `Stack`, here is a menber finction:

```c++
class Stack{
    bool empty(){
        return m_stack.empty();
    }
}
```

Li Hua want to split into a header file and a cpp file, and this is his header file.

```c++
class Stack{
    bool empty();
}
```

try to help him fdesign his cpp file. Hint: **define a member function outside the class body**

```c++
//write down your code.


```

Ans:

```c++
inline bool Stack::empty()// bool Stack::empty() is also ok.
{ 
    return m_stack.empty(); 
}
```

## 7 Design a pure virtual function.

Design `int elem(int pos) const` (a member function of class `NumSeq`) as a pure virtual funciton

```c++
class numSeq{
public:
    //write down your code.
}
```

ANS:

```c++
class numSeq{
public:
    //write down your code.
    virtual int elem(int pos) const = 0;
}
```

## 8 Type define

In this scope, I'd like to use `demical` to represent `double`. use `typedef` to help me.

```c++
//write down your code.
```

ANS:

```c++
//write down your code.
typedef double demical;
```

Hint: `typedef original_data_type your_data_type;`

## 9 Overload operator

Two Triangular iterator class objects are equal if the two `m_index` are equal, fix the scope.

```c++
bool ???(const Triangular_iterator& rhs) const{
    return this->m_index == rhs.m_index;
}
```

ANS:

```c++
bool operator==(const Triangular_iterator& rhs) const{
    return this->m_index == rhs.m_index;
}
```

## 10 Pass array name

I want to find the pointer of element whose value is 3 and store the address in variable `p`, using function `find` as follow. Fix it.

```c++
template <typename elemType>
elemType* find(const elemType* ptr, int size, const elemType& value)
{
    for (int ix = 0; ix < size; ++ix)
    	if (ptr[ix] == value)
    		return &ptr[ix];
    return 0;
}

int main(){
    int* arr = {2,3,5,10};
    //write down your code.
    int* p = ???
}
```

ANS:

`int*p = find<int>(arr, 4, 3);`

Also, answer can be:`int*p = find<int>(arr, sizeof(arr)/sizeof(int), 3);`

# Realistic Problem

Given 2 problems realistic, you're supposed to get correct codes.

（I don't know how to test...）

## 1 Febonacci

For a sequence `1,2,3,5,8`, let `febo(x)` return the $x_{th}$ febonacci value. Write down your code.

Hint: `febo(x) = febo(x-1)+febo(x-2)`, with `febon(1) = 1` and `febon(2) = 2` here.

```c++
int febon(int x){
    //write down your code.
    vector<int> elems();
    elems.push_back(1);
    elems.push_back(2);
    for(int i = 2; i < x; ++i){
        elems.push_back(elems[i-1]+elems[i-2]);
    }
    return elems[i-1];
}
```

## 2 Inheritance and polinomial

Gugugu














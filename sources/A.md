# Basic Concept Statement on CPP

In this term, you're supposted to explain each concept provide. 10 problems are provided, with 2 points each.(Total: 20 score)

## 1 Explain basic principle when initialize a data object.

A name can be any combination of letters, numbers, and the underscore (_), but cannot begin with a number and cannot be a language keyword.

## 2 Explain What is called memory leak, and how could it happen.



## 3 Write out the output.

```c++
int a = 5/3;
std::cout<<a<<std::endl;
```

output:`1`

## 4 Explain Conditional Operator ( ? : )

Take `( expr ? execute_if_expr_is_true : execute_if_expr_is_false );` for example.

If expr evaluates to true, the expression following the question mark is executed. If expr evaluates to false, the expression following the colon is executed

Remark:  Any nonzero value is treated as true.

## 5 What is a pointer?

A pointer holds a memory address, something like, e.g., 0x00a0fb64.

## 6 What is `scope`?

The region of the program in which an object is visible is called its scope.



#  Simple Coding

In this quotes, giving 10 problems(2 pit each), fix the code block.

## 1 Swap by Pointers

Impliment a function below, to swap the values of the space the pointers pointing.

```c++
void swap(int *a, int *b){
    //Write down your code.
    int c = *a;
    *a = *b;
    *b = c;
}
```

## 2 Print an Array

An array (int type), with

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
struct Point{
  	int x;
    int y;
    Point():x(0),y(0){}
};
class MyClass{
	Point*p;
    MyClass(){
        this->p = new Point();
    }
    ~Node(){
        //Write down your code.
        delete p;
    } 
};
```



## 4 Matrix

Here is a 1D array with length m*n, split it into a 2D array with m rows and n columns, to make it performes like an array.

```c++
vector<vector<int>> performMatrix(vector<int>&singleVector, int m, int n){
    vector<vector<int>> matrix(m, vector<int>(n,0));
    for(int i = 0; i < m; ++m){
        for(int j = 0; j < n; ++j){
            //write down your code
        }
    }
    return matrix;
}
```

## 5 Initialize a Float

Initialize 1.3 as a float.

```c++
float a;
//assign a as a float.
//Write down your code.
a = 1.3f;
```

also, you can write as `a = (float)1.3;`,`a=float(1.3);`,`a=float(13.0/10.0)`.etc.

# Realistic Problem

Given 2 problems realistic, you're supposed to get correct codes.

## 1 Febonacci

For a sequence `1,1,2,3,5,8`, let `febo(x)` return the $x_{th}$ febonacci value. Write down your code.

Hint: `febo(x) = febo(x-1)+febo(x-2)`, with `febo(1) = 1` and `febo(2) = 1` here.

```c++
int febo(int x){
    //write down your code.
    //The solution use "slide window", whose complexity is o(1) in space and o(n) in time.
    int first = 1, second = 1;
    int new_second = 0;
    if(x < 3) return 1;
    for(int i = 0; i < x-2; ++i){
        //second* = first+second
        //first* = second
        new_second = first+second;
        first = second;
        second = new_second;
    }
    return second;
}
```

## 2 














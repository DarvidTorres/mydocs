- **Declaration**:
	1. return type
	2. function name
	3. If the function takes arguments:
		1. Type of parameter
		2. Parameter
- **Definition**: the body of the function (code to be executed).

```c
<rtrn_type> <fun_name>(<prmtr_type> <prmtr1>, <prmtr_type> <prmtr2>) {
  // Body of the function  
}
```

Example:

```c
// Create a function  
void myFunction() {  
  printf("I just got executed!");  
}  
  
int main() {  
  myFunction(); // call the function  
  return 0;  
}  
  
// Outputs "I just got executed!"
```

Parameters and return values must have a type. `void` indicates no return type.

We can pass arguments to a function, but we need to define the parameters:

```c
rtrnType functionName(type holder1, type holder3) {  
  // code to be executed  
}
```

Example:

```c
/* function returning the max between two numbers */
int max(int num1, int num2) {

   /* local variable declaration */
   int result;
 
   if (num1 > num2)
      result = num1;
   else
      result = num2;
 
   return result; 
}
```

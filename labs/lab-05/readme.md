

# Lab 5:  Functions in C++

Welcome to the fifth CSC 200 lab! This will familiarize you with using Functions as well as give you some experience in their proper use. **Be sure to read and follow all instructions unless otherwise specified.**  You'll find the table of contents for this lab below.

1. [Introduction](#part-1-Introduction)
4. [Functions in C++ ](#part-2-Functions-in-C++)
3. [Exercises](#part-3-exercises)

## Part 1. Introduction

A function is a group of statements that together perform a task. Every C++ program has at least one function, which is **main()**, and all the most trivial programs can define additional functions.

You can divide up your code into separate functions. How you divide up your code among different functions is up to you, but logically the division usually is such that each function performs a specific task.

A function **declaration** tells the compiler about a function's name, return type, and parameters. A function **definition** provides the actual body of the function.

The C++ standard library provides numerous built-in functions that your program can call. For example, function **strcat()** to concatenate two strings, function **memcpy()** to copy one memory location to another location and many more functions.

Furthermore, The idea is to put some commonly or repeatedly done task together and make a function so that instead of writing the same code again and again for different inputs, we can call the function.

A function is known with various names like a **method** or a **sub-routine** or a **procedure**.



## Part 2. Functions in C++

1. #### **Function Definition** in c++

   The general form of a C++ function definition is as follows:

   ####  Syntax :

   ```c++
   return_type function_name( parameter list ) {
      body of the function
   }
   ```

   A C++ function definition consists of a function header and a function body. Here are all the parts of a function.

   - **Return Type** − A function may return a value. The **return_type** is the data type of the value the function returns. Some functions perform the desired operations without returning a value. In this case, the return_type is the keyword **void**.

   - **Function Name** − This is the actual name of the function. The function name and the parameter list together constitute the function signature.

   - **Parameters** − A parameter is like a placeholder. When a function is invoked, you pass a value to the parameter. This value is referred to as actual parameter or argument. The parameter list refers to the type, order, and number of the parameters of a function. Parameters are optional; that is, a function may contain no parameters.

   - **Function Body** − The function body contains a collection of statements that define what the function does.

     

   for example:

   Following is the source code for a function called **max()**. This function takes two parameters num1 and num2 and return the biggest of both :

   ```c++
   int max(int num1, int num2) {
      // local variable declaration
      int result;
    
      if (num1 > num2){
         result = num1;
      }else{
         result = num2;
      }
      return result; 
   }
   ```

   

2. #### **Function Declarations** in c++

   A function **declaration** tells the compiler about a function name and how to call the function. This is also known as **function prototyping**. The actual body of the function can be defined separately.

   A function declaration has the following parts :

   #### Syntax :

   ```c++
   return_type function_name( parameter list );
   ```

   Example: 

   For the above defined function max(), following is the function declaration :

   ```c++
   int max(int num1, int num2);
   ```

   Parameter names are not important in function declaration only their type is required, so following is also valid declaration, though not recommended as it does not provide any code-clarity :

   ```c++
   int max(int, int);
   ```

   **Note** : Function declaration is **required** when you define a function in one source file and you call that function in another file. In such case, you should declare the function at the top of the file calling the function. However, even if all functions are used solely in the file they are defined in, it is still good practice to prototype all functions. Primary benefits to doing so:
   1. By telling the compiler all of the functions you have, the order you write them in does not matter.
   2. Organizational benefits - all of the functions contained in this file is conveniently listed at the top, along with their return types.

3. #### **Calling a Function** in c++

   While creating a C++ function, you give a definition of what the function has to do. To use a function, you will have to call or invoke that function.

   When a program calls a function, program control is transferred to the called function. A called function performs defined task and when it’s return statement is executed or when its function-ending closing brace is reached, it returns program control back to the main program.

   To call a function, you simply need to pass the required parameters along with function name, and if function returns a value, then you can store returned value. For example :

   #### Syntax :

   ```c++
   // included libraries
   #include <iostream>
    
   // function declarations
   int max(int num1, int num2);
   
   // main function
   int main () {
      // local variable declaration:
      int a = 100;
      int b = 200;
      int ret;
    
      // calling a function to get max value.
      ret = max(a, b);
      std::cout << "Max value is : " << ret << endl;
    
      return 0;
   }
   
   /* After main(), implement all of the prototyped functions */
   
   // function returning the max between two numbers
   int max(int num1, int num2) {
      // local variable declaration
      int result;
     
      if (num1 > num2){
         result = num1;
      }else{
         result = num2;
      }
      return result; 
   }
   ```

   I kept max() function along with main() function and compiled the source code. While running final executable, it would produce the following result :

   Output:

   ```c++
   Max value is : 200
   ```

   

4. #### Function Arguments

   If a function is to use arguments, it must declare variables that accept the values of the arguments. These variables are called the **formal parameters** of the function.

   The formal parameters behave like other local variables inside the function and are created upon entry into the function and destroyed upon exit.

   While calling a function, there are two ways that arguments can be passed to a function :

   - [Call by Value](https://www.tutorialspoint.com/cplusplus/cpp_function_call_by_value.htm)

     This method copies the actual value of an argument into the formal parameter of the function. In this case, changes made to the parameter inside the function have no effect on the argument.

   - [Call by Pointer](https://www.tutorialspoint.com/cplusplus/cpp_function_call_by_pointer.htm)

     This method copies the address of an argument into the formal parameter. Inside the function, the address is used to access the actual argument used in the call. This means that changes made to the parameter affect the argument (**Don't worry, you'll learn this later**).

   - [Call by Reference](https://www.tutorialspoint.com/cplusplus/cpp_function_call_by_reference.htm)

     This method copies the reference of an argument into the formal parameter. Inside the function, the reference is used to access the actual argument used in the call. This means that changes made to the parameter affect the argument **(Don't worry you'll learn this later)**.

     

   By default, C++ uses **call by value** to pass arguments. In general, this means that code within a function cannot alter the arguments used to call the function and above mentioned example while calling max() function used the same method.

   

5. #### Default Values for Parameters

   When you define a function, you can specify a default value for each of the last parameters. This value will be used if the corresponding argument is left blank when calling to the function.

   This is done by using the assignment operator and assigning values for the arguments in the function definition. If a value for that parameter is not passed when the function is called, the default given value is used, but if a value is specified, this default value is ignored and the passed value is used instead. Consider the following example :

   #### Example:

   ```c++
   #include <iostream>
    
   int sum(int a, int b = 20) {
      int result;
      result = a + b;
     
      return (result);
   }
   int main () {
      // local variable declaration:
      int a = 100;
      int b = 200;
      int result;
    
      // calling a function to add the values.
      result = sum(a, b);
      std::cout << "Total value is :" << result << endl;
   
      // calling a function again as follows.
      result = sum(a);
      std::cout << "Total value is :" << result << endl;
    
      return 0;
   }
   ```

   Output:

   ```c++
   Total value is :300
   Total value is :120
   ```

   

6. #### **Main Function**

   The main function is a special function. Every C++ program must contain a function named main. It serves as the entry point for the program. The computer will start running the code from the beginning of the main function.

   **Types of main Function:**

   1) The first type is – main function without parameters :

      ```c++
      // Without Parameters
      int main()
      {
         ...
         return 0;
      }
      ```

      

   2) Second type is main function with parameters :

      ```c++
      // With Parameters
      int main(int argc, char * const argv[])
      {
         ...
         return 0;
      }
      ```

      The reason for having the parameter option for the main function is to allow input from the command line.

      When you use the main function with parameters, it saves every group of characters (separated by a space) after the program name as elements in an array named argv.

      Since the main function has the return type of int, the programmer must always have a return statement in the code. The number that is returned is used to inform the calling program what the result of the program’s execution was. Returning 0 signals that there were no problems.

## Part 3. Exercises

1. Write a function that will accept two arguments, a string and a character. Your function should search the string for and count the number of occurrences of the given character. 
   
   ```
   Enter the string to search:  Sally sells sea shells down by the sea shore.
   Enter the character to count: s
   
   output : There were 8 s's in that string.
   ```
   
1. Write a function that will convert a list of characters into a string. Return this string to main and display it.
   
   ```
   # Input:    ['H', 'e', 'l', 'l', 'o']
   # Output: "Hello"
   ```
   
1. Write a function that will return a random item from a list. Return this item to main and display it.
   
   ```
   # Input:   [5, 10, 15, 20, 25]
   # Possible Output: 15
   ```
   
   

### Requirements

1. Exercise 1 completed.

2. Exercise 2 completed.

3. Exercise 3 completed.

   






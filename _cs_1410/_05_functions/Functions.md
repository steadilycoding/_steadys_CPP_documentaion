A function is a self-contained block of code that performs a specific task. Functions allow you to organize your code into manageable and reusable chunks, making your code more modular and easier to understand.

```cpp
#include <iostream>

// Function declaration or prototype
int add(int a, int b);

int main() {
    int num1 = 10;
    int num2 = 20;

    // Call the 'add' function and store the result in 'sum'
    int sum = add(num1, num2);

    std::cout << "Sum: " << sum << std::endl;

    return 0;
}

// Function definition
int add(int a, int b) {
    return a + b;
}

```

In this example:

1. We start by including the necessary header (`<iostream>`) for input and output.
2. We declare a function prototype for the `add` function. This prototype tells the compiler about the function's name, return type, and parameter types. It allows us to call the function before its actual definition.
3. In the `main` function, we declare two integers `num1` and `num2` and assign them values.
4. We call the `add` function and pass `num1` and `num2` as arguments. The function calculates the sum of the two numbers and returns the result.
5. The result of the `add` function is stored in the variable `sum`, which we then print to the console.


Later in the code, we define the `add` function. The function takes two integer parameters, `a` and `b`, and returns the sum of these two numbers.

Functions in C++ can be as simple as the example above or much more complex, involving control structures, loops, and multiple parameters. They allow you to encapsulate functionality, promote code reusability, and make your code more organized and modular.
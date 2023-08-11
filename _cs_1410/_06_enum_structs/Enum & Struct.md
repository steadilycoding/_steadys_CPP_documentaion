
### Enum

An enum (short for "enumeration") is a user-defined data type in C++ used to represent a set of named constants. It provides a way to assign meaningful names to a set of values, making the code more readable and maintainable. Enums are typically used when you have a small, finite, and well-defined set of related values that need to be represented in your program.

```cpp
#include <iostream>

// Define an enum called 'Color'
enum class Color {
    Red,
    Green,
    Blue,
    Yellow,
    Orange
};

int main() {
    // Declare a variable of the 'Color' enum type
    Color myColor = Color::Green;

    // Using a switch statement to handle different color cases
    switch (myColor) {
        case Color::Red:
            std::cout << "The color is Red." << std::endl;
            break;
        case Color::Green:
            std::cout << "The color is Green." << std::endl;
            break;
        case Color::Blue:
            std::cout << "The color is Blue." << std::endl;
            break;
        case Color::Yellow:
            std::cout << "The color is Yellow." << std::endl;
            break;
        case Color::Orange:
            std::cout << "The color is Orange." << std::endl;
            break;
    }

    return 0;
}
```

Enums provide a way to make your code more self-documenting and less error-prone by associating meaningful names with numeric values. They are especially useful when you need to represent a small, finite set of options or states in your program.


### Struct 

a `struct` is a composite data type that allows you to group together variables of different data types under a single name. It's used to create a custom data structure that holds multiple pieces of related information. A `struct` is similar to a class, but with the default access modifier being `public` for its members.

```cpp
#include <iostream>
#include <string>

// Define a struct called 'Person'
struct Person {
    std::string name;
    int age;
    double height;
};

int main() {
    // Declare a variable of the 'Person' struct type
    Person person1;

    // Assign values to the struct members
    person1.name = "Alice";
    person1.age = 28;
    person1.height = 5.6;

    // Access and print the struct members
    std::cout << "Name: " << person1.name << std::endl;
    std::cout << "Age: " << person1.age << std::endl;
    std::cout << "Height: " << person1.height << " feet" << std::endl;

    return 0;
}

```

In this example, we define a `struct` named `Person` with three members: `name` (a string), `age` (an integer), and `height` (a double). We then declare a variable `person1` of the `Person` struct type and assign values to its members. Finally, we access and print the values of the struct members using the dot (`.`) operator.

Structs are often used to represent simple data structures, like records or data packets, where you want to group related pieces of data together for easier manipulation and organization. They provide a way to create more meaningful abstractions in your code and improve readability.
"Programmers can only solve elementary problems with a single class program; solving more complex problems requires multiple classes." - Dr. Brinkerhoff

### Six relationships for "binding" collections of objects:

-  Inheritance 
- Composition  
- Aggregation 
- Association  
- Dependency   
- Realization 

Lifetime - Objects that are created/destroyed together 
Sharing - Parts of the whole can be shared 
Binding strength - Tight, loose 

## Inheritance 

![[Pasted image 20230806143254.png]]

Inheritance is a fundamental concept in object-oriented programming, and it allows a class (called the derived class) to inherit the properties and behaviors of another class (called the base class). In C++, you can implement inheritance using the `class` keyword and specifying the base class from which the derived class should inherit.

consider an example of inheritance with a `Shape` base class and two derived classes: `Rectangle` and `Circle`.

```cpp
#include <iostream>

// Base class: Shape
class Shape {
public:
    virtual void draw() const {
        std::cout << "Drawing a generic shape.\n";
    }
};

// Derived class: Rectangle
class Rectangle : public Shape {
public:
    void draw() const override {
        std::cout << "Drawing a rectangle.\n";
    }
};

// Derived class: Circle
class Circle : public Shape {
public:
    void draw() const override {
        std::cout << "Drawing a circle.\n";
    }
};

int main() {
    Shape shape;
    Rectangle rectangle;
    Circle circle;

    shape.draw();      // Output: Drawing a generic shape.
    rectangle.draw();  // Output: Drawing a rectangle.
    circle.draw();     // Output: Drawing a circle.

    return 0;
}

```

In this example, we have a `Shape` base class that contains a virtual function `draw()`. The `draw()` function is declared as `virtual` in the base class, which allows it to be overridden by derived classes.

Next, we have two derived classes: `Rectangle` and `Circle`. Both classes inherit publicly from the `Shape` base class using the `public` keyword. This means that the `Rectangle` and `Circle` classes will have access to the public members of the `Shape` class.

Each derived class (`Rectangle` and `Circle`) overrides the `draw()` function with its own implementation. When you call the `draw()` function on objects of these derived classes, the appropriate version of the function will be called based on the actual type of the object.

In the `main()` function, we create objects of the `Shape`, `Rectangle`, and `Circle` classes and call the `draw()` function on each of them. As a result, the correct `draw()` function corresponding to each class is called, demonstrating the concept of inheritance in C++.

## Composition 

![[Pasted image 20230806143658.png]]

In C++, composition is a design principle that allows you to create complex objects by combining simpler objects (components) together. It is achieved by creating classes that contain objects of other classes as member variables. This way, you can build more complex functionality by utilizing the behavior of the individual components.

Consider the following example of a simple composition using a `Car` class. We'll create a `Car` class that is composed of an `Engine` and a `Wheel` class.

```cpp
#include <iostream>
#include <string>

// Engine class
class Engine {
public:
    void start() {
        std::cout << "Engine started.\n";
    }
};

// Wheel class
class Wheel {
public:
    void rotate() {
        std::cout << "Wheel rotating.\n";
    }
};

// Car class composed of Engine and Wheel
class Car {
private:
    Engine engine;
    Wheel wheels[4]; // Four wheels

public:
    void startCar() {
        engine.start();
        for (int i = 0; i < 4; ++i) {
            wheels[i].rotate();
        }
        std::cout << "Car started.\n";
    }
};

int main() {
    Car myCar;
    myCar.startCar();
    return 0;
}

```

In this example, we have three classes: `Engine`, `Wheel`, and `Car`. The `Engine` and `Wheel` classes represent individual components of a car. The `Car` class is composed of an `Engine` object and an array of four `Wheel` objects. The `Car` class has a member function `startCar()`, which starts the engine and rotates all the wheels.

When you create an instance of the `Car` class, it contains both the `Engine` and the `Wheel` objects, and you can call the `startCar()` function to start the car, which, in turn, starts the engine and rotates all the wheels.

This is a simple example of composition, but it demonstrates how you can build more complex objects by combining simpler ones using the concept of composition in C++.

## Aggregation 

![[Pasted image 20230806145210.png]]

Aggregation represents a "has-a" relationship between classes. In aggregation, a class contains an object of another class as a member variable, but the two classes are not tightly coupled. The lifetime of the aggregated object can be independent of the container class. 

To illustrate this, consider the following example of aggregation between a `Student` class and an `Address` class.

```cpp
#include <iostream>
#include <string>

// Address class
class Address {
public:
    Address(const std::string& street, const std::string& city, const std::string& zip) 
        : street(street), city(city), zip(zip) {}

    void display() const {
        std::cout << "Street: " << street << ", City: " << city << ", Zip: " << zip << std::endl;
    }

private:
    std::string street;
    std::string city;
    std::string zip;
};

// Student class with aggregated Address object
class Student {
public:
    Student(const std::string& name, int age, const Address& address) 
        : name(name), age(age), address(address) {}

    void displayInfo() const {
        std::cout << "Name: " << name << ", Age: " << age << std::endl;
        std::cout << "Address: ";
        address.display();
    }

private:
    std::string name;
    int age;
    Address address; // Aggregated Address object
};

int main() {
    Address studentAddress("123 Main St", "Cityville", "12345");
    Student student("John Doe", 20, studentAddress);

    student.displayInfo();

    return 0;
}

```

In this example, we have an `Address` class that represents a physical address with its member variables `street`, `city`, and `zip`. The `Address` class has a member function `display()` to print the address details.

Next, we have a `Student` class that contains an aggregated object of the `Address` class. The `Student` class has member variables `name`, `age`, and `address`. The `Student` class also has a member function `displayInfo()` to display the student's name, age, and address.

In the `main()` function, we create an `Address` object representing the student's address. Then, we create a `Student` object named `student`, passing the `Address` object as an argument to the constructor.

The key difference between aggregation and composition is that in aggregation, the `Student` class doesn't own the `Address` object. The `Address` object can exist independently outside of the `Student` class, and the `Student` class simply holds a reference to it. If the `Student` object is destroyed, the `Address` object will not be automatically destroyed. This makes aggregation a looser relationship between classes compared to composition.

## Dependency 

![[Pasted image 20230806145816.png]]

Dependency refers to a situation where one class relies on another class to perform some specific functionality. The dependent class uses objects or functions from the other class to accomplish its tasks. This relationship can be temporary and loosely coupled, and the dependent class does not "own" the objects or functions it relies upon.

Consider the example of dependency below that uses a `Logger` class that depends on a `Console` class for displaying log messages:

```cpp
#include <iostream>
#include <string>

// Console class for displaying messages
class Console {
public:
    void print(const std::string& message) const {
        std::cout << message << std::endl;
    }
};

// Logger class depends on Console class
class Logger {
private:
    Console console;

public:
    void log(const std::string& message) const {
        console.print("LOG: " + message);
    }
};

int main() {
    Logger logger;
    logger.log("This is a log message.");

    return 0;
}

```

In this example, we have a `Console` class that has a member function `print()` to display messages on the console.

Next, we have a `Logger` class that depends on the `Console` class. The `Logger` class contains a `Console` object as a member variable. The `Logger` class has a member function `log()` that takes a message as input and uses the `Console` object to display the log message by calling its `print()` function.

In the `main()` function, we create an instance of the `Logger` class and call its `log()` function, passing a log message as an argument. The `Logger` class relies on the `Console` class to print the log message on the console.

The `Logger` class depends on the `Console` class to carry out its functionality.

## Association 

![[Pasted image 20230806230549.png]]


Association represents a relationship between classes where one class is related to another class, but the relationship is not as strong as in composition or aggregation. The associated classes can exist independently of each other, and there is no ownership or containment involved.

Let's demonstrate association with a simple example of a `Department` class and an `Employee` class:

```cpp
#include <iostream>
#include <string>

// Forward declaration of Employee class
class Employee;

// Department class
class Department {
private:
    std::string name;

public:
    Department(const std::string& departmentName) : name(departmentName) {}

    void addEmployee(const Employee& employee);

    void displayEmployees() const;
};

// Employee class
class Employee {
private:
    std::string name;
    int employeeId;

public:
    Employee(const std::string& employeeName, int id) : name(employeeName), employeeId(id) {}

    std::string getName() const {
        return name;
    }

    int getEmployeeId() const {
        return employeeId;
    }
};

// Implementation of Department's member functions
void Department::addEmployee(const Employee& employee) {
    // Here, we can perform some logic to add the employee to the department's employee list.
}

void Department::displayEmployees() const {
    // Here, we can display the employees associated with this department.
}

int main() {
    Department hrDepartment("Human Resources");
    Employee employee1("John Doe", 1001);
    Employee employee2("Jane Smith", 1002);

    // Associate employees with the department
    hrDepartment.addEmployee(employee1);
    hrDepartment.addEmployee(employee2);

    // Display the employees in the department
    hrDepartment.displayEmployees();

    return 0;
}

```

In this example, we have a `Department` class and an `Employee` class. The `Department` class represents a department in a company, and the `Employee` class represents an employee.

In the `Department` class, we have a member function `addEmployee()` that takes an `Employee` object as an argument. This function is used to associate an employee with the department, but it doesn't imply any ownership or containment relationship between the two classes.

Similarly, the `displayEmployees()` function in the `Department` class can be used to display the employees associated with the department, but it doesn't indicate any tight coupling or ownership of the `Employee` objects.

In the `main()` function, we create a `Department` object named `hrDepartment` and two `Employee` objects named `employee1` and `employee2`. We then use the `addEmployee()` function to associate these employees with the HR department and display the employees in the department using the `displayEmployees()` function.
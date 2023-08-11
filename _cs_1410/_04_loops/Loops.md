
Essentially loops just repeat lines of code to reduce redundancy.

### While loops 

A while loop is a valid option if you or program does not know how many iterations. Code block will continue to execute as long as the while statement evaluates to true. 

```cpp
int number = 1;
    while (number <= 3) 
    {
        cout << "Elmo says: " << number << "!" << endl;
        number++;
    }

    srand(time(0));
    int target;
    int d1 = 0, d2 = 0, tries = 0;

    cout << "Target value: ";
    cin >> target;

    while (target >= 2 && target <= 12 && d1 + d2 != target) 
    {
        d1 = rand() % 6 + 1;
        d2 = rand() % 6 + 1;
        cout << "[" << d1 << "][" << d2 << "]" << endl;
        tries++;
    }
    if (tries)
        cout << "Number of tries: " << tries << endl;
    else
        cout << "Not possible." << endl;

    cout << endl << endl;

```

### Do while loop

A do while loop is a valid option if you or the program does not know how many iterations AND the loop will ALWAYS execute at least once. Beyond that, it will perform exactly like a while loop.

```cpp
int number = 1;
    do 
    {
        cout << "Elmo says: " << number << "!" << endl;
        number++;
    } while (number <= 3);
```

### For loop

A for loop is a valid option if you or the program knows how many iterations need to be executed. The for loop will continue to execute until it has reached the specified number of iterations.

```cpp
for (int number = 1; number <= 3; number++) 
    {
        cout << "Elmo says " << number << "!" << endl;
    }

    int value;
    cout << "Enter a number: ";
    cin >> value;

    for (int i = 1; i <= value; i++)         // this will find factors of a number
        if (value % i == 0)
            cout << i << ", " << value / i << endl;

```

### For range loop 

A for range loop is a valid option to iterate through an existing collection, such as an array of elements. The for range loop will continue to execute until it has reached the end of the collection. 

```cpp
string s = "Hello, World!";
    for (char c : s)
        cout << c << ", " << endl;

    string student[] = { "Thomas", "Austin", "Olga", "Phil", "Hunter" };
    for (string studentName : student)
        cout << "Hello " << studentName << endl;
```

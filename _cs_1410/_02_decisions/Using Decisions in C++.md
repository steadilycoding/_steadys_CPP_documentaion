## Control Structures

Things happen in C++ Sequentially

For example:
```cpp
int x = 5;                // This runs first 
    x += 10;              // This runs second 
    cout << x << endl;    // This runs third
```

### Relational Expressions:

A relational expression is an expression that evaluates to either true or false. Relational operators include:
 <
 >
 <=
 >=
 ==
 !=
 bool

Example one:
```cpp
int student = 27;
    bool section = student > 20;
    cout << section << endl; // Prints "1" which equals "True"
```

Example two:
```cpp
int missing = 4;
    bool pass = missing <= 3;
    cout << pass << endl;    // Prints "0" which equals "False"
```

### Branching (If-Statements):

If statement:
```cpp
char play;
    cout << "Do you want to play a game? (y/n): " << endl;
    cin >> play;

    if (play == 'y') // Single quotations for a single character "Char"
    {
        cout << "Let's play." << endl;
        cout << "You will roll some dice." << endl;


        // IF-ELSE STATEMENT:

        cout << "I will hide a seed under 1 of 3 cups." << endl;
        srand(time(0));
        int cup = rand() % 3 + 1;
        int choice;
        cout << "Which cup will you choose? (1-3): " << endl;
        cin >> choice;

        if (choice == cup)
        {
            cout << "That is correct! You win!" << endl;
        }
        else
        {
            cout << "This is incorrect! You Suck! It was located inside of cup number " << cup << "." << endl;
        }

    }
```

Else-if statement:
```cpp
 srand(time(0));
    int player = rand() % 13 + 2;
    int computer = rand() % 13 + 2;

    cout << "\nYour card: " << player << endl;
    cout << "My card: " << computer << endl;

    if (player > computer)
        cout << "You Win!" << endl;
    else if (computer > player)
        cout << "You Loose!" << endl;
    else
        cout << "Its a WAR!" << endl;
```

### Logical Operators:

Logical operators are **used to check whether an expression is true or false**. Logical operators include:
- && (And)
- || (Or)
- ! (Not)

```cpp
int dice1 = rand() % 6 + 1;
    int dice2 = rand() % 6 + 1;
    cout << "[" << dice1 << "]" << "[" << dice2 << "]" << endl;

    // Want to check for anything EXCEPT seven
    if (!(dice1 + dice2 == 7)) // same as !=
        cout << "Keep rolling!" << endl;
```

And operator: && (all parts of the relational expression must be true)
```cpp
if (dice1 == 2 && dice2 == 2)
        cout << "Hard 4" << endl;
    if (dice1 == 3 && dice2 == 3)
        cout << "Hard 6" << endl;
    if (dice1 == 4 && dice2 == 4)
        cout << "Hard 8" << endl;
```

Or operator: || (at least 1 part of the relational expression must be true)
```cpp
if (dice1 + dice2 == 7 || dice1 + dice2 == 11)
        cout << "Winner!" << endl;
    else if (dice1 + dice2 == 2 || dice1 + dice2 == 3 || dice1 + dice2 == 12)
        cout << "You Suck!" << endl;
    else
        cout << "Point is " << (dice1 + dice2) << endl;
```

### Nested If Statements:

A nested if statement is simply an if statement inside of another if statement.
For example:
```cpp
cout << endl << endl;

    int guess;
    cout << "Which cup will the ball fall into? (1, 2, 3, 4): " << endl;
    cin >> guess;

    int roll1 = rand() % 2;  // Between 0 and 1
    int roll2;

    if (roll1 == 0) 
    {
        cout << "Ball rolls left" << endl;
        roll2 = rand() % 2 + 1; // Between 1 and 2
        if (roll2 == 1) 
        {
            cout << "Ball rolls left and lands in cup 1" << endl;
        }
        else 
        {
            cout << "Ball rolls right and lands in cup 2" << endl;
        }
    }
    else 
    {
        cout << "Ball rolls right" << endl;
        roll2 = rand() % 2 + 2; // Between 2 and 3
        if (roll2 == 2) 
        {
            cout << "Ball rolls left and lands in cup 3" << endl;
        }
        else 
        {
            cout << "Ball rolls right and lands in cup 4" << endl;
        }
    }

    if (roll1 + roll2 == guess)
    {
        cout << "You win!";
    }
    else
    {
        cout << "You lose, try again.";
    }
```

### Switches

Everything that you can do with a switch can be done w/ an if statement. A switch uses a single variable for decisions/branching.
For example:
```cpp
int choice = rand() % 3;

    switch (choice) 
    {
    case 0:
        cout << "Rock" << endl;
        break;
    case 1:
        cout << "Paper" << endl;
        break;
    case 2:
        cout << "Scissors" << endl;
        break;
    }
```

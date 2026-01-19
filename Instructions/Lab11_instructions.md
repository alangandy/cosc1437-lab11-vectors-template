# Lab 11 (COSC 1437): Building a Complete Grade Calculator with Vectors

## Objective

- Build a complete grade calculator application from the ground up
- Learn fundamental C++ concepts: variables, input/output, loops, conditionals, functions, and header files
- Understand and implement vector storage for assignment scores
- Create a modular, well-organized C++ program

## Prerequisites

- Basic understanding of programming concepts
- C++ development environment set up

---

## Introduction

In this lab, you'll build a complete grade calculator application. This lab covers concepts from C++ fundamentals through vectors, preparing you for the advanced topics in COSC 1437.

By the end of this lab, you'll have a working application that:
- Displays a personalized greeting based on time of day
- Accepts a grading scheme (total points and grade thresholds)
- Allows unlimited assignment score entry
- Stores all scores in a vector
- Calculates and displays the final letter grade

---

## Part 1: Project Setup and Basic Output

### Concepts Covered
- Program structure
- `#include` directives
- The `main()` function
- Console output with `std::cout`

### Step 1.1: Create Your Project Files

Create three files:

| File | Purpose |
|------|---------|
| `main.cpp` | Main program logic |
| `greeting.h` | Greeting function declaration |
| `greeting.cpp` | Greeting function implementation |

### Step 1.2: Start with main.cpp

```cpp
#include <iostream>

int main() {
    std::cout << "Grade Calculator\n";
    std::cout << "================\n";
    
    return 0;
}
```

**Compile and run** to verify your setup works:
```bash
g++ -o grade_calc main.cpp
./grade_calc
```

---

## Part 2: Variables and User Input

### Concepts Covered
- Variable declarations
- Data types (`int`, `float`, `char`, `bool`)
- User input with `std::cin`

### Step 2.1: Add Variables for Grading Scheme

Add these variable declarations inside `main()`, before any output:

```cpp
int main() {
    // Grading scheme variables
    int total_course_points = 0;
    float A_points = 0.00;
    float B_points = 0.00;
    float C_points = 0.00;
    float D_points = 0.00;
    
    // Calculated percentages
    float A_percentage = 0.00;
    float B_percentage = 0.00;
    float C_percentage = 0.00;
    float D_percentage = 0.00;
    
    // Score tracking
    float total_points_earned = 0.00;
    float total_percentage_earned = 0.00;
    float assignment_score = 0.00;
    
    // Program control
    char earned_grade;
    bool score_input = true;
    int assignment = 1;
    
    // ... rest of program
}
```

### Step 2.2: Get Grading Scheme Input

After the variable declarations, add input for the grading scheme:

```cpp
    // Welcome message
    std::cout << "Welcome to [YOUR NAME]'s Grade Calculator for COSC 1437\n\n";

    // Get total course points
    std::cout << "Grading Scheme Setup\n";
    std::cout << "====================\n";
    std::cout << "Please input the Total Points Possible: ";
    std::cin >> total_course_points;
    std::cout << '\n';
```

**Important:** Replace `[YOUR NAME]` with your actual name!

---

## Part 3: Loops for Repeated Input

### Concepts Covered
- `for` loops
- `while` loops
- `do-while` loops
- Loop control

### Step 3.1: Use a For Loop for Grade Thresholds

Add a `for` loop to get the minimum points for each letter grade:

```cpp
    // Get grade thresholds using for loop
    for (char grade = 'A'; grade <= 'D'; grade++) {
        std::cout << "Please input the Minimum Points for a '" << grade << "': ";
        if (grade == 'A') {
            std::cin >> A_points;
        } else if (grade == 'B') {
            std::cin >> B_points;
        } else if (grade == 'C') {
            std::cin >> C_points;
        } else if (grade == 'D') {
            std::cin >> D_points;
        }
        std::cout << '\n';
    }
```

---

## Part 4: Mathematical Operations

### Concepts Covered
- Arithmetic operators
- Calculating percentages
- The `<cmath>` library

### Step 4.1: Include the cmath Library

At the top of `main.cpp`:

```cpp
#include <iostream>
#include <cmath>
```

### Step 4.2: Calculate Grade Percentages

After getting the thresholds, calculate the percentages:

```cpp
    // Calculate percentages
    A_percentage = (A_points / total_course_points) * 100;
    B_percentage = (B_points / total_course_points) * 100;
    C_percentage = (C_points / total_course_points) * 100;
    D_percentage = (D_points / total_course_points) * 100;
```

### Step 4.3: Display the Grading Scheme

```cpp
    // Display the grading scheme
    std::cout << "The Grading Scheme You Input\n";
    std::cout << "============================\n";
    std::cout << "Total Points Possible in the Course: " << total_course_points << '\n';
    std::cout << "Points needed for an 'A': " << A_points << " or " << A_percentage << "%\n";
    std::cout << "Points needed for a 'B': " << B_points << " or " << B_percentage << "%\n";
    std::cout << "Points needed for a 'C': " << C_points << " or " << C_percentage << "%\n";
    std::cout << "Points needed for a 'D': " << D_points << " or " << D_percentage << "%\n";
```

---

## Part 5: Conditional Statements

### Concepts Covered
- `if` statements
- `else if` chains
- `else` clauses
- Comparison operators

### Step 5.1: Determine the Letter Grade

After all scores are entered (we'll add that loop next), determine the grade:

```cpp
    // Determine the final grade
    if (total_points_earned >= A_points) {
        earned_grade = 'A';
    }
    else if (total_points_earned >= B_points) {
        earned_grade = 'B';
    }
    else if (total_points_earned >= C_points) {
        earned_grade = 'C';
    }
    else if (total_points_earned >= D_points) {
        earned_grade = 'D';
    }
    else {
        earned_grade = 'F';
    }
```

---

## Part 6: Functions and Header Files

### Concepts Covered
- Function declarations and definitions
- Header files
- `#ifndef` / `#define` / `#endif` guards
- Separate compilation

### Step 6.1: Create greeting.h

Create a new file called `greeting.h`:

```cpp
#ifndef GREETING_H
#define GREETING_H

// Function declaration
void displayGreeting();

#endif
```

**Why header guards?**
- Prevents the header from being included multiple times
- The `#ifndef` checks if `GREETING_H` is not defined
- If not defined, it defines it and includes the content
- If already defined, the content is skipped

### Step 6.2: Create greeting.cpp

Create a new file called `greeting.cpp`:

```cpp
#include "greeting.h"
#include <iostream>
#include <ctime>

void displayGreeting() {
    // Get current time
    time_t now = time(0);
    tm* localTime = localtime(&now);
    int hour = localTime->tm_hour;
    
    // Display appropriate greeting
    std::cout << "\n";
    if (hour >= 5 && hour < 12) {
        std::cout << "Good morning!\n";
    } else if (hour >= 12 && hour < 17) {
        std::cout << "Good afternoon!\n";
    } else if (hour >= 17 && hour < 21) {
        std::cout << "Good evening!\n";
    } else {
        std::cout << "Hello, night owl!\n";
    }
    std::cout << "\n";
}
```

### Step 6.3: Include and Use the Greeting

In `main.cpp`, add the include at the top:

```cpp
#include <iostream>
#include <cmath>
#include "greeting.h"
```

Then call it at the beginning of `main()`:

```cpp
int main() {
    // Variable declarations...
    
    // Display greeting
    displayGreeting();
    
    // Welcome message
    std::cout << "Welcome to [YOUR NAME]'s Grade Calculator for COSC 1437\n\n";
    
    // ... rest of program
}
```

### Step 6.4: Update Your Compile Command

Now you need to compile both .cpp files:

```bash
g++ -o grade_calc main.cpp greeting.cpp
./grade_calc
```

---

## Part 7: Vectors for Dynamic Storage

### Concepts Covered
- The `<vector>` library
- Declaring vectors
- `push_back()` to add elements
- `size()` to get count
- Iterating through vectors

### Step 7.1: Include the Vector Library

At the top of `main.cpp`:

```cpp
#include <iostream>
#include <cmath>
#include <vector>
#include "greeting.h"
```

### Step 7.2: Declare a Vector for Scores

Add this with your other variable declarations:

```cpp
    // Vector to store all assignment scores
    std::vector<float> assignment_scores;
```

### Step 7.3: Create the Score Input Loop

Add this after displaying the grading scheme:

```cpp
    // Multiple Assignment Input
    std::cout << "\nGrade Calculation\n";
    std::cout << "=================\n";
    std::cout << "You will be prompted to input scores for all assignments.\n";
    std::cout << "(Input a negative number to cease input and calculate letter grade.)\n\n";

    do {
        std::cout << "Please input the points earned for Assignment " << assignment << ": ";
        std::cin >> assignment_score;
        
        if (assignment_score >= 0) {
            assignment_scores.push_back(assignment_score);  // Store in vector
            total_points_earned += assignment_score;
            assignment++;
        } else {
            score_input = false;
        }
    } while (score_input);
```

### Step 7.4: Display All Stored Scores

After the input loop, display the scores from the vector:

```cpp
    // Display all scores entered
    std::cout << "\nScores Entered\n";
    std::cout << "==============\n";
    for (size_t i = 0; i < assignment_scores.size(); ++i) {
        std::cout << "Assignment " << (i + 1) << ": " << assignment_scores[i] << '\n';
    }
```

**Note:** We use `size_t` for the loop counter because `vector.size()` returns a `size_t` (unsigned integer type).

---

## Part 8: Putting It All Together

### Step 8.1: Add Final Calculations and Output

After displaying scores and determining the grade:

```cpp
    // Calculate percentage
    total_percentage_earned = (total_points_earned / total_course_points) * 100;

    // Display results
    std::cout << "\nFinal Results\n";
    std::cout << "=============\n";
    std::cout << "Total Points Earned: " << total_points_earned << '\n';
    std::cout << "Total Points Possible: " << total_course_points << '\n';
    std::cout << "Total Percentage: " << total_percentage_earned << "%\n";
    std::cout << "Total Percentage (rounded): " << round(total_percentage_earned) << "%\n";
    std::cout << "Final Letter Grade: " << earned_grade << '\n';

    return 0;
```

---

## Complete Code Listing

### greeting.h

```cpp
#ifndef GREETING_H
#define GREETING_H

void displayGreeting();

#endif
```

### greeting.cpp

```cpp
#include "greeting.h"
#include <iostream>
#include <ctime>

void displayGreeting() {
    time_t now = time(0);
    tm* localTime = localtime(&now);
    int hour = localTime->tm_hour;
    
    std::cout << "\n";
    if (hour >= 5 && hour < 12) {
        std::cout << "Good morning!\n";
    } else if (hour >= 12 && hour < 17) {
        std::cout << "Good afternoon!\n";
    } else if (hour >= 17 && hour < 21) {
        std::cout << "Good evening!\n";
    } else {
        std::cout << "Hello, night owl!\n";
    }
    std::cout << "\n";
}
```

### main.cpp

```cpp
#include <iostream>
#include <cmath>
#include <vector>
#include "greeting.h"

int main() {
    // Variable declarations
    int total_course_points = 0;
    float A_points = 0.00;
    float B_points = 0.00;
    float C_points = 0.00;
    float D_points = 0.00;
    
    float A_percentage = 0.00;
    float B_percentage = 0.00;
    float C_percentage = 0.00;
    float D_percentage = 0.00;
    
    float total_points_earned = 0.00;
    float total_percentage_earned = 0.00;
    
    float assignment_score = 0.00;
    char earned_grade;
    bool score_input = true;
    int assignment = 1;
    
    // Vector to store all assignment scores
    std::vector<float> assignment_scores;

    // Display greeting
    displayGreeting();

    // Welcome message
    std::cout << "Welcome to [YOUR NAME]'s Grade Calculator for COSC 1437\n\n";

    // Get total course points
    std::cout << "Grading Scheme Setup\n";
    std::cout << "====================\n";
    std::cout << "Please input the Total Points Possible: ";
    std::cin >> total_course_points;
    std::cout << '\n';

    // Get grade thresholds using for loop
    for (char grade = 'A'; grade <= 'D'; grade++) {
        std::cout << "Please input the Minimum Points for a '" << grade << "': ";
        if (grade == 'A') {
            std::cin >> A_points;
        } else if (grade == 'B') {
            std::cin >> B_points;
        } else if (grade == 'C') {
            std::cin >> C_points;
        } else if (grade == 'D') {
            std::cin >> D_points;
        }
        std::cout << '\n';
    }

    // Calculate percentages
    A_percentage = (A_points / total_course_points) * 100;
    B_percentage = (B_points / total_course_points) * 100;
    C_percentage = (C_points / total_course_points) * 100;
    D_percentage = (D_points / total_course_points) * 100;

    // Display the grading scheme
    std::cout << "The Grading Scheme You Input\n";
    std::cout << "============================\n";
    std::cout << "Total Points Possible in the Course: " << total_course_points << '\n';
    std::cout << "Points needed for an 'A': " << A_points << " or " << A_percentage << "%\n";
    std::cout << "Points needed for a 'B': " << B_points << " or " << B_percentage << "%\n";
    std::cout << "Points needed for a 'C': " << C_points << " or " << C_percentage << "%\n";
    std::cout << "Points needed for a 'D': " << D_points << " or " << D_percentage << "%\n";

    // Multiple Assignment Input
    std::cout << "\nGrade Calculation\n";
    std::cout << "=================\n";
    std::cout << "You will be prompted to input scores for all assignments.\n";
    std::cout << "(Input a negative number to cease input and calculate letter grade.)\n\n";

    do {
        std::cout << "Please input the points earned for Assignment " << assignment << ": ";
        std::cin >> assignment_score;
        
        if (assignment_score >= 0) {
            assignment_scores.push_back(assignment_score);  // Store in vector
            total_points_earned += assignment_score;
            assignment++;
        } else {
            score_input = false;
        }
    } while (score_input);

    // Display all scores entered
    std::cout << "\nScores Entered\n";
    std::cout << "==============\n";
    for (size_t i = 0; i < assignment_scores.size(); ++i) {
        std::cout << "Assignment " << (i + 1) << ": " << assignment_scores[i] << '\n';
    }

    // Determine the final grade
    if (total_points_earned >= A_points) {
        earned_grade = 'A';
    }
    else if (total_points_earned >= B_points) {
        earned_grade = 'B';
    }
    else if (total_points_earned >= C_points) {
        earned_grade = 'C';
    }
    else if (total_points_earned >= D_points) {
        earned_grade = 'D';
    }
    else {
        earned_grade = 'F';
    }

    // Calculate percentage
    total_percentage_earned = (total_points_earned / total_course_points) * 100;

    // Display results
    std::cout << "\nFinal Results\n";
    std::cout << "=============\n";
    std::cout << "Total Points Earned: " << total_points_earned << '\n';
    std::cout << "Total Points Possible: " << total_course_points << '\n';
    std::cout << "Total Percentage: " << total_percentage_earned << "%\n";
    std::cout << "Total Percentage (rounded): " << round(total_percentage_earned) << "%\n";
    std::cout << "Final Letter Grade: " << earned_grade << '\n';

    return 0;
}
```

---

## Running the Program

### Compile

```bash
g++ -std=c++17 -o grade_calc main.cpp greeting.cpp
```

### Run

```bash
./grade_calc
```

### Example Session

```
Good afternoon!

Welcome to John Smith's Grade Calculator for COSC 1437

Grading Scheme Setup
====================
Please input the Total Points Possible: 1000

Please input the Minimum Points for a 'A': 900

Please input the Minimum Points for a 'B': 800

Please input the Minimum Points for a 'C': 700

Please input the Minimum Points for a 'D': 600

The Grading Scheme You Input
============================
Total Points Possible in the Course: 1000
Points needed for an 'A': 900 or 90%
Points needed for a 'B': 800 or 80%
Points needed for a 'C': 700 or 70%
Points needed for a 'D': 600 or 60%

Grade Calculation
=================
You will be prompted to input scores for all assignments.
(Input a negative number to cease input and calculate letter grade.)

Please input the points earned for Assignment 1: 95
Please input the points earned for Assignment 2: 88
Please input the points earned for Assignment 3: 92
Please input the points earned for Assignment 4: 78
Please input the points earned for Assignment 5: -1

Scores Entered
==============
Assignment 1: 95
Assignment 2: 88
Assignment 3: 92
Assignment 4: 78

Final Results
=============
Total Points Earned: 353
Total Points Possible: 1000
Total Percentage: 35.3%
Total Percentage (rounded): 35%
Final Letter Grade: F
```

---

## Concepts Summary

| Part | Concepts Covered |
|------|------------------|
| 1 | Program structure, cout |
| 2 | Variables, data types, cin |
| 3 | for loops, while loops, do-while |
| 4 | Arithmetic, cmath library |
| 5 | if/else if/else, comparisons |
| 6 | Functions, headers, separate compilation |
| 7 | Vectors, push_back, size, iteration |
| 8 | Integration, final output |

---

## Common Mistakes to Avoid

| Mistake | Solution |
|---------|----------|
| Forgetting `#include <vector>` | Add at top of main.cpp |
| Using `int` for loop with `size()` | Use `size_t` type |
| Forgetting to compile greeting.cpp | Include in g++ command |
| Missing header guards | Always use `#ifndef`/`#define`/`#endif` |
| Division by zero | Validate total_course_points > 0 |

---

## Submission Requirements

Your submission must include these three files:

1. **main.cpp** - Contains the main program with:
   - All required includes
   - Variable declarations
   - Grading scheme input
   - Vector for score storage
   - Score input loop using do-while
   - Score display using for loop
   - Grade calculation
   - Final output

2. **greeting.h** - Contains:
   - Header guards
   - Function declaration for `displayGreeting()`

3. **greeting.cpp** - Contains:
   - Implementation of `displayGreeting()`
   - Time-based greeting logic

---

## Grading Rubric

| Requirement | Points |
|-------------|--------|
| Program compiles without errors | 10 |
| greeting.h with proper header guards | 10 |
| greeting.cpp with time-based greeting | 10 |
| Grading scheme input works | 15 |
| Vector declaration and usage | 15 |
| Score storage with push_back | 15 |
| Score display with for loop | 10 |
| Final grade calculation | 10 |
| Clean, formatted output | 5 |
| **Total** | **100** |

---

## What You Learned

In this lab, you:
- ✅ Created a multi-file C++ program
- ✅ Used variables, input/output, and arithmetic
- ✅ Implemented loops (for, while, do-while)
- ✅ Used conditional statements for decisions
- ✅ Created and used functions with header files
- ✅ Used vectors for dynamic data storage
- ✅ Iterated through vectors with loops

---

## Next Steps

In **Lab 12**, you'll add the `<algorithm>` library to find the highest and lowest scores using STL functions!

# COSC 1437: Grade Calculator Portfolio Project

Welcome to **COSC 1437 - Programming Fundamentals II**! In this course, you'll continue building the Grade Calculator application, adding advanced features like file I/O, object-oriented programming, templates, and exception handling.

## 🎯 Course Overview

This portfolio project spans **Labs 11-22**, building on foundational C++ concepts to create a professional-grade application.

| Lab | Topic | Key Concepts |
|-----|-------|--------------|
| 11 | Vectors & Complete Setup | `std::vector`, program structure |
| 12 | STL Algorithms | `min_element`, `max_element` |
| 13 | File I/O | `ifstream`, `ofstream`, persistence |
| 14 | Custom Objects | Classes, constructors, methods |
| 15 | Fine-Tuning Objects | Header/implementation separation, encapsulation |
| 16 | Menu System | `iomanip`, formatted output, user interface |
| 17 | Inheritance | Base/derived classes, polymorphism |
| 18 | Input Validation | Error handling, robust input |
| 19 | Templates | Generic programming, type parameters |
| 20 | Lambdas & STL | Lambda functions, algorithms |
| 21 | Associative Containers | `std::map`, user-defined categories |
| 22 | Exception Handling | try-catch, custom exceptions |

## 📁 Project Structure

```
├── Instructions/           # Lab instructions (Lab11-Lab22)
├── main.cpp               # Main program file
├── greeting.h             # Greeting function header
├── greeting.cpp           # Greeting function implementation
├── Assignment.h           # (Lab 14+) Assignment class
├── Assignment.cpp         # (Lab 15+) Assignment implementation
├── GradedItem.h          # (Lab 17+) Base class for graded items
├── Homework.h            # (Lab 17+) Homework derived class
├── Quiz.h                # (Lab 17+) Quiz derived class
├── Exam.h                # (Lab 17+) Exam derived class
├── InputHelper.h         # (Lab 18+) Input validation utilities
├── MathHelper.h          # (Lab 19+) Template math functions
├── Category.h            # (Lab 21+) Category struct for maps
├── Exceptions.h          # (Lab 22+) Custom exception classes
├── FileManager.h         # (Lab 22+) File operations
└── .github/classroom/    # Autograding configuration
```

## 🚀 Getting Started

### For Students New to the Grade Calculator

If you haven't completed COSC 1436, start with **Lab 11** which provides a comprehensive introduction that builds the complete foundation.

### For Students Continuing from COSC 1436

Your Lab 12 completion state is the starting point. Begin with **Lab 13** to add file persistence.

## 💻 Compilation

As you progress through the labs, your compilation command will grow:

```bash
# Labs 11-14
g++ -std=c++17 -o grade_calc main.cpp greeting.cpp

# Labs 15-16
g++ -std=c++17 -o grade_calc main.cpp greeting.cpp Assignment.cpp

# Labs 17-22 (header-only classes)
g++ -std=c++17 -o grade_calc main.cpp greeting.cpp
```

## 📋 How Labs Work

1. **Read the Instructions** - Find your current lab in the `Instructions/` folder
2. **Find the TODOs** - Look for `// TODO: Lab XX` comments in the code
3. **Implement the Feature** - Follow the instructions to complete the task
4. **Test Your Code** - Run and verify your implementation
5. **Submit** - Commit and push to trigger autograding

## 🏆 Grading

Each lab is worth 100 points, assessed through automated tests that check:
- Successful compilation
- Required files exist
- Correct program behavior
- Expected output

## 📚 Resources

- [C++ Reference](https://en.cppreference.com/)
- [Halterman C++ Textbook](http://python.cs.southern.edu/cppbook/progcpp.pdf)
- StudySite.ai AI Tutor (available in the coding environment)

---

Good luck with your Grade Calculator! 🎓

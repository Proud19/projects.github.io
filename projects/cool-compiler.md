# Cool Compiler (CS 143 - Compilers)
This is a description of a Cool compiler project done as part of CS 143 (Compilers) at Stanford University. The compiler consists of several stages: lexical analysis, syntax analysis, semantic analysis, and code generation. The final output is MIPS assembly code that implements the given Cool program. 

**NB: The repository for this project is private as per the Stanford University requirements as it contains potential solutions to assignments**

## Table of Contents
1. [Overview](#overview)
2. [Phases of the Compiler](#phases-of-the-compiler)
    - [Lexical Analysis](#lexical-analysis)
    - [Syntax Analysis (Parsing)](#syntax-analysis-parsing)
    - [Semantic Analysis](#semantic-analysis)
    - [Code Generation](#code-generation)
3. [Runtime System Integration](#runtime-system-integration)
4. [Testing and Debugging](#testing-and-debugging)
5. [Final Submission](#final-submission)
6. [Conclusion](#conclusion)

## Overview
The Cool compiler takes a source program written in the Cool programming language and generates MIPS assembly code that implements the program. The compiler performs the following steps:
1. **Lexical Analysis**: Tokenizes the input program.
2. **Syntax Analysis**: Parses the tokenized input into an Abstract Syntax Tree (AST).
3. **Semantic Analysis**: Checks for semantic errors and ensures type correctness.
4. **Code Generation**: Translates the AST into MIPS assembly code.

The final MIPS code, when executed using the SPIM simulator, produces the output specified by the Cool program.

## Phases of the Compiler

### Lexical Analysis
In this phase, the input Cool source code is converted into a sequence of tokens. This is done by the lexer, which reads the program character by character and classifies sequences of characters into token types like keywords, identifiers, operators, and literals.

#### Key Steps:
- Implemented the lexer using regular expressions to match patterns for Cool keywords, identifiers, integers, booleans, and operators.
- The lexer outputs a sequence of tokens, which are passed to the parser for syntax analysis.

### Syntax Analysis (Parsing)
The syntax analysis phase parses the tokenized input and generates an Abstract Syntax Tree (AST). The AST is a hierarchical representation of the program structure, where each node represents a construct in the program (e.g., an expression, statement, class, etc.).

#### Key Steps:
- Used a recursive descent parser to handle the Cool language's grammar, which was specified in the Cool Reference Manual.
- The parser handles constructs such as class definitions, method declarations, expressions, and control structures.
- The output of this phase is the AST, which is passed to the semantic analyzer.

### Semantic Analysis
Semantic analysis checks for logical errors in the program, such as type mismatches, uninitialized variables, and invalid method calls. This phase uses the type environment to ensure that the types of variables, expressions, and method calls are valid according to Cool’s type system.

#### Key Steps:
- Built a symbol table to store information about classes, methods, and variables.
- Implemented the type checker to ensure that method calls, variable accesses, and expressions adhere to Cool's typing rules.
- Checked for semantic errors, such as method calls on non-objects or void values, and reported them.

### Code Generation
The code generation phase translates the AST into MIPS assembly code, which can be executed on the SPIM simulator. The generated code performs the operations described by the AST, following Cool's operational semantics as outlined in the Cool Reference Manual.

#### Key Steps:
- The code generator performs two passes: one to determine the object layout and another to generate the corresponding MIPS instructions.
- The first pass assigns memory offsets for each class’s attributes and methods.
- The second pass generates the MIPS assembly instructions for expressions, method calls, and class initialization.

#### Key Concepts:
- Implemented functions for generating MIPS code for basic constructs like integers, booleans, and strings.
- Handled method dispatch, including support for the dispatch tables and runtime checks for errors like dispatching on void.
- Generated MIPS code for each method, ensuring that it adheres to the calling conventions specified in the Cool Runtime Manual.

### Runtime System Integration
The Cool compiler integrates with the runtime system to provide necessary functionalities such as garbage collection, runtime checks, and object management. The runtime system supports operations like method dispatch, heap allocation, and type checking.

#### Key Steps:
- Integrated the garbage collector into the code generation phase, ensuring that the generated MIPS code works correctly with Cool’s generational garbage collector.
- Ensured that the generated code handles runtime errors, such as dispatching on void and performing invalid case expressions.
- Used predefined runtime functions like `print_string`, `abort`, and `dispatch_error` to handle errors and garbage collection.

## Testing and Debugging
Testing and debugging were critical to ensure the correctness of the code generator. The following approaches were used:

- **Unit Testing**: We wrote several example Cool programs to test the correctness of the code generator. These tests covered different constructs such as class definitions, method calls, and expressions.
- **SPIM Simulator**: The generated MIPS code was tested using SPIM, a MIPS simulator. We used SPIM to check the execution of the generated code and compare it to the expected output.
- **GDB Debugging**: We used GDB to debug the code generator itself. Setting breakpoints allowed us to inspect intermediate results and ensure that the MIPS code was being generated correctly.
- **Edge Case Testing**: We tested edge cases such as dispatching on void, division by zero, and out-of-bounds array accesses to ensure the runtime system properly handled errors.

To submit, we used the provided `make submit` command, which packaged our files for submission.

## Conclusion
This project was a challenging but rewarding experience. It provided a deep understanding of compiler construction and the interaction between various compiler phases, such as lexical analysis, syntax parsing, semantic analysis, and code generation. We successfully generated MIPS assembly code that implements Cool programs, integrating it with the runtime system and ensuring correct error handling and garbage collection.

We are proud of the work done and look forward to further exploring compiler design in future projects.

---

**Authors:**
- Proud Mpala
- [Ritvik Sharma](https://github.com/Ritvik1sharma)

**Stanford University, CS 143 - Compilers**

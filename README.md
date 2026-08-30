# HerbLang 🌱

**HerbLang** is a nature-inspired symbolic programming language developed as a project for the **Programming Languages and Paradigms** course.

The language models computation through natural processes such as **growth, flow, decay, and division**. It uses nature-based entities such as `seed`, `grow`, `cut`, `split`, `flower`, `leaf`, `tree`, and `root` to give conceptual meaning to arithmetic operations.

A key feature of HerbLang is its **repetition-based operator syntax**, where the number of repeated operator symbols determines how many times an operation is applied.

For example:

```text
seed 5 +++> 3 flower
```

represents:

```text
5 + 3 + 3 + 3 = 14
```

---

## 📚 Course

**Programming Languages and Paradigms**

**Project:** HerbLang

---

## 👥 Team Members

* Amira Khezzar — U23104100
* Hasna Imad Eldin Abdul Hay — U23100997
* Fatma A. S. Alkhodari — U22104519
* Mona M. M. Mansour — U22104988
* Fatma Ibrahim Khammas — U23101181

**Instructor:** Dr. Imad Afyouni

---

## 🌿 Concept Overview

HerbLang combines programming concepts with natural metaphors.

The language represents arithmetic transformations using nature-inspired entities:

| Entity   | Meaning                                    |
| -------- | ------------------------------------------ |
| `seed`   | Initial value                              |
| `grow`   | Increasing / multiplication transformation |
| `cut`    | Decreasing / subtraction transformation    |
| `split`  | Division / branching                       |
| `flower` | Result of growth / addition                |
| `leaf`   | Result of reduction / subtraction          |
| `tree`   | Result of multiplication                   |
| `root`   | Result of division                         |

The language is designed around three main goals:

1. **Semantic alignment** — operations should have meaning beyond mathematical symbols.
2. **Repetition as syntax** — repeated operators directly express repeated operations.
3. **Engagement through metaphor** — nature-based entities make programming more intuitive and engaging.

---

## ✨ Features

### Arithmetic Expressions

HerbLang supports:

* Addition
* Subtraction
* Multiplication
* Division

The number of operator symbols determines the number of repetitions.

### Examples

```text
seed 5 +> 3 flower
```

Result:

```text
8
```

```text
seed 5 ++> 3 flower
```

Result:

```text
11
```

```text
seed 5 +++> 3 flower
```

Result:

```text
14
```

```text
cut 10 --> 2 leaf
```

Result:

```text
6
```

```text
grow 2 **> 3 tree
```

Result:

```text
18
```

```text
split 81 //> 3 root
```

Result:

```text
9
```

---

## 🌱 Built-in Functions

HerbLang provides nature-themed built-in functions that operate on lists of numbers.

| Function    | Description                               | Example                          |
| ----------- | ----------------------------------------- | -------------------------------- |
| `propagate` | Duplicates the list                       | `propagate [1,2,3]`              |
| `harvest`   | Returns the sum                           | `harvest [1,2,3]` → `6`          |
| `bloom`     | Returns the maximum                       | `bloom [3,1,5,2]` → `5`          |
| `wither`    | Returns the minimum                       | `wither [3,1,5,2]` → `1`         |
| `average`   | Returns the arithmetic mean               | `average [2,4,6]` → `4.0`        |
| `sort`      | Sorts the list in ascending order         | `sort [3,1,4]` → `[1,3,4]`       |
| `uproot`    | Reverses the list                         | `uproot [1,2,3]` → `[3,2,1]`     |
| `unique`    | Removes duplicates while preserving order | `unique [1,2,1,3]` → `[1,2,3]`   |
| `flourish`  | Keeps elements greater than a threshold   | `flourish [5,2,8,1] 4` → `[5,8]` |

---

## 🧩 Programming Paradigm

HerbLang follows the **functional programming paradigm**, even though the implementation is written in Python 3.

The project demonstrates several functional programming concepts:

### Immutability

Values are not modified. Instead, new values are produced.

### Pure Functions

Operations produce the same output for the same input without side effects.

### Recursion

Repetition is implemented using recursion rather than traditional loops.

### First-Class Functions

Functions can be passed as arguments and returned as values, supporting higher-order operations.

### Referential Transparency

An expression can be replaced by its value without changing the program's behavior.

---

## ⚙️ Implementation

HerbLang is implemented using **Python 3**.

The implementation consists of four main components:

```text
Source Code
     ↓
   Lexer
     ↓
   Parser
     ↓
    AST
     ↓
 Interpreter
     ↓
   Result
```

### 1. Lexer

The lexer/tokenizer reads the source code and converts it into a sequence of tokens.

HerbLang uses regular expressions to recognize:

* Keywords
* Numbers
* Operators
* Arrows
* Brackets
* Commas

Example:

```text
seed 5 +++> 3 flower
```

is tokenized into:

```text
START  seed
NUM    5
OP     +
OP     +
OP     +
ARROW  >
NUM    3
END    flower
```

### 2. Parser

The parser verifies that the token sequence follows the grammar of HerbLang.

It uses a **recursive-descent parsing strategy**.

The parser supports:

* Arithmetic expressions
* Function calls
* Entity matching
* Syntax error reporting

### 3. Abstract Syntax Tree (AST)

The parser produces a compact AST representation.

For example:

```text
seed 5 +++> 3 flower
```

becomes:

```text
('ADD', 5, 3, 3)
```

Function calls are represented using:

```text
('FUNC', name, args, extra)
```

### 4. Interpreter

The interpreter evaluates the AST and produces the final result.

Arithmetic operations use recursive helper functions.

For example:

```text
seed 5 +++> 3 flower
```

is evaluated recursively as:

```text
5 → 8 → 11 → 14
```

---

## 📖 Context-Free Grammar

The language syntax is defined using a **Context-Free Grammar (CFG)**.

The main production rules include:

```text
<program> → <statement>

<statement> → <arith_expr> | <func_call>

<arith_expr> →
    <entity_open> <number> <op_seq> > <number> <entity_close>

<entity_open> → seed | cut | grow | split

<entity_close> → flower | leaf | tree | root

<op_seq> → <op> | <op> <op_seq>

<op> → + | - | * | /

<func_call> →
    <func_name> [ <arg_list> ]
    | flourish [ <arg_list> ] <number>
```

The parser also enforces entity-pairing constraints:

```text
seed  → flower
cut   → leaf
grow  → tree
split → root
```

---

## 🌳 Abstract Syntax Tree Examples

| HerbLang Expression    | AST                                  |
| ---------------------- | ------------------------------------ |
| `seed 5 +++> 3 flower` | `('ADD', 5, 3, 3)`                   |
| `seed 5 +> 3 flower`   | `('ADD', 5, 1, 3)`                   |
| `cut 10 --> 2 leaf`    | `('SUB', 10, 2, 2)`                  |
| `grow 2 **> 3 tree`    | `('MUL', 2, 2, 3)`                   |
| `split 12 //> 3 root`  | `('DIV', 12, 2, 3)`                  |
| `harvest [1,2,3]`      | `('FUNC', 'harvest', [1,2,3], None)` |
| `sort [3,1,4]`         | `('FUNC', 'sort', [3,1,4], None)`    |

---

## 🧮 Mathematical Semantics

For an expression of the form:

```text
<entity₁><n₁> <operator_seq> > <n₂><entity₂>
```

the number of operator symbols is represented by `k`.

The operations are defined as:

### Addition

```text
n₁ + (k × n₂)
```

### Subtraction

```text
n₁ - (k × n₂)
```

### Multiplication

```text
n₁ × (n₂^k)
```

### Division

```text
n₁ ÷ (n₂^k)
```

---

## 📝 Example Programs

### Arithmetic

```text
seed 5 +++> 3 flower
```

Output:

```text
14
```

### List Functions

```text
harvest [10,20,30]
```

Output:

```text
60
```

```text
bloom [7,2,9,4]
```

Output:

```text
9
```

```text
sort [5,3,8,1,4]
```

Output:

```text
[1,3,4,5,8]
```

```text
unique [1,1,2,3,2,4]
```

Output:

```text
[1,2,3,4]
```

```text
flourish [1,5,3,9,2] 3
```

Output:

```text
[5,9]
```

---

## ⚠️ Current Limitations

The current version of HerbLang has several limitations:

* Only addition, subtraction, multiplication, and division are supported.
* There are no variables.
* Parentheses and operator precedence are not supported.
* There is no control flow such as `if`, `while`, or `for`.
* The language has limited data-type support.
* User-defined functions are not supported.
* Error messages are minimal.
* The implementation operates interactively through the REPL and does not currently support file input.

---

## 🚀 Future Work

Possible future improvements include:

1. Variable assignment and lookup
2. Parentheses and operator precedence
3. User-defined functions
4. Additional data types such as strings and Booleans
5. Better error reporting with line numbers
6. File input support
7. Control-flow constructs such as `if` and `while`
8. Implementation of the reserved `prune` and `absorb` functions

---

## 📂 Project Documentation

This repository contains the project documentation:

* **Final Report** — detailed explanation of HerbLang, its grammar, semantics, lexer, parser, AST, interpreter, examples, limitations, and future work.
* **Presentation** — project presentation covering the language concept, syntax, semantics, implementation architecture, grammar, lexer, AST, and interpreter.

---

## 🎓 Academic Project

HerbLang was developed as part of the **Programming Languages and Paradigms** course in the **Computer Science Department, College of Computing and Informatics**.

---

## 📌 Project Summary

HerbLang demonstrates how the concepts studied in programming languages can be applied to the design and implementation of a small programming language.

The project covers:

* Language design
* Syntax design
* Functional programming
* Context-Free Grammar
* Lexical analysis
* Parsing
* Abstract Syntax Trees
* Semantics
* Interpretation
* Recursion
* Built-in functions

---

**HerbLang 🌱 — Programming through the language of nature.**

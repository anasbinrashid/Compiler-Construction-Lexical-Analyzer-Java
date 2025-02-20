# Lexical Analyzer for Custom Programming Language

## Introduction
This project is a lexical analyzer for a custom programming language, implemented in Java using regular expressions and data structures. The analyzer classifies tokens into different categories, including keywords, datatypes, variables, operators, and symbols. It also detects lexical errors and maintains a symbol table. The project was developed using **ECLIPSE IDE**.

## Features
- Tokenization of a custom programming language
- Identification of valid **keywords, operators, and identifiers**
- Detection of **lexical errors**
- Maintenance of a **symbol table**
- Handling of **single-line and multi-line comments**
- Support for **scope-based variable classification (Global & Local)**

## Setup & Compilation
### Prerequisites
- Java Development Kit (JDK) 8 or later
- Eclipse IDE
- A terminal or command prompt for running the Java program

## File Structure
- **`Automaton.java`** - Defines deterministic finite automata (DFA) rules and generates Transition State Table.
- **`LexicalAnalyzer.java`** - Handles tokenization and classification of input code.
- **`SymbolTable.java`** - Maintains and displays the symbol table.
- **`ErrorHandler.java`** - Stores and displays lexical errors.

## Language Syntax & Rules

### Keywords
| Keyword           | Description              |
|-------------------|--------------------------|
| int          | `123`         |
| decimal   | `12.34567`      |
| char        | `'A'`         |
| bool         | `true`, `false` |
| string         | `"I am a Student"` |
| if          | Conditional Structure    |
| else   | Conditional Structure     |
| return        | Function Return        |

### Variable Naming Rules
- Must only contain **lowercase** letters.
- Example: `var`, `counter`

### Operators
| Operator  | Meaning         |
|----------|----------------|
| +      | Addition       |
| -      | Subtraction    |
| *      | Multiplication |
| /      | Division       |
| %      | Modulus        |
| ^      | Exponent       |
| &&      | AND     |
| !      | NOT     |
| >      | Greater      |
| <      | Less     |
| >=      | Greater Equal     |
| <=      | Less Equal     |
| ==      | Equal     |
| !=      | Not Equal     |
| =      | Assignment     |

### Delimiters
| Type             | Symbol     | Example |
|-----------------|-----------|---------|
| Parentheses     | `()`      | `(x + y)` |
| Curly Braces    | `{}`      | `{ code }` |
| Semi-Colon    | `;`      | `code;` |
| Comma    | `,`      | `value1, value2` |

### Comments
| Type             | Symbol     | Example |
|-----------------|-----------|---------|
| Single-Line Comment | `//` | `// This is a comment` |
| Multi-Line Comment | `/* */` | `/* This is a comment */` |

## Example Program
```

int counter = 100;             
decimal value = 123.45678;      
bool flag = 7;               
char letter = 'a';   
           
int main()
{
	int sum = counter + 50;         
	int diff = counter - 30;       
	decimal prod = value * 2;       
	decimal quot = value / 2;       
	int modResult = counter % 3;    
	int powerint = 2^3;             
	decimal powerDec = value^2;     
  	 int    spaced    =     42   ;

	/*
   	 This is a multi-line comment.
    	 It includes extra spaces, blank lines, and even symbols.
    
   	 Make sure the lexer properly ignores all of this.
	*/

	if (counter > 50) {
    		int localvar = counter + 10;
    		write("Local variable value: " + localvar);
    		// in if
    		if (flag == true) {
        		decimal nestedval = 0.00001;   
        		write("Nested local decimal: " + nestedval);
    		}
	}

	int Invalid = 5;  
	bool 12re = 3;

	int user_input = read("Enter a number: ");
	write("You entered: " + userinput);
}

```

## How It Works

### **1. Tokenization (Lexical Analysis)**
- The program reads the source code **line by line**, breaking it down into individual tokens.
- Tokens are categorized into **keywords, datatypes, identifiers, operators, delimiters, numbers, and comments**.
- **Whitespace and comments are ignored**, ensuring they do not interfere with tokenization.

### **2. Symbol Table Construction**
- A **symbol table** is created to store relevant information about variables, functions, and constants in the program.
- Each valid identifier (variable or function) is recorded along with its **datatype, scope (global/local), and memory location**.
- The symbol table helps with **semantic analysis** later in compilation and assists with **error detection**.

### **3. Operator and Delimiter Identification**
- The lexical analyzer detects **operators and delimiters** using predefined symbol lists.
- Operators such as `+`, `-`, `*`, `/`, `%`, and `^` are recognized as **arithmetic operators**.
- Operators like `>`, `<`, `>=`, `<=`, `==`, `!=`, `&&`, and `!` are classified as **relational and logical operators**.
- Delimiters including **brackets, parentheses, semicolons, and commas** are properly categorized to maintain correct syntax structure.

### **4. Handling Comments**
- **Single-line comments (`//`)**: Everything after `//` on a line is ignored.
- **Multi-line comments (`/* */`)**: The analyzer ensures that everything between `/*` and `*/` is ignored, regardless of how many lines it spans.
- Proper handling of comments prevents unnecessary parsing and helps in code readability.

### **5. Error Detection and Handling**
- The program detects **lexical errors** such as:
  - **Invalid identifiers** (e.g., variable names starting with numbers)
  - **Unrecognized symbols** that do not belong to the defined syntax
  - **Missing tokens** such as an unclosed string (`"hello` without `"`), or unclosed comments (`/*` without `*/`)
- Detected errors are **logged into the `ErrorHandler`**, and error messages are displayed to the user.

### **6. Processing Keywords and Identifiers**
- **Keywords** are stored in a predefined list and checked against tokens to differentiate them from identifiers.
- **Identifiers** (variable and function names) are validated using **naming conventions** (e.g., lowercase letters for variable names).

### **7. Numeric Literal Recognition**
- The lexical analyzer differentiates between:
  - **Integer literals** (e.g., `123`)
  - **Decimal literals** (e.g., `12.34567`)
  - **Character literals** (e.g., `'A'`)
  - **Boolean literals** (`true`, `false`)
- Invalid numeric formats (e.g., `12..34`, `123a`) are flagged as lexical errors.

### **8. Transition Table Generation**
- After processing the input code, a **state transition table** is generated to represent how the DFA transitions between states during lexical analysis.
- The transition table is displayed as output, providing a clear visualization of how tokens were classified.

### **9. Output Display**
- **Symbol Table**: Displays all valid identifiers along with their attributes (type, scope, etc.).
- **Lexical Errors**: Lists any errors encountered during analysis.
- **State Transition Table**: Shows the DFA transitions for token recognition.

### **10. Integration with Other Phases**
- The lexical analyzer serves as the **first phase** of a compiler.
- The generated tokens and symbol table can be used for **syntax analysis (parsing)** and **semantic analysis** in later stages of compilation.

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
1. **Tokenization:** The program reads the source code line by line and splits it into tokens.
3. **Symbol Table:** Recognized tokens are stored in the `SymbolTable`.
4. **Error Detection:** Unrecognized tokens and incorrect syntax are stored in the `ErrorHandler`.
5. **Output Display:** The program prints the **symbol table** and **lexical errors** if any.
6. **Transition Table:** The final State Transition Table is then displayed.

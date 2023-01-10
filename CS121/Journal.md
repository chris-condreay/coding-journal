# Coding Journal
## Name: Chris Condreay
## Reading / Lab: Module 1
## Entries:
### January 8th, 2023

## 1.1 Programming

### Basic Instruction Types
- Input
- Process
- Output

## 1.2 Programming Basics

### Simple Java
- A program starts in main(), executing the statements within main's braces {}

      public class Salary {

        public static void main(String[] args) {
          int wage;

          wage = 20;

          // output: Salary is 41600

          System.out.print("Salary is ");
          System.out.println(wage * 40 * 52); // 20 * 40 * 52
        }
      }

### Basic Input
- The following code at the top of the file enables the program to get input:
      import java.util.Scanner;
- A Scanner is a text parser that can get numbers, words, or phrases from an input source
- Getting input is by first creating a Scanner object via statement:
      Scanner scnr = new Scanner(System.in);
- the following statement gets an input value and assigns x with that value: x = scnr.nextint();

      import java.util.Scanner;

      public class Salary {
        public static void main(String[] args) {
          int wage;

          Scanner scnr = new Scanner(System.in);
          // scnr.nextInt() get an input value from keyboard and puts into wage variable
          wage = scnr.nextInt();

          System.out.print("Salary is ");
          System.out.println(wage * 40 * 52);
          // wage's value can be used in subsequent processing and outputs
        }
      }

### Basic output: Text
- Outputting text is achieved by 
      System.out.print("desired text");
and is known as a string literal
- System.out.println starts a new output line after the outputted values, called a newline
- Programmers commonly use a single output statement for each line of output by combining the outputting of text, variable values, and a new line

## 1.3 Comments and Whitespace

### Comments
- A comment is text a programmer adds to code, to be rad by humans to better understand teh code but ignored by the compiler
- Two common kinds of comments are:
  - Single-line comment: starts with // and includes all the following text on that line. They commonly appear after a statement on the same line
  - Multi-line comment(block comment): starts with /* and ends with */, where all the text within those symbols are part of the comment

  Invalid comments:
      // Print "Hello"
        Then print "Goodbye"
        And finally return.
      //

      /* 
        numKids = 2;  /* Typical number */
        numCars = 5;
      */

  Valid comments:
      // Get user input

      /* Get user input */

      /* Determine width and height,
        calculate volume, 
        and return volume squared.
      */

      // Print "Hello" to the screen //

      /*
      * Author: Michelangelo
      * Date: 2014
      * Address: 111 Main St, Pacific Ocean
      */

      // numKids = 2;  // Typical number

      /* 
        numKids = 2;  // Typical number
        numCars = 5; 
      */

### Whitespace
- Whitespace refers to blank spaces between items within a statement and blank lines between statements
  * Deliberately adn consistently use whitespace to make a program more readable
- Programmers usually follow conventions defined by their company, team, instructor such as:
  - Use blank lines to separate conceptually distinct statements
  - Indent lines the same amount
  - Align items to reduce visual clutter
  - Use a single space before and after any operators like =,+,*, or / to make statements more readable

  #### Good use of whitespace
      import java.util.Scanner;

      public class WhitespaceEx {
        public static void main(String[] args) {
            Scanner scnr = new Scanner(System.in);
            int myFirstVar;    // Aligned comments yield less
            int yetAnotherVar; // visual clutter
            int thirdVar;

            // Above blank line separates variable declarations from the rest
            System.out.print("Enter a number: ");
            myFirstVar = scnr.nextInt();

            // Above blank line separates user input statements from the rest
            yetAnotherVar = myFirstVar;        // Aligned = operators
            thirdVar      = yetAnotherVar + 1; 
            // Also notice the single-space on left and right of + and =
            // (except when aligning the second = with the first =)

            System.out.println("Final value is " + thirdVar); // Single-space on each side of +
        }
      }

  #### Bad use of whitespace
      import java.util.Scanner;
      public class PastaCalculator {
      public static void main (String [] args) {
      Scanner scnr = new Scanner(System.in);int numPeople;int totalOuncesPasta;
      System.out.println("Enter number of people:");
      numPeople = scnr.nextInt(); totalOuncesPasta = numPeople * 3; 
      System.out.println("Cook "+totalOuncesPasta+" ounces of pasta.");}}
  
- Spaces are not always ignored by the compiler

## 1.5 Error and warnings

### Syntax errors 


# Coding Journal
## Name: Chris Condreay
## Reading / Lab: Module 2
## Entries:
### January 25th, 2023

#### Variables and assignments

A **variable** is a named item, such as x or numPeople, used to hold a value

An **assignment** assigns a variable with a value, such as x = 5
- = is an assignment of a left-side variable with a right-side value

#### Assignments with variable on left and right

Increasing a variable's value by 1, as in x = x + 1, is common, and known as **incrementing** the variable

#### Variable declarations

A **variable delaration** is a statement that declares a new variablem, specifying the variable's name and type

#### Assingment statements

An **assignment statement** assigns the variable on the left-side of the = with the current value of the right side expression. Ex: numApples = 8

An **expression** may be a number like 80, a variable name like numApples, or a simple calculation like numApples + 1

#### Common errors

A common error is to read a variable that has not yet been assigned a value

## 2.3 Indentifiers

#### Rules for indentifiers

A name created by a programmer for an item like a variable or method is called an **identifier**. Identifiers must:
  - be a sequence of letters (a-z, A-Z), underscore (_), dollar signs ($), and digits (0-9)
  - start with a letter, underscore, or dollar sign

Indentifiers are case sensitive, meaning upper and lower cased letters differ

A **reserved word** is a word that is part of the language, like int, short, or double. A reserved word is also known as a keyword
  - Programmers cannot use a rserved word as an identifier

#### Style guidelines for identifiers

**Lower camel case** abuts multiple words, capitalizing each word except the first, as in numApples or peopoleOnBus.

## 2.4 Arithmetic expressions
#### Basics

An **expression** is any individual item or combination of items, like variables, literals, operators, and parenthesis, that evaluates to a value, like 2 * (x + 1)

a **literal** is a specific value in code like 2
an **operator** is a symbol that performs a build-in calculation, like +, which performs addition

An expression **evaluate**to a value, which replaces teh expression

An expression is evaluate using the order of standard mathematics, such order known in programming as **precedence rules**
  - Ex: (), urnary -, * / %, + -, left-to-right

## Arithmetic expressions (int)

    import java.util.Scanner

    /* Computes the total cost of leasing a car given the down payment,
    monthly rate, and number of months 
    */

    public class CarLeaseCost {
      public static void main(String[] args) {
          Scanner scnr = new Scanner(System.in);
          int downPayment; 
          int paymentPerMonth; 
          int numMonths;
          int totalCost; // Computed total cost to be output

            
          System.out.print("Enter down payment: ");
          downPayment = scnr.nextInt();

          System.out.print("Enter monthly payment: ");
          paymentPerMonth = scnr.nextInt();

          System.out.print("Enter number of months: ");
          numMonths = scnr.nextInt();
            
          totalCost = downPayment + (paymentPerMonth * numMonths);
            
          System.out.println("Total cost: " + totalCost);
      }
    }

- totalCost = downPayment + (paymentPerMonth * numMonths); would yield the same results removing the parenthesis because the * has higher presedence than + . Using parenthesis mkes the programmer's intent more clear to people reading the code

#### Compound operators

**compound operators** provide a shorthand way to update a variable, such as userAge += 1 being shorthand for userAge = userAge + 1

## 2.6 Example: Health data

## Calculating user's age in days 

**Incremental development** is the process of writing, compilingm and testing a small amount of code, then writing, compiling, and testing a small amount more (an incremental amount)

    import java.util.Scanner;

    public class HealthData {
      public static void main(String[] args) {
          Scanner scnr = new Scanner(System.in);
          int userAgeYears;
          int userAgeDays;
          
          System.out.print("Enter your age in years: ");
          userAgeYears = scnr.nextInt();
          
          userAgeDays = userAgeYears * 365;

          System.out.println("You are " + userAgeDays + " days old.");      
      }
    }

- The initial program above calculates a user's age in days based on the user's age in years. The assignment statement userAgeDays = userAgeYears * 365; assigns userAgeDays with the product of the user's age and 365, which does not take into account leap years.

## 2.7 Floating-point numbers (double)

## Floating-point (double) variables

A **floating-point number** is a real number containing a decimal point that can appear anywhere (or "float") in the number

A **double** variable stores a floating-point number

A **floating-point literal** is a number with a fractional part, even if the fraction is 0, as in 1.0, 0.0, or 99.573
  - Good practice is to always have a digit before the decimal point, as in 0.5, since .5 might mistakenly be viewed as 5

        import java.util.Scanner;

        public class TravelTime {
          public static void main(String[] args) {
              Scanner scnr = new Scanner(System.in);
              double milesTravel; // User input of miles to travel
              double hoursFly;    // Travel hours if flying those miles
              double hoursDrive;  // Travel hours if driving those miles

              System.out.print("Enter distance in miles: ");
              milesTravel = scnr.nextDouble();

              hoursFly   = milesTravel / 500.0;
              hoursDrive = milesTravel / 60.0;

              System.out.println(milesTravel + " miles would take:");
              System.out.println("   " + hoursFly + " hours to fly,");
              System.out.println("   " + hoursDrive + " hours to drive.");
          }
        }

#### Choosing a variable type (double vs. int)

A programmer should choose a variable's type based on the type of value held
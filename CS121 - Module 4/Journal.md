# Coding Journal
## Name: Chris Condreay
## Lab: Module 4 - Conditionals and Loops
## Entries: February 14, 2023

### 4.1 If-else Branches

#### Branch Basics(If)

A ***branch*** is a sequence of statements only executed under a certain condition

An ***if*** branch is a branch taken only IF an expression is true

#### If-else Branches
An ***if-else*** branch has two branches: The first is executed IF an expression is true, ELSE the other branch is executed

#### If-else if-else branches

Commonly a programmer wishes to take one of multiple (3 or more) branches. An if-else statement can be extended to an if-elseif-else structure

In some cases, order doesn't matter as long as one branch can have a true expression

### 4.2 Detecting equal calues with branches

#### Detecting if two items are equal using an if statement

An ***if statement*** executes a group of statements if an expression is true
  - Braces surround the if statements

***Braces*** {}, sometimes redundantly called curly braces, represent a grouping, such as a grouping of statements

The ***equality operator (==)*** evaluates to true if the left and right sides are equal

#### Equality and inequality operators

The ***inequality operator (!=)*** evaluates to true if the left and right sides are not equal, or different

- An expression involving the equality or inequality operators evaluates to a Boolean value

A ***Boolean*** is a type that has just two values: true or false

#### If-else statement

An ***if-else statement*** executes one group of statements when an expression is true, and another group of statements when the expression is false

### 4.4 Detecting ranges with branches

#### Relational operators

A ***rational operator*** checks how one operand's value relates to another, like being greater than

#### Detecting Ranges with if-else statements 
Programmers often use sequential nature of the multi-branch if-else arrangemen to detect ranges of numbers

### 4.5 Detecting ranges using logical operators

#### Logical AND, OR, and NOT (general)

A ***logical operator*** treats operands as being true or false, and evaluates to true or false
  - Logical operators include AND, OR, and NOT

        false && false = false
        false && true = false
        true && false = false
        true && true = true

        false || false = false
        false || true = true
        true || false = true
        true || true = true

        a = false a! = true
        a = true a! = false

a **AND** b is *true* when both of its operands are true
a **OR** b is *true* when at least one of its operands are true
**NOT** a is *true* when its one operand is false, and vice-versa

### 4.6 Detecting ranges with gaps

Oftentimes, ranges contain gaps like movie theaters often give ticket discounts to children(anyone 12 or under) and seniors(65 and older)

    import java.util.Scanner;

    public class MovieTicketPrices {
    public static void main(String[] args) {
        int userAge;
        int movieTicketPrice;     
        Scanner scnr = new Scanner(System.in);

        System.out.println("Enter your age: ");
        userAge = scnr.nextInt();

        if (userAge <= 12) {         // Age 12 and under
            System.out.println("Child ticket discount.");
            movieTicketPrice = 11;
        }
        else if (userAge >= 65) {    // Age 65 and older
            System.out.println("Senior ticket discount.");
            movieTicketPrice = 12;
        }
        else {                       // All other ages
            movieTicketPrice = 14;
        }

        System.out.println("Movie ticket price: $" +
            movieTicketPrice);
      }
    }

#### Ranges with gaps using logical operators

Programmers often use logical operators to explicitly detect ranges with an upper and lower bound

    if (officeNum >= 100 && officeNum <= 150)
    {
        // valid office number
    }
    else if (officeNum >= 200 && officeNum <= 250)
    {
        // valid office number
    }
    else
    {
        // invalid office number
    }

### 4.7 Detecting multiple features with branches

#### Multiple distinct if statements

A programmer can use multiple if statements in sequence to detect multiple features with independent actions

Multiple sequential if statements look similar to a multi-branch statement but has a very different meaning

  -Each if statement is independent, and thus more than one branch can execute

    if (userAge < 16) {
        System.out.println("Enjoy your early years.");
    }

    if (userAge > 15) {
        System.out.println("You are old enough to drive.");
    }

    if (userAge > 17) {
        System.out.println("You are old enough to vote.");
    }

    if (userAge > 24) {
        System.out.println("Most car rental companies will rent to you");
    }



### 4.11 Switch Statements
A ***switch statement*** can more clearly represent multi-branch behavior involving a variable being compared to constant values

The program executes the first ***case*** whose constant expression matches the value of the switch expression, executes the case's statement, and then jumps to the end, then the ***default case*** statements are executed

    switch (a) {
        case 0:
            // Print "zero"
            break;

        case 1:
            // Print "one"
            break;

        case 2:
            // Print "two"
            break;

        default:
            // Print "unknown"
            break;
        }

#### Switch statement general form

The switch statement's expression should be an integer, char, or string. The expression should not be a Boolean or a floating-point type. Each case must have a constant expression like 2 or 'q'; a case expression canoot be a expession
  - Order does not matter (though it is bad style)
  - !! Good practice - ALWAYS HAVE DEFAULT CASE FOR SWITCH

#### Omitting the break statement

Omitting the ***break*** statement for a case will cause the statements within the next case to be executed

    if (dogAgeYears == 0) {
        System.out.print("Enter dog's age in months: ");
        dogAgeMonths = scnr.nextInt();

        switch (dogAgeMonths) {
        case 0:
        case 1:
        case 2:
            System.out.println("That's 0..14 human months.");
            break;

        case 3:
        case 4:
        case 5:
        case 6:
            System.out.println("That's 14 months to 5 human years.");
            break;

        case 7:
        case 8:
            System.out.println("That's 5..9 human years.");
            break;

        case 9:
        case 10:
        case 11:
        case 12:
            System.out.println("That's 9..15 human years.");
            break;

        default:
            System.out.println("Invalid input.");
            break;
        }
    }
    else {
        System.out.println("FIXME: Do earlier dog years cases");
        switch (dogAgeYears) {
        }
    }

### 4.14 String access operations 

#### Working with the end of a string

The method ***length()*** returns the length of a string
  - If s1 is "Hey", s1.length() returns 3

A common task is to append(add to the end) a string to an existing string
  - The ***+*** operator can return a new string tat appends a string to another string
  - Similarly, s1.***concat***(s2) returns a new string that appends s2 to s1.
    - If s1 is "Hey", then 1.concat("!!!") returns "Hey!!!"
 

# Guided Experiment

## Boolean Expression Experimentation

    public class SmartHome {
        public static void main(String[] args)
        {
            final int MAX_TIME = 60; // minutes
            boolean alertMode = true; 
            boolean lightsOn = true; 
            boolean away = false; 
            int timeOn = 0; //minutes 

            boolean alert = alertMode && ((lightsOn && away) || (timeOn > MAX_TIME));

            System.out.println("An alert has been triggered: " + alert);
        }
    }

- Modify the values as shown below. Has the alert been triggered and if not, why?

      alertMode = false
      lightsOn = true
      away = true
      timeOn = 0

  - The alert was not triggered because the left side is false and the right is true leading to alert = false

- Modify the values as shown below. Has the alert been triggered and if not, why?

      alertMode = false
      lightsOn = true
      away = true
      timeOn = 120

  - The alert would be false because the left side is false and the right is true leading to alert = false

- Modify the values as shown below. Has the alert been triggered and if not, why?

      alertMode = true
      lightsOn = false
      away = false
      timeOn = 120

  - The alert was triggered because the left side is true but the right is true leading to alert = true

- Modify the values as shown below. Has the alert been triggered and if not, why?

      alertMode = true
      lightsOn = true
      away = false
      timeOn = 0

  - The expression is false because alertMode is true but lightsOn && away are truth and false making it false which makes alertMode && (lightsOn && away) = false. Since timeOn is not greater than MAX_TIME that would be false making the alert print false

## Data Comparison

In the ObjectComparison file, if we change ***if (p1 == p3)*** to:

    if (p1 == p2)

Then the it will print "The objects are NOT aliases" because the statement is no longer true since the p2 does not reference the same object which is p1. They are using == to check the alias and not the value

In the second experiment, when we change p1.equals(p2) to:

    p1.equals(p3)

then the statement is still true since p3 = p1

## Switch Statements

In the GradeReport.java file, if you remove the breaks in the switch statement, whenever you type in the input, then the code is broken because there is so stop when the code is ran




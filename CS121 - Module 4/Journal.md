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




# Coding Journal
## Name: Chris Condreay
## Reading / Lab: Module 5
## Entries:
### February 27, 2023

### 5.1 User-defined method basics

#### Methods

A program may perform the same operations repeatedly, causing a large and confusing program due to redundancy

A ***method*** is a program redundancy that can be reproduced by creating a grouping of predefined statemenets for repeatedly used operations

  - Even without redundancy, methods can prevent a main program from becoming large and confusing

#### Basic of methods

A ***method*** is named lists of statements
  - A ***method definition*** consists of the new method's name and block of statements

        public static double calcPizzaArea() (/* block of statements */)

  - A ***method call*** is an invocation of a method's name, causing the method's statement to execute

The method's name can be any valid identifier. A ***block*** is a list of statements surrounded by braces

    public class PizzaArea {
      public static double calcPizzaArea() {
        double pizzaDiameter;
        double pizzaRadius;
        double pizzaArea;
        double piVal = 3.14159265;

        pizzaDiameter = 12.0;
        pizzaRadius = pizzaDiameter / 2.0;
        pizzaArea = piVal * pizzaRadius * pizzaRadius;
        return pizzaArea;
      }

      public static void main(String[] args) {
        System.out.println("12 inch pizza is " + calcPizzaArea() + " inches squared");
      }
    }

***!!! Methods must be stored inside a class !!!***

*public class PizzaArea* has two classes, calcPizzaArea() and main(), these both use ***access modifiers*** 

    public static

  - public indicates the method may be called from any class in the program, and static indicates the method only uses values that are passed to the method

#### Returning a value from a method

A method may return one value using a ***return statement***

    public class SquareComputation {

      public static int computeSquare(int numToSquare) {

          // method returns 49
          return numToSquare * numToSquare;
      }

      public static void main (String [] args) {
          int numSquared;

          // computeSquare() is called, passing 7 to the method's numToSquare parameter
          numSquared = computeSquare(7);

          // prints "7 squared is 49"
          System.out.println("7 squared is " + numSquared);
      }
    }

A return type of ***void*** incdicates that a method does not return any value

#### Parameters

A programmer can influence a method's behavior via an input

  - A ***parameter*** is a method input specified in a mothod definition
  - An ***argument*** is a value provided to a method's parameter during a method call

#### Multiple or no parameters

A method definition may have multiple parameters, separated by commas
  - Parameters are assigned with argument values by position: First parameter with first argument, second with second, etc.

A method definition with no parameters must still have the parentheses

    int doSomething() { ... }

5.1.1: Method with multiple parameters

    public class PizzaVolume {

      public static double calcPizzaVolume(double pizzaDiameter, double pizzaHeight) {
          double pizzaRadius;
          double pizzaArea;
          double pizzaVolume;
          double piVal = 3.14159265;

          pizzaRadius = pizzaDiameter / 2.0;
          pizzaArea = piVal * pizzaRadius * pizzaRadius;
          pizzaVolume = pizzaArea * pizzaHeight;
          return pizzaVolume;
      }

      public static void main (String [] args) {
          System.out.println("12.0 x 0.3 inch pizza is "  + calcPizzaVolume(12.0, 0.3) + " inches cubed");
          System.out.println("12.0 x 0.8 inch pizza is "  + calcPizzaVolume(12.0, 0.8) + " inches cubed");
          System.out.println("16.0 x 0.8 inch pizza is "  + calcPizzaVolume(16.0, 0.8) + " inches cubed");
      }
    }

#### Parameters 
A programmer can influence a method's behavior via an input
  - A ***parameter*** is a method input specified in a method definition
  - An ***argument*** is a value provided to a method's parameter during a method call

A parameter is like a variable declaration. Upon a call, the parameter's memory location is allocated, and the parameter is assigned with the argument's value
  - Upon returning to the original call location, the parameter is deleted from memory

#### Multiple or No parameters

A method definiton may have multiple parameters, separated by commas. Parameters are assigned with argument values by position
  1. First parameter with first argument
  2. Second with second

A method definition with no parameters must still have parenthesis, as in: **int doSomething() {...}**

    public class PizzaVolume {

      public static double calcPizzaVolume(double pizzaDiameter, double pizzaHeight) {
          double pizzaRadius;
          double pizzaArea;
          double pizzaVolume;
          double piVal = 3.14159265;

          pizzaRadius = pizzaDiameter / 2.0;
          pizzaArea = piVal * pizzaRadius * pizzaRadius;
          pizzaVolume = pizzaArea * pizzaHeight;
          return pizzaVolume;
      }

      public static void main (String [] args) {
          System.out.println("12.0 x 0.3 inch pizza is "  + calcPizzaVolume(12.0, 0.3) + " inches cubed");
          System.out.println("12.0 x 0.8 inch pizza is "  + calcPizzaVolume(12.0, 0.8) + " inches cubed");
          System.out.println("16.0 x 0.8 inch pizza is "  + calcPizzaVolume(16.0, 0.8) + " inches cubed");
      }
    }

#### Calling methods from methods
A method's statements may call other methods

    public class MethodsCallingMethods {

      public static double calcCircleArea(double circleDiameter) {
          double circleRadius;
          double circleArea;
          double piVal = 3.14159265;
              
          circleRadius = circleDiameter / 2.0;
          circleArea = piVal * circleRadius * circleRadius;
              
          return circleArea;
      }

      public static double pizzaCalories(double pizzaDiameter) {
          double totalCalories;
          double caloriesPerSquareInch = 16.7;    // Regular crust pepperoni pizza
              
          totalCalories = calcCircleArea(pizzaDiameter) * caloriesPerSquareInch;
              
          return totalCalories;
      }

      public static void main (String [] args) {
          System.out.printf("12 inch pizza has %.2f calories.\n", pizzaCalories(12.0));
          System.out.printf("14 inch pizza has %.2f calories.\n", pizzaCalories(14.0));
      }
    }

### 5.2 Print methods

#### Printing from a method

A common operation for a method is to print text. Large text outputs can clutter the main() method of a program, especially if the text needs to be output multiple times

A method that only prints typically does not return a value
The ***void*** keyword indicates a method does not return a value
A method with a void return type is often called a ***void method***. Once a void method finishes execution, control returns back to the called and no value is returned

#### Calling a print method multiple times

One benefit of a print method is that complex output statements can be written in code once
The print method can be called multiple times to produce the output instead of rewriting complex statements for every necessary instance 

    import java.util.Scanner;

    public class MenuSystem {
      public static void printMenu() {
          System.out.println("Today's Menu:");
          System.out.println("   1) Gumbo");
          System.out.println("   2) Jambalaya");
          System.out.println("   3) Quit\n");
      }
      
      public static void main(String[] args) {
          Scanner scnr = new Scanner(System.in);
          boolean quit = false;
          int choice;

          while (!quit) {
            printMenu();
            System.out.print("Enter choice: ");
            choice = scnr.nextInt(); 
            if (choice == 3) {
                System.out.println("Goodbye");
                quit = true;
            }
            else {
                System.out.print("Order: ");
                if (choice == 1) {
                  System.out.println("Gumbo");
                }
                else if (choice == 2) {
                  System.out.println("Jambalaya");
                }
                System.out.println();
            }  
          }  
      }
    }

### 5.3 Reasons for defining methods

#### Improving Program readability

Programs can become hard for humans to read and understand. Decomposing a program into methods can greatly aid program readability, helping yield an initially correct program

    import java.util.Scanner;

    public class CalorieCalc {
      public static double stepsToMiles(int numSteps) {
          final double FEET_PER_STEP = 2.5;               // Typical adult
          final int FEET_PER_MILE = 5280;

          return numSteps * FEET_PER_STEP * (1.0 / FEET_PER_MILE);
      }

      public static double stepsToCalories(int numSteps) {
          final double STEPS_PER_MINUTE = 70.0;           // Typical adult
          final double CALORIES_PER_MINUTE_WALKING = 3.5; // Typical adult
          double minutesTotal;
          double caloriesTotal;

          minutesTotal = numSteps / STEPS_PER_MINUTE;
          caloriesTotal = minutesTotal * CALORIES_PER_MINUTE_WALKING;

          return caloriesTotal;
      }
      
      public static void main(String[] args) {
          Scanner scnr = new Scanner(System.in);
          int stepsWalked;
          
          System.out.print("Enter number of steps walked: ");
          stepsWalked = scnr.nextInt();
          
          System.out.println("Miles walked: " + stepsToMiles(stepsWalked));
          System.out.println("Calories: " + stepsToCalories(stepsWalked));
      }
    }

*User defined methods make main() easy to understand*

#### Modular and incremental program development

Programmers commonly use methods to write programs modularly and incrementally

  - ***Modular development*** is the process of dividing a program into separate modules that can be developed and tested separately and then integrated into a single program
  - ***Incremental development*** is a process in which a programmer writes, compiles, and tests a small amount of code, then writes, compiles, and tests a small amount more, an so on
  - A ***method stub*** is a method definition whose statements have not yet been written

A programmer can use method stubs to capture the high-level behavior of main() and the required method (or modules) before diving into details of each method, like planning a route for a road trip before starting to drive

#### Avoid writing redundant code

A method can be defined once, then called from multiple places in a program, thus avoiding redudant code.

### 5.22 ArrayList

#### ArrayList introduction

An ***ArrayList*** is an ordered list of reference type items that comes with Java,
Each item in an ArrayList is known as an ***element***. The statement **import.util.ArrayList;** enables use of an ArrayList

The declaration **ArrayList<Integer> vals = new Arraylist<Integer>()** creates reference variable vals that refers to a new ArrayList object consisting of Integer objects.


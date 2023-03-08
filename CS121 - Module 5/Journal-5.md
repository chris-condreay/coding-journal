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

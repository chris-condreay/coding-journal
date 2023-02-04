# Coding Journal
## Name: Chris Condreay
## Lab: Module 3
## Entries: January 31st, 2023

### 3.1 Objects: Introduction

#### Grouping things into objects

An **object** is a group of data (variables) and operations that can be performed on that data (methods)

  - Programs commonly are not viewed as variables and functions/methods, but as objects

#### Abstraction / Information hiding

**Abstraction** means to have a user interact with an item at high-level, with lower-level internal details hidden from the user (**information hiding** or **encapsulation**)

  - Objects strongly support abstraction, hiding entire groups of methods and variables, exposing only certain methods to a user

An **abstact data type** (**ADT**) is a data type whose creation and update are constrained to specific well-defined operations. A class can be used to implement an ADT

### 3.2 Using a Class

#### Classes intro: Public member methods

The **class** construct defines a new type that can group data and methods to form an object.

A class' **public member methods** indicate all operations a class user can perform on the object.

  - The power of classes is that a class user need not know how the class' data and methods are implemented, but need only understand how each public member method behaves

        public class Restaurant {                         // Info about a restaurant
          // Internal fields

          public void setName(String restaurantName) {    // Sets the restaurant's name
              ...
          }

          public void setRating(int userRating) {         // Sets the rating (1-5, with 5 best)
              ...
          }

          public void print() {                           // Prints name and rating on one line
              ...
          }
        }

      - A class definition creates a new type that can be used to create objects. The class declares all methods a programmer can call to operate on such an object.
      - A class user can create an object by declaring and initializing a variable of the class type with new instance of the class type

            Restaurant favPlace = new Restaurant();

      - The class user can then call the methods to operate on the object

            Restaurant favPlace = new Restaurant();
            
            favPlace.setName("Central Deli");
            favPlace.setRating(4);
            favPlace.print();
      
#### Using a class

A programmer can create one or more objects of the same class. Creating an object consists of two steps:
  1. declaring a refrerence variable of the class type
  2. assigning the variable with an explicit;y allocated instance of the class type

A **reference variable** can refer to an instance of a class

The **new** operator explicitly allocates an ***object*** of the specified class type

    Restaurant favLunchPlace = new Restaurant();  // creates a Restaurant object named favLunchPlace

The "." operator, known as the ***member access operator***, is used to invoke a method on an object

    favLunchPlace.setRating(4) // calls setRating on favLunchPlace
                               // sets the rating to 4

#### Class example: String

- Java's Strring object is a class that stores a character string in memory, along with variables indicating the length and other things, but a String's user doesn't need to know

- Instead, the String's user just needs to know what public member methods can be used

      // Returns the character value at the index
      public char chatAt(int index);

      //Returns the length of the string
      public int length();

      //Returns a new string with the string argument
      //concatenated to the end of this string
      public String concat(String str);

### 3.3 Objects and references

#### References

A **reference** is a variable type that refers to an object

  - A reference might be thought of as storing the memory address of an object
  - Variables of a class data type(and array types) are refence variables

### 3.4 Primitive and reference types

#### Wrapper classes

Java variables are one of two types

  1. A **primitive type** variable directly stores the data for that variable type such as int, double, or char
  2. A **reference type** variable can refer to an instance of a class, also known as an object

Java provides several **wrapper classes** that are built-in reference types that augment the primitive types

The **Integer** data type is a built-in class in Java that augments the int primitive type

    // Declares an Integer reference variable maxPlayers
    // refers to an instance of the Integer class
    Integer maxPlayers = 10;

#### Memory allocation for wrapper class objects

A wrapper class object is ***immutable***, meaning a programmer cannot change the object via methods or variable assignments after object creation

  - The example uses the ***Double*** class to calculate the amount of time necessary to drive or fly a certain distance

        import java.util.Scanner;

        public class FlyDrive {
          public static void main(String [] args) {
              Scanner scnr = new Scanner(System.in);
              Double distMiles; 
              Double hoursFly;
              Double hoursDrive;

              System.out.print("Enter a distance in miles: ");
              distMiles = scnr.nextDouble();

              hoursFly = distMiles / 500.0;
              hoursDrive = distMiles / 60.0;

              System.out.println(distMiles + " miles would take:");
              System.out.println(hoursFly + " hours to fly");
              System.out.println(hoursDrive + " hours to drive");
          }
        }

#### Comparing wrapper class objects

Common error when referencing variables of wrapper classes is using equality operators == and != when comparing values

  - using the equality operators on any two reference evaluates to true or false depending on each operand's referenced objects
  - The expression num1 == num2 compares if both num1 and num2 reference the same Integer object, but does not compare the Integers' contents

Reference variables of wrapper classes can also be compared using the **equals()** and **compareTo()** methods

### 3.5 Wrapper class conversions

#### Autoboxing and Unboxing

**Autoboxing** is the automatic conversion of primitive types to the corresponding wrapper classes

**Unboxing** is the automatic converesion of wrapper class objects to the corresponding primitive types

###### Autoboxing Senarios
(1) Assign primitive type to wrapper class variable

    Double floorArea = 20.25; // Autboxing of 20.25 to a Double
    Integer calcResult;

    calcResult = 5 / 2; //Autoboxing of expression result to Integer

    int num1 = 23;
    Integer num2 = num1; // Autoboxing of num1 to Integer

(2) Pass primitive type to a method with wrapper class parameter

    public void setRate(Double rate) {
      // ...
    }

    setRate(50.2); // Autoboxing of 50.2 to Double

    double newRate = 97.2;
    setRate(newRate); // Autoboxing of newRate to Double

###### Unboxing Scenarios
(1) Assign wrapper class variable to primitive type

      Double num1 = 3.14;
      Character letter1 = 'A';

      double num2 = num1; // Unboxing of Double to double
      char letter2 = letter1; // Unboxing of Character to char

(2) Pass wrapper class variable to a method with primitive type parameter

    public void setInitial(char letter) {
      // ...
    }

    Character userInitial = 'Z';
    setInitial(userInitial); // Unboxing of userInitial to a char

(3) Combine wrapper class and primitive types in expression

    Double currTemp = 95.2;
    double tempDiff = 100.0 - currTemp; // Unboxing of currTemp to double

    Integer numItems = 11;

    if (numItems % 2 == 0) { // Unboxing of numItems to int
      // ...
    }

#### Converting to primitive types

The Integer, Double, and Long wrapper classes provide methods for converting object to primtive types

***intValue()*** returns the value of the wrapper class object as a primitive int value, type casting if necessary

***doubleValue ()*** returns the value of the wrapper class object as a primitive double value, type casting if necessary

***longValue()*** returns the value of the wrapper class object as a primitive long value, type casting if necessary

    Integer num1 = 14;
    Double num2 = 6.7643;
    Double num3 = 5.6e12;

    num2.intValue() // Returns 6

    num1.doubleValue() // Returns 14.0

    num3.longValue() // Returns 5600000000000

The Character and Boolean classes support the ***charValue()*** and ***booleanValue()*** methods, respectively, which perform similar functions

#### Converting to and from Strings

***toString()*** returns a String containing the decimal representation of the value contained by the wrapper class object

    Integer num1 = 10;
    Double num2 = 3.14;

    num1.toString() // Returns "10"
    num2.toString() // Returns "3.14"



***Integer.toString***(someInteger) returns a String containing the decimal representation of the value of someInteger. someInteger may be an Integer object, a int variable, or an integer literal. This static method is also available for the other wrapper classes (e.g.,  **Double.toString(someDouble)**)


    Integer num1 = 10;
    int regularInt = 20;

    Integer.toString(num1)       // Returns "10"
    Integer.toString(regularInt) // Returns "20"
    Integer.toString(3)          // Returns "3"

***Integer.parseInt***(someString) parses someString and returns an int representing the value encoded by someString. This static method is also available for the other wrapper classes (e.g., **Double.parseDouble(someString)**), returning the corresponding primitive type

    String str1 = "32";

    Integer.parseInt(str1)    // Returns int value 32
    Integer.parseInt("2001") // Returns int value 2001

***Integer.valueOf***(someString) parses someString and returns a new Integer object with the value encoded by someString. This static method is also available for the other wrapper classes (e.g., **Double.valueOf(someString)**), returning a new object of the corresponding type

    String str1 = "32";

    Integer.valueOf(str1)    // Returns Integer object with value 32
    Integer.valueOf("2001") // Returns Integer object with value 2001

***Integer.toBinaryString***(someInteger) returns a String containing the binary representation of someInteger. someInteger may be an Integer object, a int variable, or an integer literal. This static method is also available for the Long classes (e.g.,  **Long.toBinaryString(someLong)**)

    Integer num1 = 10;
    int regularInt = 20;

    Integer.toBinaryString(num1)       // Returns "1010"
    Integer.toBinaryString(regularInt) // Returns "10100"
    Integer.toBinaryString(7)          // Return "111"


Ex: Converting a decimal number to a binary 

    import java.util.Scanner;

    public class DecimalToBinary {
      public static void main(String [] args) {
          Scanner scnr = new Scanner(System.in);
          int decimalInput;
          String binaryOutput;
          
          System.out.print("Enter a decimal number: ");
          decimalInput = scnr.nextInt();
          
          binaryOutput = Integer.toBinaryString(decimalInput);
          
          System.out.println("The binary representation of " + decimalInput +
                            " is " + binaryOutput);
      }
    }

### 3.6 Using packages

#### Built-in Java packages

A **package** is a grouping of related types, classes, interfaces, and subpackage

**Package members** are the types, classes, and interfaces in a package

###### Common Java packages

  - ***java.lang*** (String, Integer, Double, Math)
    - Contains fundamental Java classes. Automatically imported by Java
  - ***java.util*** (Collection, ArrayList, LinkedListm Scanner)	
    - Contains the Java collections framework classes and miscellaneous utility classes
  - ***java.io*** (File, InputStream, OutputStream)
    - Contains classes for system input and output
  - ***javax.swing*** (JFrame, JTextField, JButton)
    - Contains classes for building graphical user interfaces

A class' **fully qualified name** is the concatenation of the package name with the class name using a period

An **import statement** imports a package member into a file to enable use of the package member directly, without having to use the package member's fully qualified name

A programmer import all members of a package by using the **wildcard** character "*" instead of a package member name
    
    import java.util.*;

### 3.7 Random numbers

#### Generating a random number

The **Random** class provides methods that return a random integer in the range -2^31 to 2^31 - 1 or a programmer-defined range

    import java.util.Random;

    public class ThreeRandomValues {
      public static void main(String[] args) {
          Random randGen = new Random();  // New random number generator

          System.out.println(randGen.nextInt());  // 959650663
          System.out.println(randGen.nextInt());  // 324135575
          System.out.println(randGen.nextInt());  // 1735989143
      }
    }

The statement **import java.util.Random;** enables use of the Random class

  - The statement *Random randGen = new Random();* creates a new random number generator object named randGen

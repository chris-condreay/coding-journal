# Coding Journal
## Name: Chris Condreay
## Reading / Lab: Module 6
## Entries:
### March 13, 2023

### 6.1 Definig a class

#### Private fields
In addition to public member methods, a class definiton has ***private fields***: variables that member methods can access but class users cannot

#### Defining a class' public member methods
A programmer defining a class first names the class, *declares* private fields, and *defines* public member methods.

A class methods are collectively called ***class members***

The programmer defines the details of each member method, sometimes called the class' ***implementation***

A ***method definition*** provides an access modifier, return type, name, parameters, and the method's statements
  - A member method can access all private fields

  *Restaurant.java*

    public class Restaurant {                          // Info about a restaurant
      private String name;
      private int rating;

      public void setName(String restaurantName) {    // Sets the restaurant's name
          name = restaurantName;
      }

      public void setRating(int userRating) {         // Sets the rating (1-5, with 5 best)
          rating = userRating;
      }

      public void print() {                           // Prints name and rating on one line
          System.out.println(name + " -- " + rating);
      }
    }
  
  *RestaurantFavorites.java*

    public class RestaurantFavorites {
      public static void main(String[] args) {
          Restaurant favLunchPlace = new Restaurant();
          Restaurant favDinnerPlace = new Restaurant();

          favLunchPlace.setName("Central Deli");
          favLunchPlace.setRating(4);

          favDinnerPlace.setName("Friends Cafe");
          favDinnerPlace.setRating(5);

          System.out.println("My favorite restaurants: ");
          favLunchPlace.print();
          favDinnerPlace.print();

          // My favorite restaurants:
          // Central Deli -- 4
          // Friens Cafe -- 5
      }
    }

### 6.2 Mutators, accessors, and private helpers

#### Mutators and accessors

A class' public methods are commonly classified as either mutators or accessors
  - A ***mutator*** method may modify ("mutate") a class' fields
  - An ***accessor*** method accesses fields but may not modify a class' fields

Commonly, a field has two associated methods:

  1. A mutator for setting the value
  2. An accesor for getting the value, known as a ***setter*** and ***getter*** method, respectively, and typically with names starting with set or get

  *Restaurant.java*
    
    public class Restaurant {                          
      private String name;
      private int rating;

      public void setName(String restaurantName) {  // Mutator
          name = restaurantName;
      }

      public void setRating(int userRating) {       // Mutator
          rating = userRating;
      }

      public String getName() {  // Accessor
          return name;
      }

      public int getRating() {  // Accessor
          return rating;
      }

      public void print() {      // Accessor
          System.out.println(name + " -- " + rating);
      }
    }

  *MyRestaurant.java*

    public class MyRestaurant {
      public static void main(String[] args) {
        Restaurant myPlace = new Restaurant();
        myPlace.setName("Maria's Diner");
        myPlace.setRating(5);
        System.out.print(myPlace.getName() + " is rated ");
        System.out.println(myPlace.getRating());
      }
    }

#### Private helper methods

A programmer commonly creates private methods, known as ***private helper methods***, to help public methods carry out tasks

*Dog.java*

    public class Dog {
      private int years;
      private int weight;
      private String size;
      private int humanYears;

      private void setHumanYears() {
        int factor;
      
        if (size.equals("small")) {
          factor = 6;
        }
        else if (size.equals("medium")) {
          factor = 7;
        }
        else {
          factor = 8;
        }
    
        humanYears = years * factor;
      }
      
      public int getHumanYears() {
        return humanYears;
      }

      public void setWeightAndAge(int weightToSet, int yearsToSet) {
        weight = weightToSet;

        if (weight <= 20) {
          size = "small";
        }
        else if (weight <= 50) {
          size = "medium";
        }
        else {
          size = "large";
        }

        years = yearsToSet;
        setHumanYears();
      }
    }

  *CallDog.java*

    
    CallDog.java
      Dog.java
      public class CallDog {
        public static void main(String [] args) {
          Dog buddy = new Dog();

          buddy.setWeightAndAge(52, 9);
          System.out.print("Human years: " + buddy.getHumanYears());
      
      }
    }

### 6.3 Initialization and constructors
*A good practice is to initialize all variables when declared*

#### Field initialization
A programmer can initialize fields in the field declaration. Any object created in that class type will initially have those values

*Restaurant.java*

    public class Restaurant {

      !!!! 
      private String name = "NoName";
      private int rating = -1; 
      !!!!


      public void setName(String restaurantName) {  
          name = restaurantName;
      }

      public void setRating(int userRating) {
          rating = userRating;
      }

      public void print() {  
          System.out.println(name + " -- " + rating);
      }
    }

*RestaurantFavorites.java*

    public class RestaurantFavorites {
      public static void main(String[] args) {
        Restaurant favLunchPlace = new Restaurant(); // Initializes fields with values in class definition

        // Prints NoName -- -1
        favLunchPlace.print();

        // set name and rating to different values
        favLunchPlace.setName("Central Deli");
        favLunchPlace.setRating(4);
        
        favLunchPlace.print(); // Prints Central Deli -- 4
      }
    }

#### Constructors
Java provides a special class member method, known as a ***constructor***, that is called when an object of that class type is created, and which can be used to initialize all fields

  - The constructor has the same name as the class
  - The constructor method has no return type, not even void
    - Ex: **public Restaurant() {...}** defines a constructor for the Restaurant class
  - A programmer specifies the constuctor that should be called when creating an object
    - Ex: **Restaurant favLunchPlace = new Restaurant();** creates a new Restaurant object and calls the constructor Restaurant()

If a class does not have a programmer-defined constructor, then the Java compiler *implicitly* defines a default constructor with no arguments

*Restaurant.java*

    public class Restaurant {
      private String name = "NoName";
      private int rating = -1;

      public Restaurant() {  // Constructor with no arguments
        name = "NoName";     // Default name: NoName indicates name was not set
        rating = -1;         // Default rating: -1 indicates rating was not set
      }

      public void setName(String restaurantName) {  
        name = restaurantName;
      }

      public void setRating(int userRating) {
        rating = userRating;
      }

      public void print() {  
        System.out.println(name + " -- " + rating);
      }
    }

*RestaurantFavorites.java*

    public class RestaurantFavorites {
      public static void main(String[] args) {
        Restaurant favLunchPlace = new Restaurant(); // Call the constructor

        // Prints NoName -- -1
        favLunchPlace.print();

        // set name and rating to different values
        favLunchPlace.setName("Central Deli");
        favLunchPlace.setRating(4);
        
        favLunchPlace.print(); // Prints Central Deli -- 4
      }
    }

### 6.4 Choosing classes to create

#### Decomposing into classes
Thinking of a program as classes is sometimes helpful, sometimes not, depending on the application. Even when helpful, many ways exist to decompose the program into classes

#### Coding the classes
A programmer can convert class sketches into code. The programmer likely would first create and test the Person class, followed by the Team class.

*TeamPerson.java*

    public class TeamPerson {
      private String fullName;
      private int ageYears;
      
      public void setFullName(String firstAndLastName) {
          fullName = firstAndLastName;
      }
      
      public void setAgeYears(int ageInYears) {
          ageYears = ageInYears;
      }
      
      public String getFullName() {
          return fullName;
      }
      
      public int getAgeYears() {
          return ageYears;
      }
      
      public void print() {
          System.out.println("Full name: " + fullName);
          System.out.println("Age (years): " + ageYears);
      }
    }

*SoccerTeam.java*

    public class SoccerTeam {
      private TeamPerson headCoach;
      private TeamPerson assistantCoach;
      // Players omitted for brevity
      
      public void setHeadCoach(TeamPerson teamPerson) {
          headCoach = teamPerson;
      }
      
      public void setAssistantCoach(TeamPerson teamPerson) {
          assistantCoach = teamPerson;
      }
      
      public TeamPerson getHeadCoach() {
          return headCoach;
      }
      
      public TeamPerson getAssistantCoach() {
          return assistantCoach;
      }
      
      public void print() {
          System.out.println("HEAD COACH: ");
          headCoach.print();
          System.out.println();
          
          System.out.println("ASSISTANT COACH: ");
          assistantCoach.print();
          System.out.println();
      }
    }

*SoccerTeamPrinter.java*

    public class SoccerTeamPrinter {
      public static void main(String[] args) {
          SoccerTeam teamCalifornia = new SoccerTeam();
          TeamPerson headCoach = new TeamPerson();
          TeamPerson asstCoach = new TeamPerson();
          
          headCoach.setFullName("Mark Miwerds");
          headCoach.setAgeYears(42);
          teamCalifornia.setHeadCoach(headCoach);

          asstCoach.setFullName("Stanley Lee");
          asstCoach.setAgeYears(30);
          teamCalifornia.setAssistantCoach(asstCoach);

          teamCalifornia.print();
      }
    }

### 6.5 Defining main() in a programmer-defined class

#### Defining main() in a programmer-defined class

The main() method can be defined within a programmer-defined class and create objects of that clas type
main() is a static method that is independent of class objects
  - main() can access other static methods and static fields of the class, but cannot directly access non-static methods or fields, like BasicCar's checkOdometer() method
  - a programmer must create objects within main() to call non-static methods on those objects
    - Ex: BasicCar's main() creates two objects of type BasicCar and performs operations on those objects

Non-static fields and methods are also called instance variables and instance methods

    public class BasicCar {

      // Total miles driven by the car
      private int milesDriven;
        
      // Constructor assigns initial values to instance variables
      public BasicCar() {
          milesDriven = 0;   
      }

      // Drive the requested miles
      public void drive(int tripMiles) {
          milesDriven = milesDriven + tripMiles;
      }

      // Return total number of miles driven
      public int checkOdometer() {
          return milesDriven;
      }

      ================================================
      // Main() creates objects of type BasicCar and 
      // calls methods to operate on the objects
      public static void main(String [] args) {
          BasicCar redCorvette = new BasicCar();
          BasicCar fordMustang = new BasicCar();

          redCorvette.drive(100);        
          fordMustang.drive(75);
          fordMustang.drive(300);
          fordMustang.drive(50);        
      }
      =================================================
    }

### 6.6 Unit testinf (classes)

#### Testbenches

A ***testbench*** is a program whose job is to thoroughly test another program (or portion) via a series of input/output checks know as ***test cases***

***Unit testing*** means to create and run a testbench for a specific item (or "unit") like a method or a class

Features of a good testbench include:
  - Automatic checks
    - Ex: Values are compared, as in **testData.GetNum1() != 100**. For conciseness, only fails are printed
  -Independent test cases
    - Ex: The test case for GetAverage() assigns new values, vs. relying on earlier values
  - ***100% code coverage***: Every line of code is executed
    - A good testbench would have more test cases than below
  -Includes not just typical values but also ***border cases***: Unusual or extreme test cases values like 0, negative numbers, or large numbers

*The testbench below creates an object, then checks public methods for correctness. Some tests failed*

Class to test: StatsInfo.java

    public class StatsInfo {

      // Note: This class intentionally has errors

      private int num1;
      private int num2;

      public void setNum1(int numVal) {
          num1 = numVal;
      }

      public void setNum2(int numVal) {
          num2 = numVal;
      }

      public int getNum1() {
          return num1;
      }

      public int getNum2() {
          return num1;
      }

      public int getAverage() {
          return num1 + num2 / 2;
      }
    }

Testbench: StatsInfoTest.java

    public class StatsInfoTest {
      public static void main(String[] args) {
          StatsInfo testData = new StatsInfo();

          // Typical testbench tests more thoroughly

          System.out.println("Beginning tests.");

          // Check set/get num1
          testData.setNum1(100);
          if (testData.getNum1() != 100) {
            System.out.println("   FAILED set/get num1");
          }

          // Check set/get num2
          testData.setNum2(50);
          if (testData.getNum2() != 50) {
            System.out.println("   FAILED set/get num2");
          }

          // Check getAverage()
          testData.setNum1(10);
          testData.setNum2(20);
          if (testData.getAverage() != 15) {
            System.out.println("   FAILED GetAverage for 10, 20");
          }

          testData.setNum1(-10);
          testData.setNum2(0);
          if (testData.getAverage() != -5) {
            System.out.println("   FAILED GetAverage for -10, 0");
          }

          System.out.println("Tests complete.");
      }
    }

```console
Beginning test.
  FAILED set/get num2
  FAILED GetAverage for 10, 20
  FAILED GetAverage for -10, 0
Tests complete
```

#### Regression testing

***Regression testing*** means to retest an item like a class anytime that item is changed; if previously-passed test cases fail, the item has "regressed"

  - A testbranch should be maintained along with the item, to always be usable for regression testing

#### Erroneous unit tests

An erroneous unit test may fail even if the code being tested is correct
*A common error is for a programmer to assume that a failing unit test means that the code being tested has a bug*
  - such an assumption would lead to the programmer trying to "fix" code that is already correct
*Good practice is to inspect the code of a failing unit test before making changes to the code being tested*
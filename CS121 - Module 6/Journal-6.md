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

### 6.7 Constructor overload

#### Basics

Programmers often want to provide different initialization values when creating a new object

A class creator can ***overload*** a constructor by defining multiple constructors different in parameter types
  - When an object is created with the new operator. arguments can be passed to the constructor
  - The constructor with matching parameters will be called

#### If any constructor defined, should define default

*If a programmer defines any constructor, the compiler does not implicitly define a default constrcutor, so good practice is for the programmer to also explicitly define a default constructor* so that an object creation like **new MyClass()** remains supported 

Error - The programmer defined a constructor, so the compiler does not automatically define a default constructor

    public class Restaurant {
      public Restaurant(String initName, int initRating) {
          ... 
      }

      // No other constructors
    }

    public class RestaurantFavorites {
      public static void main(String[] args) {
          Restaurant foodPlace = new Restaurant();              
          ...
      }
    }

```console
RestaurantFavorites.java:3: cannot find symbol
symbol  : constructor Restaurant()
location: class Restaurant
      Restaurant foodPlace = new Restaurant();
                             ^
```

### 6.8 The 'this' implicit parameter

#### Implicit parameter

An object's member method is called using the syntax **objectReference.method()**

The object reference before the method name is known as an ***implicit parameter*** of the member method because the compiler converts the call syntax **objectReference.method(...)** into a method call with the object reference implicity passed as a parameter.
  - Ex: **method(objectReference, ...)**

Within a member method, the implicity-passed object reference is accessible via the keyword ***this***
  - A class member can be accessed as **this.classMember**
    - The "**.**" is the member access operator

Using **this** makes clear that a class member is being accessed and is essential if a field member and parameter have the same indentifer

*ShapeSquare.java*

    public class ShapeSquare {
      // Private fields
      private double sideLength;

      // Public methods
      public void setSideLength(double sideLength) {
        ================================
          this.sideLength = sideLength;
          // Field member    Parameter
        ================================
      }

      public double getArea() {
          return sideLength * sideLength; // Both refer to field
      }
    }

*ShapeTest.java*

    public class ShapeTest {
      public static void main(String[] args) {
          ShapeSquare square1 = new ShapeSquare();

          square1.setSideLength(1.2);
          System.out.println("Square's area: " + square1.getArea());
      }
    }

```console
Square's area: 1.44
```

#### Using 'this' in class member methods and constructors

When an object's member method is called, the object's reference, which can be thought of as the object's memory address, is passed to the method via the implicit "this" parameter 

The "this: keyword can also be  used ina constructor to invoke a different (overloaded) constructor.
  - Invoking other constructors is useful when a class' initialization routine is lengthy and avoids rewriting the same code

*Calling overloaded constructor using 'this' keyword*

    public class ElapsedTime {
      private int hours;
      private int minutes;

      // Overloaded constructor definition
      public ElapsedTime(int timeHours, int timeMins) {
          hours   = timeHours;
          minutes = timeMins;
      }
      
      // Default constructor definition
      public ElapsedTime() {
          this(0, 0);
      }
      
      // Other methods ...
    }

### 6.9 Java documentation for classes

The ***JavaDoc*** tool parses source code along with specifically formatted comments to generate documentation
  - The documentation generated by JavaDoc is known as an ***API*** for classes and class members.
  - API is short for ***application programming interface***

The specifically formatted comments for JavaDoc are called ***Doc comments***, which are multi-line comments consisting of all text enclosed between the /* and */ characters.
  - Doc comments are distinguished by the opening character /**, which inlcude two asterisks

*ElapsedTime.java*

    /**
    * A class representing an elapsed time measurement 
    * in hours and minutes. 
    * @author Mary Adams
    * @version 1.0
    */
    public class ElapsedTime {
      /**
        * The hours portion of the time
        */
      private int hours;
      
      /**
        * The minutes portion of the time
        */
      private int minutes;

      /**
        * Constructor initializing hours to timeHours and 
        * minutes to timeMins. 
        * @param timeHours hours portion of time
        * @param timeMins minutes portion of time
        */   
      public ElapsedTime(int timeHours, int timeMins) {
          hours   = timeHours;
          minutes = timeMins;
      }
      
      /**
        * Default constructor initializing all fields to 0. 
        */   
      public ElapsedTime() {
          hours = 0;
          minutes = 0;
      }
      
      /**
        * Prints the time represented by an ElapsedTime 
        * object in hours and minutes.
        */
      public void printTime() {
          System.out.print(hours + " hour(s) " + minutes + " minute(s)");
      }
      
      /**
        * Sets the time to timeHours:timeMins.
        * @param timeHours hours portion of time
        * @param timeMins minutes portion of time
      */
      public void setTime(int timeHours, int timeMins) {
          hours = timeHours;
          minutes = timeMins;
      }

      /**
        * Returns the total time in minutes.
        * @return an int value representing the elapsed time in minutes.
        */
      public int getTimeMinutes() {
          return ((hours * 60) + minutes);
      }
    }

*TimeDifference.java*

    import java.util.Scanner;

    /**
    * This program calculates the difference between two 
    * user-entered times. This class contains the 
    * program's main() method and is not meant to be instantiated.
    * @author Mary Adams
    * @version 1.0
    */
    public class TimeDifference {
      /**
        * Asks for two times, creating an ElapsedTime object for each, 
        * and uses ElapsedTime's getTimeMinutes() method to properly 
        * calculate the difference between both times.
        * @param args command-line arguments
        * @see ElapsedTime#getTimeMinutes()
        */
      public static void main(String[] args) {
          Scanner scnr = new Scanner(System.in);
          int timeDiff;     // Stores time difference
          int userHours;
          int userMins;
          ElapsedTime startTime = new ElapsedTime(); // Starting time
          ElapsedTime endTime = new ElapsedTime(); // Ending time

          // Read starting time in hours and minutes
          System.out.print("Enter starting time (hrs mins): ");
          userHours = scnr.nextInt();
          userMins = scnr.nextInt();
          startTime.setTime(userHours, userMins);
                  
          // Read ending time in hours and minutes
          System.out.print("Enter ending time (hrs mins): ");
          userHours = scnr.nextInt();
          userMins = scnr.nextInt();
          endTime.setTime(userHours, userMins);

          // Calculate time difference by converting both times to minutes
          timeDiff = endTime.getTimeMinutes() - startTime.getTimeMinutes(); 
          
          System.out.println("Time difference is " + timeDiff + " minutes");
      }
    }

A Doc comment associated with a class is written immediately before the class definition
  - Usually describes the main purpose

The tag section of the Doc comment may include block tags such as ***@author*** and ***@version*** to specify the class' author and version number respectively.

Each class also contains Doc comments describing member methods
Programmers can use the ***@param*** and ***@return*** block tags to specify a method parameter and method return value respectively

Generic block tags, such as ***@see*** and others described by the Javadoc specification, may be used to provide more information
  -Ex: the main() method's Doc comment use the @see block tag to refer to ElapsedTime's getTimeMinutes() method, as in **@see ElapsedTime#getTimeMinutes()**

### 6.10 Parameters of reference types

#### Methods with reference variables as parameters

A ***reference variable*** is a variable that points to, or refers to, an object or array

  - Internally, a reference variable stores a reference, or the memory location, of the object to which it refers

  - A programmer can only access the data or functionality provided by objects through the use of reference variables

Beecause reference variables store object locations and not the object data itself, passing a reference variable as a method argument assigns the argument's stored reference to the corresponding method parameter
  - Returning a reference variable returns an object reference 

#### Methods with wrapper class parameters

Instances of wrapper classes, such as Integer and Double, and the String class are defined as ***immutable***, meaning that a programmer cannot modify the object's contents after initialization; new objects must be created instead
  - The statement **Integer travelTime = 10;** initializes the variable travelTime with a reference to a new Integer object
  - Assigning the variable travelTime later with another value, such as **travelTime = 11;**, creates a completely new object and assigns travelTime to refer to the new object's reference

#### Methods with user-declared reference variables as parameters

A programmer-defined object is passed to a method by passing a reference(i.e. memory location) to the object.
  - The reference to the object is copied to the method's parameter, so the method can modify the object

Ex:
  - the DeviceOrientation class to represent the smartphone's orientation in terms of pitch and roll of a device such as a smartphone
  - This information is typically used to track a device for purposes such as changing screen orientation
  - The updateOrientation method modifies a DeviceOrientation object by calling the object's member methods that modify the object

        public class SmartPhoneTracking {
          public static void updateOrientation(DeviceOrientation device,double samplingPeriod, double gyroX, double gyroY) {
          
              double pitchAngle = device.getPitch() + (gyroX * samplingPeriod);
              double rollAngle = device.getRoll() + (gyroY * samplingPeriod);
          
              device.setPitch(pitchAngle);
              device.setRoll(rollAngle);
          }

          public static void main(String[] args) {
              DeviceOrientation phoneOrientation = new DeviceOrientation();

              phoneOrientation.setPitch(45.0);
              phoneOrientation.setRoll(0.0);
          
              updateOrientation(phoneOrientation, 0.01, 100.0, 10.0);
              System.out.println("iPhone's pitch: " + phoneOrientation.getPitch());
              System.out.println("iPhone's roll: " + phoneOrientation.getRoll());
          }
        }

A parameter of reference type allows object modification only through the object's public methods or fields

Assigning a different value to a parameter variable of reference type, as in **device = new DeviceOrientation();** assigns a new object to the reference variable, but does not modify the original object to which the variable first referred

### 6.11 Static fields and methods

#### Static fields

The keyword ***static*** indicates a variable is allocated in memory only once during a program's execution

Static variables reside in teh program's static memory region and have a global scope
  - static variables can be accessed from anywhere in the program

In a class, a ***static field*** is a field of the class instead of a field of each class object

Static fields are independent of any class object, and can be accessed without creating a class object
  - Static fields are declared and initialized in the class definition

Within a class method, a static field is accessed using the field name

##### Instance and class variable
*Static field are called **class variables**, and non-static fields are also called **instance variables***

#### Static member methods

A ***static member method*** is a class method that is independent of class objects. They are often used to access and mutate private static fields from outside the class
  - Since static methods are independent of class object, the **this** parameter is not passed to a static method method

### 6.14 Classes and ArrayLists

#### ArrayList of objects: A reviews program

A programmer commonly uses classes and ArrayList together.

*Review.java*

    public class Review {
      private int rating = -1;
      private String comment = "NoComment";
      
      public void setRatingAndComment(int revRating, String revComment) {
          rating = revRating;
          comment = revComment;
      }
      public int getRating() { return rating; }
      public String getComment() { return comment; }
    }

*ReviewSystem.java*

    import java.util.ArrayList;
    import java.util.Scanner;

    public class ReviewSystem {
    
      public static void main(String [] args) {
          Scanner scnr = new Scanner(System.in);
          ArrayList<Review> reviewList = new ArrayList<Review>();
          Review currReview;
          int currRating;
          String currComment;
          int i;
      
          System.out.println("Type rating + comments. To end: -1");
          currRating = scnr.nextInt();
          while (currRating >= 0) {
            currReview = new Review();
            currComment = scnr.nextLine(); // Gets rest of line
            currReview.setRatingAndComment(currRating, currComment);
            reviewList.add(currReview);
            currRating = scnr.nextInt();
          }
      
          // Output all comments for given rating
          System.out.println();
          System.out.println("Type rating. To end: -1");
          currRating = scnr.nextInt();
          while (currRating != -1) {
            for (i = 0; i < reviewList.size(); ++i) {
                currReview = reviewList.get(i);
                if (currRating == currReview.getRating()) {
                  System.out.println(currReview.getComment());
                }
            }
            currRating = scnr.nextInt();
          }
      }
    }

#### A class with an ArrayList: The Reviews class

A class can involve ArrayLists. 
  - The program below redoes the example above, creating a Reviews class for managing an ArrayList of Review objects
  - The Reviews class has methods for reading reviews and printing comments. The resulting main() is clearer than above
  - The Reviews class has a getter method that returns the average rating
  - The method computes the average rather than reading a private field, but the class user need not know how the method is implemented

*Review.java*

    public class Review {
      private int rating = -1;
      private String comment = "NoComment";
      
      public void setRatingAndComment(int revRating, String revComment) {
          rating = revRating;
          comment = revComment;
      }
      public int getRating() { return rating; }
      public String getComment() { return comment; }
    }

===============================================================
*Reviews.java*

    import java.util.ArrayList;
    import java.util.Scanner;

    public class Reviews {
      private ArrayList<Review> reviewList = new ArrayList<Review>();
      
      public void inputReviews(Scanner scnr) {
          Review currReview;
          int currRating;
          String currComment;
      
          currRating = scnr.nextInt();
          while (currRating >= 0) {
            currReview = new Review();
            currComment = scnr.nextLine(); // Gets rest of line
            currReview.setRatingAndComment(currRating, currComment);
            reviewList.add(currReview);
            currRating = scnr.nextInt();
          }
      }
      
      public void printCommentsForRating(int currRating) {
          Review currReview;
          int i;
      
          for (i = 0; i < reviewList.size(); ++i) {
            currReview = reviewList.get(i);
            if (currRating == currReview.getRating()) {
                System.out.println(currReview.getComment());
            }
          }
      }
      
      public int getAverageRating() {
          int ratingsSum;
          int i;
      
          ratingsSum = 0;
          for (i = 0; i < reviewList.size(); ++i) {
            ratingsSum += reviewList.get(i).getRating();
          }
          return (ratingsSum / reviewList.size());
      }
    }
===============================================================
ReviewSystem.java

    import java.util.ArrayList;
    import java.util.Scanner;

    public class ReviewSystem {
    
      public static void main(String [] args) {
          Scanner scnr = new Scanner(System.in);
          Reviews allReviews = new Reviews();
          String currName;
          int currRating;
      
          System.out.println("Type rating + comments. To end: -1");
          allReviews.inputReviews(scnr);
      
          System.out.println("\nAverage rating: ");
          System.out.println(allReviews.getAverageRating());
      
          // Output all comments for given rating
          System.out.println("\nType rating. To end: -1");
          currRating = scnr.nextInt();
          while (currRating != -1) {
            allReviews.printCommentsForRating(currRating);
            currRating = scnr.nextInt();
          }
      }
}

```console

Type rating + comments. To end: -1
5 Great place!
5 Loved the food.
2 Pretty bad service.
4 New owners are nice.
2 Yuk!!!
4 What a gem.     
-1

Average rating: 
3
================================
Type rating. To end: -1
5
 Great place!
 Loved the food.
1
4
 New owners are nice.
 What a gem.     
-1
```

#### Using Reviews in the Restaurant class

Programmers commonly use classes within classes
  - The program below uses a Restaurant class that contains a Reviews class so reviews can be associated with a specific restaurant

*Restaurant.java*

    import java.util.Scanner;

    // Review and Reviews classes omitted from the figure 

    public class Restaurant {
      private String name;
      private Reviews reviews = new Reviews();
      
      public void setName(String restaurantName) {
          name = restaurantName;
      }
          
      public void readAllReviews(Scanner scnr) {
          System.out.println("Type ratings + comments. To end: -1");
          reviews.inputReviews(scnr);
      }
      
      public void printCommentsByRating() { 
          int i;
          
          System.out.println("Comments for each rating level: ");
          for (i = 1; i <= 5; ++i) {
            System.out.println(i + ":");
            reviews.printCommentsForRating(i);
          }
      }
    }

*RestaurantReviews.java*

    import java.util.ArrayList;
    import java.util.Scanner;

    public class RestaurantReviews {
    
      public static void main (String [] args) {
          Scanner scnr = new Scanner(System.in);
          Restaurant ourPlace = new Restaurant();
          String currName;
      
          System.out.println("Type restaurant name: ");
          currName = scnr.nextLine();
          ourPlace.setName(currName);
          System.out.println();
      
          ourPlace.readAllReviews(scnr);
          System.out.println();
      
          ourPlace.printCommentsByRating();
      }
    }

```console
Type restaurant name: 
Maria's Healthy Food

Type ratings + comments. To end: -1
5 Great place!
5 Loved the food.
2 Pretty bad service.
4 New owners are nice.
2 Yuk!!!
4 What a gem.     
-1

Comments for each rating level: 
1:
2:
 Pretty bad service.
 Yuk!!!
3:
4:
 New owners are nice.
 What a gem.     
5:
 Great place!
 Loved the food.
```
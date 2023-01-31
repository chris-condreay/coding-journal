# Coding Journal
## Name: Chris Condreay
## Lab: Module 3
## Entries:
### January 31st, 2023

## 3.1 Objects: Introduction

### Grouping things into objects

An **object** is a group of data (variables) and operations that can be performed on that data (methods)

  - Programs commonly are not viewed as variables and functions/methods, but as objects

#### Abstraction / Information hiding

**Abstraction** means to have a user interact with an item at high-level, with lower-level internal details hidden from the user (**information hiding** or **encapsulation**)

  - Objects strongly support abstraction, hiding entire groups of methods and variables, exposing only certain methods to a user

An **abstact data type** (**ADT**) is a data type whose creation and update are constrained to specific well-defined operations. A class can be used to implement an ADT

## Using a Class

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
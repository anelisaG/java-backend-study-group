## 1. Generics 

## 1.1 What are Generics ?
Generics allow you to write classes, interfaces, and methods that can work with different data types while still maintaining type safety.
By using a type parameter (like <T>), they allow you to write reusable code that works with various objects without forcing you to duplicate code or rely on dangerous type casting.

This makes your code more flexible, reusable, and type-safe.

Instead of specifying a specific type, you use a type parameter such as T.
For example:

List<String> names = new ArrayList<>();

List → generic interface
String → the type being supplied
<String> → tells Java that this list should contain only String

## 1.2 Why do we use Generics ?
Code Reusability: Write one class or method that works with different data types.
Type Safety: Catch type errors at compile time instead of runtime.
Cleaner Code: No need for casting when retrieving objects.

Generic class example : You can create a class that works with different data types using generics:
___________________________________________________________________
  class Box<T> {
    T value; // T is a placeholder for any data type
  
    void set(T value) {
      this.value = value;
    }
  
    T get() {
      return value;
    }
  }
  
  public class Main {
    public static void main(String[] args) {
      // Create a Box to hold a String
      Box<String> stringBox = new Car<>();
      stringBox.set("Nisaan Magnite");
      System.out.println("Value: " + stringBox.get());
  
      // Create a Box to hold an Integer
      Box<Integer> intBox = new Box<>();
      intBox.set(50);
      System.out.println("Value: " + intBox.get());
    }
  }
___________________________________________________________________

## 1.3 What does <T> mean?

You will see this everywhere: <T>
T is a type parameter.
Think of it as: "I don't know the type yet. The person using this class/method will tell me."
___________________________________________________________________
For example:
class Box<T> {
    private T value;
}

When we create: Box<String>
Java replaces T with String.
Conceptually:
class Box<String> {
    private String value;
}

And:
Box<Integer>

means T becomes Integer.
_____________________________________________________________________

## 1.4 Types of Generics 

## The 3 Primary Structures Using Generics
You can implement generics across three main areas in Java code:

• Generic Classes: A class that can operate on a parameterized type. The type parameter is specified within angle brackets (<>) after the class name.java
  class Box<T> {
      private T data;
      public void set(T data) { this.data = data; }
      public T get() { return data; }
  }
  
• Generic Interfaces: Just like classes, interfaces can accept type parameters. This is used extensively in the Java Collection Framework (e.g., List<E> or Map<K, V>).java
interface Repository<T> {
    void save(T item);
}

• Generic Methods: A method can have its own generic type.
 example:
 
  public static <T> void printValue(T value) {
      System.out.println(value);
  }

  Now we can pass different types:
  printValue("Hello");
  printValue(100);
  printValue(10.5);
  printValue(true);
  
  The method works with all of them.
  
Notice <T> appears before the return type:
public static <T> void printValue(T value) //That tells Java this method introduces a generic type called T

## Bounded Generics
Bounded generics are generic type parameters that restrict the types of arguments you can pass into a generic class, interface, or method. Instead of letting a type parameter accept any arbitrary object type, a bounded generic forces the type argument to be a specific class or a subtype/implementer of a given class or interface.

- Bounds are specified using the extends keyword.
- A type parameter can have a single bound or multiple bounds.

Syntax
<T extends superClassName>

Note: In generics, extends means that T can be any subclass of the specified type or the type itself. It sets an inclusive upper bound for the type parameter.

Sometimes you don't want to allow any type. You can put a restriction on T.
For example:
public static <T extends Number> void printNumber(T number) {
    System.out.println(number);
}

Now T must extend Number.
So these work:
printNumber(10);
printNumber(10.5);
printNumber(100L);

Because:
Integer  → Number
Double   → Number
Long     → Number

But:
printNumber("Hello"); // ❌

because String does not extend Number.
This is called a bounded type parameter.


## LETS DO EXAMPLE OF A BOUNDED GENERIC CLASS TOGETHER !!


## 1.5 Wildcards <?>

## 2 Enums

## What are Enums ?
  In Java, an enum is essentially a special type of class that contains a fixed set of constants.
  Enums are often used in cases where we know all possible values at compile time. Examples
  include:
  ● Days of the week (SUNDAY, MONDAY, TUESDAY, etc.)
  ● Directions (NORTH, SOUTH, EAST, WEST)
  ● Status codes (RUNNING, FAILED, SUCCESS, etc.)
  Enums are particularly useful for situations where a variable can only have one of a small set
  of predefined values

## Real-world Example of Enums
  Consider how websites return error codes like 404 Page Not Found or 500 Internal Server
  Error. These codes are constants used to indicate specific conditions, much like Java's enums.
  In Java, enums allow us to define custom constants for scenarios like:
  ● Days of the week
  ● Status codes
  ● Seasons (WINTER, SPRING, SUMMER, FALL)

## Defining an Enum in Java
  You can define an enum using the enum keyword. For example:
  
  enum Status {
    RUNNING, 
    FAILED , 
    PENDIND, 
    SUCCESS;
  }
  Here, the Status enum has four constants: RUNNING, FAILED, PENDING, and SUCCESS.
  Example: Using Enums in Code
  
   public class Demo {
      public static void main(String[] args){
         Status status = Status.RUNNING;
         System.out.println(status); // Output:RUNNING
      }
   }
  In this example, the status variable is of type Status (an enum), and it holds the value
  RUNNING. You can think of Status.RUNNING as an object representing the RUNNING
  constant.

## Characteristics of Java Enums
  ● Named constants: Enum constants are implicitly public, static, and final. This means
  they are constants that cannot be changed.
  ● Object-oriented: Although enums look simple, they are full-fledged objects in Java.
  You can define constructors, instance variables, methods, and even implement
  interfaces in enums.
  ● Indexing: Enum constants have an implicit order, starting from 0. You can retrieve
  the index of an enum constant using the ordinal() method.

## Methods in Enums
  Java provides several useful methods for enums:
  1. ordinal() Method
  This method returns the index of the enum constant. The first constant is assigned an
  index of 0, the second 1, and so on.
   System.out.println(Status.RUNNING.ordinal()); // Output: 0
  2. values() Method
  This method returns an array of all enum constants. It is helpful for iterating through
  all possible values.

Example:

 public class Demo {
      public static void main(String[] args){
         Status[] statuses = Status.values();
         for (Status s: statuses){
            System.out.println(s + " at index "+ s.ordinal());
         }
      }
   }

Output:

RUNNING at index 0
FAILED at index 1
PENDING at index 2
SUCCESS at index 3


## Conclusion
Enums in Java are powerful and versatile tools. They allow you to define a set of named
constants, making code more readable and maintainable. With methods like ordinal() and
values(), enums offer additional functionality that can be very useful when managing
predefined constants.

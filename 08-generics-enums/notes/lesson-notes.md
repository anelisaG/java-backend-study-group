## Generics 

## What are Generics ?
Generics allow you to write classes, interfaces, and methods that can work with different data types while still maintaining type safety.
By using a type parameter (like <T>), they allow you to write reusable code that works with various objects without forcing you to duplicate code or rely on dangerous type casting.

This makes your code more flexible, reusable, and type-safe.

Instead of specifying a specific type, you use a type parameter such as T.
For example:

List<String> names = new ArrayList<>();

List → generic interface
String → the type being supplied
<String> → tells Java that this list should contain only String

## Why do we use Generics ?
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

## What does <T> mean?

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

## Types of Generics 

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


TO BE CONTINUED

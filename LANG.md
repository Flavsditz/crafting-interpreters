# The LOX Language

## Dynamically typed

## Automatic memory management - GC'd

## Data Types
- Booleans ("true" and "false")
- Numbers - double precision floating point. No Hex, Octals or Binary. Just integers (1234) and decimals (12.34)
- Strings - enclosed in double quotes
- Nil (written "nil")

## Expressions 
Expressions produce values

- Arithmetic (only works on numbers)
    - Addition ("+")
    - Subtraction ("-")
    - Multiplication ("*")
    - Division ("/")
    - Negation ("-" in front of a number)

- Comparisoni (only for numbers) and equality (numbers and types)
    - Less than ("<")
    - Less than or equal ("<=")
    - Greater than (">")
    - Greather than or equal (">=")
    - Equality ("==")
    - Inequality ("!=")

- Logical operators
    - Not ("!")
    - AND ("and") - short circuit
    - OR ("or") - short circuit

- Precedence and grouping
    - work like in C 
    - grouping is done with parenthesis

## Statements
Statements produce effects

An expression followed by a semicolon makes a statement.
If you want to pack several statements into a single one you can pack them in a block (inside "{}").

## Variables
Declare them using the **var** keyword.
If you don't initialize it right away it defaults to **nil**.

## Control Flow
- IF statement
- WHILE loop
- FOR loop

## Functions
- Define functions with **fun**
- Parentheses are mandatory to call a function.
- You can define a return value using the **return** statement
- If no return is defined it implicitly returns **nil**.
- Are first-class, i.e. they are real values that can be passed around.

## Closures
-  Due to functions being first class you can have some interesting functionality where a function is declared inside another but uses values from the parent function (thus outside of its own context). These are called closures.

## Classes
- This allows us to bundle "things" together under a name
- Allow us to have functions scoped to an object and thus not conflict with others with a similar name, avoiding having to create specific method names for different types (e.g. hashCopy vs arrayCopy vs vectorCopy, etc).
- Are also first class
- Can define a constructor that is called automatically upon instantiation, with the name `init()`.

### Instances
- Instantiation happens by simply calling the class like a function i.e. the class name followed by parenthesis: "MyClass()".
- Like other dynamic languages you can freely add properties to an object by calling `myobject.newProp = "value"`
- If you want to access a field or method within the object you use the keywork `this`.

### Inheritance
- Supports **single** inheritance 
- Upon class declaration you can specify a parent by using the `<`(less than) operator
- Example: `class Brunch < Breakfast {...}`
- Every method defined in the superclass is available to the subclasses
- One uses `super` to call methods from the superclass.


## The standard library
This is the set of functionality that is implemented directly in the interpreter and that all user-defined behaviour is built on top of.

This is kept really simple here and we only implement `print`and the `clock` statements.

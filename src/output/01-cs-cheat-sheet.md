# C# Cheat Sheet

© thecodingguys 2013

A cheat sheet to the C# language, ideal for newcomers to the language. For more visit <http://www.thecodingguys.net>.

## License

This work is licensed under the Creative Commons Attribution-NonCommercial-NoDerivs 3.0 Unported.

- You may not alter, transform, or build upon this work.
- You may not use this work for commercial purposes.
- You are free to copy, distribute and transmit the work.

## Language Basics

### Introduction

C# is a powerful Object Orientated language, for those coming from Java or C++ you should be able to pick up the syntax for C# quickly. A few points:

- The language is case-sensitive (So `A` and `a` are different)
- Lines terminate with semi-colons
- Code is put in code blocks `{ }`
- Inline comments start with `//`
- Block comments start with `/* */`
- XML comments start with `///`

### Variables

To declare a variable you specify the data type and variable name followed by a value.

**Syntax**

```csharp
DataType variableName = value;
```

**Naming Rules**

- Variables must start with underscore or letter
- Variables cannot contain spaces
- Variables can contain numbers
- Cannot contain symbols (except underscore)

**Example**

```csharp
string Name = "thecodingguys";
int Year = 2013;
```

These two variables are used throughout the examples.

### Arrays

Arrays are similar to variables, but can hold more than one value.

**Syntax**

```csharp
DataType[] ArrayName = { Comma Separated Values }             // Array of any size
DataType[] ArrayName = new DataType[3] { Comma Separated Values } // Expects 3 values
```

**Example**

```csharp
string[] MyGamesOf2013 = {"GTAV", "Battlefield3"};
string[] MyMoveisOf2013 = new string[3] {"The Amazing Spiderman", "The Expendables 2",
    "Rise of the planet of the apes"};
```

### Strings

#### Concatenation

Concatenation is done through the `+` operator.

```csharp
Console.WriteLine("Hello " + "World");
```

#### New Line

```csharp
Console.WriteLine("Hello \n" + "World");
```

#### String.Format

Formats an object, you specify the formatting you wish to perform, the following formats an integer and displays the currency symbol.

```csharp
Console.WriteLine(string.Format("{0:C}", 5));
```

Depending on your computers regional settings you will see £5.00 displayed (you'll see your countries currency symbol). The `0:C` is the formatting we wish to do, in this case it means format the first parameter (`0`) and show a currency sign.

## Conditional Statements

### If Statements

`if` statement is used to execute code based on a condition. The condition must evaluate to true for the code to execute.

**Syntax**

```csharp
if (true)
{

}
```

**Example**

```csharp
if (Year > 2010)
{
    Console.WriteLine("Hello World!");
}
```

### If Else Statements

If a condition does not evaluate to true you can use an `if else` statement to execute other code.

**Example**

```csharp
if (Year > 2015)
{
    Console.WriteLine("Hello World!");
}
else
{
    Console.WriteLine("Year is: " + Year);
}
```

### Switch Statement

Similar to the If Else statement, however it has these benefits:

- Much easier to read and maintain
- Much cleaner than using nested if else
- It only evaluates one variable

**Syntax**

```csharp
switch (switch_on)
{
    default:
}
```

**Example**

```csharp
switch (Year)
{
    case 2013:
        Console.WriteLine("It's 2013!");
        break;
    case 2012:
        Console.WriteLine("It's 2012!");
        break;
    default:
        Console.WriteLine("It's " + Year + "!");
        break;
}
```

The `break` keyword is required as it prevents case falling.

## Loops

### While Loop

Continuously loops code until the condition becomes false.

**Syntax**

```csharp
while (true)
{
}
```

**Example**

```csharp
while (Year >= 2013)
{
    if (Year != 2100)
    {
        Console.WriteLine(Year++);
    }
    else
    {
        break;
    }
}
```

Make sure your condition evaluates to false at some point otherwise the loop is endless and it can result in errors.

### For Loop

Similar to the While Loop, but you specify when the loop will end.

**Syntax**

```csharp
for (int i = 0; i < length; i++)
{
}
```

**Example**

```csharp
for (int i = 0; i <= 100; i++)
{
    Console.WriteLine(i);
}
```

This prints out 1 to 100. The expression can be easily broken down like this:

- `i = 0;`
- `i` is less than or equal to 100? (True)
- Increment `i` by 1

When `i` reaches 100 it will stop because `i` will no longer be less than 100 and will equal 100 so the condition is false.

### For Each

The for each loop is used to loop around a collection (such as an array).

**Syntax**

```csharp
foreach (var item in collection)
{

}
```

**Example**

```csharp
foreach (string movie in MyMoveisOf2013)
{
    Console.WriteLine(movie);
}
```

Outputs all the elements in the `MyMoviesOf2013` array.

## Advanced – Exceptions, Methods & Classes

### Exceptions

To catch any exceptions which are likely to occur you use a try catch block.

**Syntax**

```csharp
try
{

}
catch (Exception)
{
    throw;
}
```

**Example**

```csharp
try
{
    string result = "k";
    Console.WriteLine(Convert.ToInt32(result) + 10);
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
```

The above code results in a format exception, because you can't convert `K` to a number.

### Methods

**Syntax**

```csharp
public void MethodName()
{
    // Does not return a value
}

public static void MethodName()
{
    // Does not return a value, the class does not need to be initialized
    // for this method to be used.
}

public static DataType MethodName()
{
    // Requires a value to be returned, class does not need to be
    // initialized for this method to be used.
}
```

**Example**

```csharp
public static void WelcomeUser()
{
    Console.WriteLine("Hello Guest!");
}
```

#### Passing Parameters

```csharp
public static void WelcomeUser(string Name)
{
    Console.WriteLine("Hello " + Name + "!");
}
```

Since both methods have the same name and different parameters (one takes no parameters and the other one does) this is said to be an overloaded method.

#### Returning Data

```csharp
public static DateTime Tomorrow()
{
    return DateTime.Now.AddDays(1);
}
```

All the examples above are static, this allows the use of methods without initializing the class. You can read more about Classes and Methods. Also public methods are available outside of the current class, private methods are only available in the current class.

### Classes

**Syntax**

```csharp
class MyClassName
{

}
```

**Example**

```csharp
class MyCar
{
    public void Manufacturer(string Manf)
    {
        Console.WriteLine(Manf);
    }
}
```

To use the method in the class, the class must be initialized first:

```csharp
MyCar NewCar = new MyCar();
NewCar.Manufacturer("Audi");
```

If the method was declared static you could simply do this:

```csharp
MyCar.Manufacturer("Audi");
```

Static methods are useful, make sure you are using the right design for your classes and methods. A good example is the Math class, to perform simple calculations you do not want to be initializing the class all the time, that's why most methods are static.

## Summary

This cheat sheet sums up the basics of C#, for experienced developers who are learning C# and users who already know programming basics. For more visit <http://www.thecodingguys.net>.

# Getting Started

A list of C# features.

# Table of Contents

-   [Getting Started](#getting-started)
-   [Table of Contents](#table-of-contents)
-   [Features](#features)
    -   [C# 1.0](#c-10)
        -   [Ternary Operator](#ternary-operator)
            -   [Code Example](#code-example)
    -   [C# 7.0](#c-70)
        -   [Switch Expression - Pattern Matching Expressions](#switch-expression---pattern-matching-expressions)
            -   [Code Example](#code-example)
    -   [C# 8.0](#c-80)
        -   [Interface Default Implementation](#interface-default-implementation)
            -   [Code Example](#code-example)
    -   [C# 9](#c-9)
        -   [Record Type](#record-type)
            -   [Code Example](#code-example)
        -   [Top Level Statement](#top-level-statement)
            -   [Code Example](#code-example)
    -   [C# 10](#c-10)
        -   [Record Struct](#record-struct)
            -   [Code Example](#code-example)
        -   [Global Using Directives](#global-using-directives)
            -   [Code Example](#code-example)
        -   [File-scoped Level Namespace](#file-scoped-level-namespace)
            -   [Code Example](#code-example)
    -   [C# 11](#c-11)
        -   [Interfaces static modifiers](#interfaces-static-modifiers)
            -   [Code Example](#code-example)

<small><i><a href='https://luciopaiva.com/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>

# Features

## C# 1.0

### Ternary Operator

1. [Ternary Conditional Operator](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/conditional-operator)

#### Code Example

```
// Ternary Operator Syntax
condition ? true : false
condition ? consequent : alternative

// Sample
var random = Convert.ToBoolean(new Random().Next(0, 2));
var value = random ? "This is true" : "This is false";
```

## C# 7.0

### Switch Expression - Pattern Matching Expressions

1. [Pattern Matching Overview](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/functional/pattern-matching)
2. [Pattern Matching Expressions](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/switch-expression)

#### Code Example

```
var booleanValue = Convert.ToBoolean(new Random().Next(0, 2));
var booleanString = booleanValue switch
{
    false => "This is False",
    true => "This is True",
    // Note:
    // - This just a sample, do not mind the error "It has already been handle by the previous arm of the switch expression" the code below generated.
    _ => "This is neither or discarded",
};
```

## C# 8.0

### Interface Default Implementation

1. [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/proposals/csharp-8.0/default-interface-methods)
2. [Default Implementations](https://devblogs.microsoft.com/dotnet/default-implementations-in-interfaces/)

#### Code Example

```
interface ILogger
{
    void Log(LogLevel level, string message);
    void Log(Exception ex) {
        Log(LogLevel.Error, ex.ToString());
    }
}
```

## C# 9

### Record Type

1. [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/whats-new/tutorials/records) - A reference type that uses value-based equality on it's fields.

#### Code Example

`example.cs`

```
public record Example
{
    public int A
    {
        get;
        set;
    }

    public int B
    {
        get;
        set;
    }

    public int c;

    public Example(int cvalue)
    {
        c = cvalue;
    }
}
```

---

`main.cs`

```
var a = new Example(-1)
{
    A = 1,
    B = 2
};

var b = new Example(-1)
{
    A = 1,
    B = 2
};

// expected output:
// true
Console.WriteLine(a == b);
```

### Top Level Statement

1. [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-9#top-level-statements)

#### Code Example

`before_top_level_statement`

```
using System;

namespace Project
{
   public class Program
   {
      public static void Main(List<string> args)
      {
         Console.WriteLine("Hello, World!");
      }
   }
}
```

---

`after_top_level_statement.cs`

```
// there is no need to add `using System` as top level statement is part of a global namespace and BCL are in the global namespace
Console.WriteLine("Hello, World!");
```

## C# 10

### Record Struct

1. [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/record)

-   A value type record.
-   The main difference better `public record A` and `public record struct A` is that the `public record A` is a reference type and `public record struct A` is a value type.

#### Code Example

`example1.cs`

```
public record struct Example
{
    public int A
    {
        get;
        set;
    }
}
```

### Global Using Directives

1. [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-10#file-scoped-namespace-declaration)

#### Code Example

`class_with_namespace.cs`

```
namespace Example;

public class OriginalExample {}
```

---

`class_with_another_A_namespace.cs`

```
// Note:
// - `using global Example`
using global Example;

namespace ExampleA;

public class ExampleCopyA
{
    public OriginalExample original;
}
```

---

`class_with_another_B_namespace`

```
namespace ExampleB;

public class ExampleCopyB
{
    // Note:
    // - I didn't add a `using Example` in here, it's because the `namespace Example` is already added to the global namespace by another .cs file
    public OriginalExample original;
}

```

### File-scoped Level Namespace

1. [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-10#file-scoped-namespace-declaration)

#### Code Example

`before_filescope_level_namespace.cs`

```
namespace Project
{
   // Class Here
}
```

---

`after_filescore_level_namespace.cs`

```
namespace Project;

// Class Here
```

## C# 11

### Interfaces static modifiers

1. [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/whats-new/tutorials/static-virtual-interface-members)
2. [Specification](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/proposals/csharp-11.0/static-abstracts-in-interfaces)

#### Code Example

##### Static Abstract

`static_abstract.cs`

```
// Example:
// - static abstract
public interface IExample<T>
{
    public static abstract T Zero
    {
        get;
    }
}
```

`using_static_abstract.cs`

```
var aInt = new[] { 1, 2, 3 };
var aDouble = new[] { 1, 2, 3 };

var sumInt = Sum(aInt);
var sumDouble = Sum(aDouble);

T Sum<T>(T[] x) where T : INumber<T>
{
	T sum = T.Zero;

	foreach (var temp in x)
	{
		sum += temp;
	}

	return sum;
}
```

##### Static Virtual

`static_virtual.cs`

```
// Example:
// - static virtual
public interface IExample
{
    public static virtual void Sample()
    {
        Console.WriteLine("Interface Sample");
    }
}
```

---

`concrete_static_virtual_a.cs`

```
public class ConcreteStaticVirtualA : IExample
{

}
```

---

`concrete_static_virtual_b.cs`

```
public class ConcreteStaticVirtualB : IExample
{
    public static void Sample()
    {
        Console.WriteLine("Concrete B");
    }
}
```

---

`using_static_virtual.cs`

```
// Expected Output:
// - Interface Sample
Test<ConcreteStaticVirtualA>();

// Expected Output:
// - Concrete B
Test<ConcreteStaticVirtualB>();

void Test<T>() where T : IExample
{
	T.Sample();
}
```

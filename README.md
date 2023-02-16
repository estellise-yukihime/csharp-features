## Getting Started

A list of C# features.

## Table of Contents

1. [C# 1.0](#c-10)
   1. [Ternary Operator](#ternary-operator)
2. [C# 7.0](#c-70)
   1. [Switch Expression - Pattern Matching Expressions](#switch-expression---pattern-matching-expressions)
2. [C# 9](#c-9)

## Features

### C# 1.0

#### Ternary Operator

1. [Ternary Conditional Operator](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/conditional-operator)

##### Code Example
```
// Ternary Operator Syntax
condition ? true : false
condition ? consequent : alternative

// Sample
var random = Convert.ToBoolean(new Random().Next(0, 2));
var value = random ? "This is true" : "This is false";
```

### C# 7.0

#### Switch Expression - Pattern Matching Expressions

1. [Pattern Matching Overview](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/functional/pattern-matching)
2. [Pattern Matching Expressions](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/switch-expression)

##### Code Example

```
var booleanValue = Convert.ToBoolean(new Random().Next(0, 2));
var booleanString = booleanValue switch
{
    false => "This is False",
    true => "This is True",
    // This just a sample, do not mind the error "It has already been handle by the previous arm of the switch expression
    _ => "This is neither or discarded",
};
```

### C# 9

#### Top Level Statements

1. [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-9#top-level-statements)

##### Code Example
```
// before_top_level_statements.cs
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

---

// after_top_level_statement.cs
// --
// there is no need to add `using System` as top level statement is part of a global namespace and BCL are in the global namespace
Console.WriteLine("Hello, World!");
```

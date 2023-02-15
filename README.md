## Getting Started

A list of C# features.

## Table of Contents

1. [C# 7.0](#c-70)
   a. [Switch Expression - Pattern Matching Expressions](#switch-expression---pattern-matching-expressions)

## Features

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

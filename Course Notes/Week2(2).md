# Week2(2)

Course Name: Introduction to Computation
Date: September 28, 2021
Number: 6
简介: Function Application&Lists and Tuples

## 【Ch2】Types and Functions(2)

**Function Definition**

Function Declaration and Definition：

```haskell
--Signature
double :: Int -> Int
{-
--double：Function Name
--x：Formal Parameter
--x + x：Function Body
-}
double x = x + x
```

Calling a Function:

```haskell
--3：Actual Parameter
> double 3
6
```

**Function Application**

To apply a function in Haskell, we write the name of the function followed by its arguments.

```haskell
> odd 3
True
```

*Notice：We do not use parentheses or commas to group or sepearate the arguments to a function*

```haskell
> compare 2 3
LT
```

Function application has higher precedence than using operators, so the following two expressions have the same meaning.

```haskell
> (compare 2 3) == LT
True
> compare 2 3 == LT
True
```

However, we must use parentheses to indicate how we want a complicated expression to be parsed

```haskell
> compare (sqrt 3)(sqrt 6)
LT
```

If we omit the parentheses, it looks like we are trying to pass four arguments to the function compare, instead of the two it expects.

**Composite Data Types：Lists and Tuples**

Composite Data Type：A composite data type is constructed from other types.

*Lists*

A list type is an unbounded-sized collection of values, which only contains elements of  the same type

```haskell
> let a = ['H', 'E', 'L', 'L', 'O']
> a
"HELLO"

```

The head function returns the first element of a list.

```haskell
> head [1,2,3,4]
1
```

In counterpart, tail returns all but the head of a list

```haskell
> tail [1,2,3,4]
[2,3,4]
> tail[]
*** Exception: Prelude.tail: empty list
```

Because a list can take any type as its element, we call the list type polymorphic. We will cover this in future chapters.

*Tuples*

A tuple is a fixed-size collection of values, where each value can have a different type.

Application of tuple:We have two pieces of information, publication year and title, about a book, and we want to keep track of its information. We can store the information in a tuple

```haskell
> (1964, "Book")
(1964, "Book")
```

To examine the type of a tuple:

```haskell
> :type (True, "hello", 3)
(True, "hello", 3) :: (Bool, [Char], Int)
```

There is a special type, (), that actas as a tuple of zero elements. This type has only one value, also written (). Both the type and the value are usually pronounced "unit", it is somewhat similar to void in C.

A 2-tuple has two elements, and is usually called a pair. A 3-tuple(sometimes called a triple) has three elements and so on.

*Lists vs. Tuples*

- Lists:
    1. Lists does not have a fixed size
    2. Lists can only contain values of the same type
    3. Lists must be declared using brackets（[ ]）
- Tuples:
    1. Tuples does have a fixed size
    2. Tuples can contain values of any type（You can put values of different types in a tuple）
    3. Tuples can be declared using paratheses（( )）
# Week 4 FP(2)

Course Name: Introduction to Computation
Date: October 12, 2021
Number: 11

## 【Ch3】Defining Types, Streamlining Functions

**Exhaustive Patterns and Wild Cards**

When writing a series of patterns, it's important to cover all of a type's constructors.

*For example, if we are inspecting a list, we should have one equation that matches the non-empty constructor (:), and one that matches the empty-list constructor [ ].*

See the following bad example

```haskell
badExample (x : xs) = x + badExample xs
```

If we apply this to a value that it cannot match, we'l get an error at runtime.

![1.PNG](https://github.com/KingArthur0205/Learn-Haskell/blob/main/Images/Exhaustive%20Types.png)

**Parameterised Types**

We can use the type Maybe to represent a value that could be either present or missing.

```haskell
data Maybe a = Just a |Nothing
```

Maybe is a polymorphic, or generic, type. We give the Maybe type constructor a parameter to create a specific type, such as Maybe Int or Maybe [Bool].

**Recursive Types**

Our familiar list type is recursive: it's defined in terms of itself.

We will create our list-like type, use Cons in place of the (:) constructor, and Nil in place of [ ].

```haskell
data List a = Cons a (List a) | Nil
	deriving (Show)
```

Because Nil has a List type, we can use it as a prameter to Cons

```haskell
> Cons 0 Nil
Cons 0 Nil
```

Use this to create our own list-like type:

```haskell
fromList [] = Nil
fromList ( x : xs ) = Cons x (fromList xs)
```

One famous example of a recursive type is the definition of a binary tree type

```haskell
data Tree a = Node a (Tree a) (Tree a) | Empty
	deriving (Show)
```

Use this to construct a tree

```haskell
simpleTree = Node "Parent" (Node "LChild" Empty Empty) (Node "RChild" Empty Empty)
```

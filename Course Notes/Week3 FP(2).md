# Week 3 FP(2)

Course Name: Introduction to Computation
Date: October 5, 2021
Number: 9

## 【Ch3】Defining Types, Streamlining Functions(2)

**Construction and Deconstruction**

If we apply a value constructor to build a value. The expression *Book 9 "Arthur"* applies the Book constructor to the *values 9, "Arthur"* to produce a new value of type BookInfo.

```haskell
--Definition of this data type can be found in the previous notes.
bookone = Book 9 "Arthur"
```

When we pattern match against the Book constructor, we reverse the construction process.

- The match will succeed, because the constructor in the value matches the one in our pattern.
- The varaible id will be bound to 9
- The variable name will be bound to "Arthur"

Because pattern matching acts as the inverse of construction, it's sometimes referred to as deconstruction.

**Further Adventures**

Now that we have created a data type with different values. *How do we extract the values from such data type?*

We can extract values from a BookInfo as follows:(Called the Accessor Functions)

```haskell
bookId (Book id title) = id
bookTitle (Book id title) = title
```

If we run it in Shell:

```haskell
> let a = Book 1 "Arthur"
> bookId a
1
> bookTitle a
"Arthur"
> bookId (Book 2 "Arthur2")
2
```

The compiler can infer the types of the accessor functions based on the constructor we are using in our pattern:

```haskell
> :type bookId
bookId :: BookInfo -> Int
> :type bookTitle
bookTitle :: BookInfo -> String
```

IF we use a literal value in a pattern, the corresponding part of the value we're matching against must contain an indentical value.

For instance, the pattern (3:xs) first of all checks that a value is a non-empty list, by matching against the (:) constructor. It also ensures that the head of the list has the eaxct value 3. If both of these conditions hold, the tail of the list will be bound to the variable xs.

**The Wild Card Pattern**

We can indicate that we don't care what is present in part of a pattern. The notation for this is the underscore character "_", which we call a wild card.

```haskell
nicerId (Book id _) = id
nicerTitle (Book _ title) = title
```

An advantage of wild cards is that a Haskell compiler can warn us if we introduce a variable name in a pattern, but do not use it in a function's body. Defining a variable, but forgetting to use it, can often indicate the presence of a bug.

If we use a wild card instead of a variable that we do not intend to sue, the compiler won't complain.

**Use of Wild Card Pttern**

If we want to calculate the sum in a list. The code would be as following:

```haskell
sum (x:xs) = x + sum xs
sum [] = 0
```

If we need to provide a default behavior in cases where we don't care about specific constructors, we can use a wild card pattern

```haskell
sum (x:xs) = x + sum xs
sum _ = 0
```

**Record Syntax**

Writing accessor functions for each of a data type's components can be repetitive and tedious.

```haskell
nicerId (Book id _) = id
nicerTitle (Book _ title) = title
```

In Haskell, we can define a data type , and accessors for each of its components, simultaneously.

```haskell
type Address = String
type CustomerId = Int

data Customer = Customer {
	customerId :: CustomerId,
	customerName :: String,
	customerAddress :: Address
} deriving(Show)
```

Then, we call up the accessor functions to get each value:

```haskell
> let a = Customer 3 "A" "B"
> customerId a
3
> customerName a
"A"
> customerAddress a
"B"
```

This style of defining a data type is exactly identical in meaning to the following, more familar form:

```haskell
data Customer = Customer Int String [String]
  deriving (Show)

customerID :: Customer -> Int
customerID (Customer id _ _) = id

customerName :: Customer -> String
customerName (Customer _ name _) = name

customerAddress :: Customer -> [String]
customerAddress (Customer _ _ address) = address
```

Record syntax adds a more verbose notation for creating a value:

```haskell
customer1 = Customer {
	customerId = 271828,
	customerAddress = ["Balabala"],
	customerName = "Arthur"
}
```

Also, when we define a type using record syntax, it changes the way the type's values are printed.

If we have the following code:

```haskell
type Address = String
type CustomerId = Int

data Customer = Customer {
    customerId :: CustomerId,
    customerName :: String,
    customerAddress :: Address
} deriving(Show)

data CustomerA = CustomerA CustomerId String Address
    deriving(Show)

customer1 = Customer {
    customerId = 1,
    customerName = "Arthur",
    customerAddress = "Balabala"
}
```

Old way of printing:

![1.PNG](Week%203%20FP(2)%20276b7a1a75ec4795bff31b9de77dbf4f/1.png)

New way of printing:

![2.PNG](Week%203%20FP(2)%20276b7a1a75ec4795bff31b9de77dbf4f/2.png)
# Week3 FP

Course Name: Introduction to Computation
Date: October 4, 2021
Number: 8

## 【Ch3】Defining Types, Streamlining Functions

**Defining a new data type**

We define a new data type using the *data* keyword.

See the following code for an example tol construct a BookInfo data type:

```haskell
data BookInfo = Book Int String [String]
    deriving (Show)
```

- The *BookInfo* after the data keyword is the name of our new type.
    
    We call BookInfo a type constructor. Once we have defined a type, we will use its type constructor to refer to it.
    
    A type constructor must start with a capital letter.
    
- The *Book* that follows is the name of the value constructor.
    
    We use this to create a value of the *BookInfo* type.
    
- After *Book, the Int, String, and [String]* that follow are the components of the type
    
    A componenet serves the same purpose in Haskell as a field in a structure or class would in another language.
    

Even though the following *MagazinInfo* type has the same structure as our BookInfo type, Haskell treats the types as distinct because their type and value constructors have different names.

```haskell
data MagazineInfo = Magazine Int String [String]
    deriving (Show)
```

*Notice: The name of the type constructor(BookInfo) cannot be the same as that of the value constructor(Book).*

**Type Synonyms**

We can introduce a synonym for an existing type at any time, to give a type a more descriptive name.

The type keyword introduces a type synonym. The new name is on the left of the =, with the existing name on the right.

Type synonyms are purely for making code more reliable.

```haskell
type BookRecord = (BookInfo, BookReview)
```

**Algebraic Data Types**

The familiar *Bool* is the simplest common example of a category of type called an algebraic data type. An algebraic data type can have more than one value constructor.

```haskell
data Bool = False | True
```

The Bool type has two value constructors, True and False. Each value constructor is seperated in the definition by a | character, which we can read as "or": we can struct a Bool that has the value True, or the value False.

When a type has more than one value constructor, they are usually referred to as alternatives or cases.

Each of an algebraic data type's value constructors can take zero or more arguments. See the following code as an example:

```haskell
type CardHolder = String
type CardNumber = String
type Address = [String]

data BillingInfo = CreditCard CardNumber CardHolder Address
	| CashOnDelivery
	| Invocie CustormerID
		deriving (Show)
```

**The Enumeration**

In C, enumeration types look like following:

```c
enum color {
	red,
	orange,
	yellow,
	green
};
```

In Haskell, the following is equivalent:

```haskell
data Color = Red
	| Orange
	| Yellow
	| Green
		deriving (Show)
```

**Pattern Matching**

If we have a value of some type, there are two things we would like to be able to do.

- If the type has more than one value constructor, we need to be able to tell which value constructor was used to create the value.
- If the value constructor has data components, we need to be able to extract those values.

See the following code for an example:

```haskell
sumList (x:xs) = x + sumList xs
sumList [] = 0
```

The list notation [1,2] is shorthand for the expression (1:(2:[])). We begin by trying to match the pattern in the first equation of the definition of sumList.

In the (x:xs) pattern, the ":" is the familiar list constructor. We are not using it to match against a value, not to construct one. 

The value (1:2:[])) was constructed with :, so the constructor in the value matches the constructor in the pattern. We say that the pattern matches.
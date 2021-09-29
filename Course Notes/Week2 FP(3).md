# Week2 FP(3)

Course Name: Introduction to Computation
Date: September 29, 2021
Number: 7

## 【Ch2】Types and Functions(3)

**Functions over Lists and Tuples**

*List Functions*

A related pair of list functions, take and drop, take two arguments：

- take: Returns a list containing the first n elements of the list
- drop: Returns a list containing all but the first n elements of the list

See the following example:

```haskell
> take 2 [2,3,4,5,6]
[2,3]
> drop 2 [2,3,4,5,6]
[4,5,6]
```

*Tuples Functions*

For tuples, the fst and snd functions return the first and second element of a pair.

See the following example:

```haskell
> fst (1, 'a')
1
> snd (1, 'a')
'a'
```

**Passing an Expressino to A Function**

In Haskell, function application is left associate. For example, the expression a b c d is interpreted by the compiler as (((a b) c) d).

If we want to use one expression as an argument to another, we have to use explicit parentheses to tell the parser what we really mean.

Here is an example:

```haskell
> head (drop 6 "Hello World")
'W'
```

We can read this as "pass the expression drop 6 "Hello World“ as the argument to head."

**Function Types and Purity**

Here is an exmample of a function's type:

```haskell
> :type lines
lines :: String -> [String]
```

This is called the signature of function lines.

We can read the arrow above as "to", which loosely translates to "returns." The function takes in a String-typed argument and returns a list of String values.

*What does pure mean?*

In imperative programming language, if we pass a global variable to a function and asks the function to return the value of that variable. During the execution of the function, that global variable could be changed by some other functions and thus cause a side effect, even though the function itself never modifies the global variable.

In Haskell, the default is for functions to not have side effects: the result of a function depends only on the inputs that we explicitly provide. We call these functions pure; those functions with side effects are impure.

If a function has side effects, we can tell by reading its type signature: the type of the function's result will begin with IO.

See the following example:

```haskell
> :type readFile
readFile :: FilePath -> IO String
```

**Variable**

Definition: In Haskell, a variable provides a way to give name to an expression.

Once a variable is bound to a particular expression, its value does not change: we can always use the name of the variable instead of writing out the entire expression and get the same result

*Note: In Haskell, once we've bound a variable to an expression, we know that we can substitute it for that expression because it will not and should not be changed.*

See the following example:

```haskell
x = 10
--This will cause an error!
x = 11
```

![1.PNG](Week2%20FP(3)%2082682d00917f415f96b4e2dd625e636d/1.png)

**Conditional  Evaluation**

Haskell has an "if" expression, and let's see it in an example.

We want to define our own drop function, which returns an exmpty list if the first argument ≤ 0. Otherwise, it removes elemtns until either it runs out or reachs the given number.

```haskell
myDrop :: Int -> [a] -> [a]
myDrop n xs = if n <= 0 || null xs
							then xs
							else myDrop(n - 1)(tail xs)
```

In Haskell, indentation is IMPORTANT! It continues an existing definition, instead of starting a new one. DO NOT OMIT THE INDENTATION!!!

The xs in the code is a common naming pattern for lists: read the *s* as a suffix.  The name is essentially "plural of x."

- *An expression of type Bool* follows the if. We refer to this as a predicate
- A *then keyword*. This expression will be used as the value of the if expression if the predicate evaluates to True.
- *An else keyword*, followed by another expression. This expression will be used as the value of the if expression if the predicate evaluates to False.

In Haskell, you need to have both an *if and an else* to get the program to work.
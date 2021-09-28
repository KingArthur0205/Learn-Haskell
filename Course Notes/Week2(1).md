# Week2学习

Course Name: Introduction to Computation
Date: September 26, 2021
Number: 5
简介: Types

## 【Ch2】Types and Functions

**Type**

Every expression and function in Haskell has a type.

The type of a value indicates that it shares certain properties with other values of the same type. *For example, you can add two numbers and concatenate lists.*

*Why do we care about types?*

At the lowest leel, a computer works on bytes, with barely any additional structures. 

A type system offers us **abstraction**, which means adding meanings to the plain bytes.

The benefit of abstraction is letting us forget low-level details and only deal with what we need.

**Haskell's Type System**

There are three very interesting aspects to types in Haskell:

- Strong
- Static
- Automatically Inferred

*Strong Types*

**Definition of Weak or Strong：**

- Strength refers to how permissive a type system is. A weaker type system treats more expressions as valid than a stronger type system.

Haskell has a strong type system, which means that the  type system guarantees that a program cannot contain certain kinds of errors.

An expression that obeys a language's type rules is *well typed*, and yet one that does not is *ill typed* and will cause a type error.

The strong typing also will not automatically coerce(or known as cast or convert) values from one type to another.

In some other languages(like C), the C compiler will coerce an Int value into a Float value if the function expect a parameter of type float.

But a Haskell compiler will raise a compilation error in a similar situation. We must coerce types by applying coercion functions.

The huge benefit of strong types is that they can catch bugs before they cause any problem.

*Static Types*

**Definition of Static Type System**：

- A static type system means that the compiler knows the type of every value and expression at compile time, before any code is exectued.

For example, if we write the code below:

```haskell
ghci> True && "False"
```

It will give us the following error:

![1.PNG](https://github.com/KingArthur0205/Learn-Haskell/blob/main/Images/Ill%20Typed%20Error.png)

This is because the compiler has inferred the type of the expression "False" to be [Char]. The (&&) operator requires each of its operands on the side to be of the type Bool, and since the expression "False" does not match the requirement, the compiler rejects this expression as ill typed.

*Type Inference*

**Definition of Type Inference：**

- A haskell compiler can automatically deduce the types of almost all expressions in a program.

Haskell allows us to explicitly declare the type of any value, but the presence of type inference means that this is almost always optional.

**Some Common Basic Types**

- A Char value：Represents a Unicode character.
- A Bool value：Represents a value in Boolean logic. The possible values of Bool are True and False
- Int type：On 32-bit machine, an Int type value is usually 32 bits wide, while on a 64-bit machine it is usually 64 bits wide.（The Haskell standard only guarantees that an Int is wider than 28 bits）
- Integer value：Signed integer of unbounded size. Integers are not used as often as ints, because they are more expensive both in performance and space consumption. However, Integer computations do not silently overflow and thus give more reilably correct answer.
- Double type：Used for floating point numbers. A Double value is typically 64 bits wide.*（A narrower floating point type, Float, also exists, but its use is discouraged. This is because Haskell compiler works more efficiently on Double than on Float）*

The combination of (::) and the type after it is called a *type signature.*

```haskell
ghci> :type 'a'
'a' :: Char
```

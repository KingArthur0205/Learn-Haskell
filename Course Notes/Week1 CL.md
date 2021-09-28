# Week1 CL

Course Name: Introduction to Computation
Date: September 18, 2021
Number: 1

## 【Ch1】 Sets

**Sets, set membership and set equality**

Definition：One kind of thing is a collection of other things, known as a set.

One way of describing a set is by writing down a list of the elements it contains.

Ex：The natural numbers N = { 0, 1, 2, 3, ... } and the set of integers Z = { ..., -3, -2 ,-1, 0, 1, 2, 3, ... }.

- A thing is either in a set（$\in$）or not in a set （$\notin$）。
- Two sets are equal if they have the same elements regardless of the order.
- The empty set { } with not elements, usually written $\empty$, is also a set.
- The size or cardinality |A| of a finite set A is the number of elements it contains.

**Subset**

Suppose one set B is "bigger" than another set A in the sense that B contains all of A's elements, and maybe more. Then we say that A is a subset of B, written $A\subset B$

To prove A = B, we can prove that $A \sub B$ and $B \sub A$

**Operations on Sets**

- The union $A \bigcup B$ of two sets A and B is the set that contains all the elements(either) of A as well as all the lements of B.
    
    *This is the subset of students either has red hair or brown eyes.*
    

![1.PNG](https://github.com/KingArthur0205/Learn-Haskell/blob/main/Images/set1.png)

- The intersection $A \bigcap B$ of two sets A and B is the set that contains all the things that are elements of both A and B.
    
    ![1.PNG](https://github.com/KingArthur0205/Learn-Haskell/blob/main/Images/set2.png)
    
    *This is the subset of students that have both red hair and brown eyes.*
    

![1.PNG](https://github.com/KingArthur0205/Learn-Haskell/blob/main/Images/set3.png)

- The difference A - B of two sets A and B is the set that contains all the elements of A that are not in B.
- The complement of a set A is the set $\overline{A}$ of everything that is not in A. Complement only makes sense with respect to some universe of lements under consideration.
- Power Set：

![1.PNG](https://github.com/KingArthur0205/Learn-Haskell/blob/main/Images/set4.png)

**Ordered Pairs and Cartesian Product**

Two things x and y can be combined to form an ordered pair, written (x,y)

The Cartesian product of two sets A and B is the set A x B of all ordered pairs (x,y) with $x \in A \space and \space y \in B$

$\{Fiona,Dora \} \times \{19,20\} = \{ (Fiona,19),(Fiona,20),(Dora,19),(Dora,20) \}$

**Relations**

A set of ordered pairs can be regarded as a relation in which the first component of each pair stands in some relationship to the second component of the pair.

Ex：

![2.PNG](https://github.com/KingArthur0205/Learn-Haskell/blob/main/Images/set5.png)

**Functions**

- Some relations $f \sub A \times B$ have the property that the first component uniquely determines the second component:if (x,y) $\in f$ and $(x,y^{'}) \in f$ then $y = y^{'}$. Such a relation is called a function.
- Give $x \in A$, the notation f(x) is used for the value in B such taht $(x,f(x)) \in f$. If there is such a value for every $x \in A$ then f is called a total function; otherwise it is a partial function.

# Week4 FP

Course Name: Introduction to Computation
Date: October 12, 2021
Number: 10

## [Lec6]Map, Filter, Fold

**Map**

Description: Returns a list constructed by applying a function(the first argument) to all items in a list passed as the second argument

```haskell
map :: (a -> b) -> [a] -> [b]
map f xs = [ f x | x <- xs ]

--Define recursively
map f [] = []
map f (x : xs) = f x : map f xs
```

Square every element in a list using map:

```haskell
squares :: [Int] -> [Int]
squares list = map sqr list
	where
	sqr = x * x
```

**Filter**

Description: Returns a list constructued from members of a list(the second argument) fulfilling a condition given by the first argument

```haskell
filer :: (a -> Bool) -> [a] -> [a]
filter p xs = [ x | x <- xs, p x]

--Define recursively
filter p [] = []
filter p (x : xs) 
	| p x = x : filter p xs
	--Skip the current x
	| otherwise = filter p xs
```

Get every odd number in a list using filter

```haskell
getOdd :: [Int] -> [Int]
--odd is a built-in library function in Haskell
getOdd list = filter odd list
```

**Fold**

Description: It takes the second argument and the first item of the list and applies the function to them, then feeds the function with this result and the second argument and so on.

```haskell
foldr :: (a -> a -> a) -> a -> [a] -> a
foldr f v [] = v
foldr f v (x : xs) = f x (foldr f v xs)
```

Define sum using foldr

```haskell
sum :: [Int] -> Int
sum list = foldr (+) 0 list
```
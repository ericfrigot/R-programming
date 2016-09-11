# R-programming
R Programming lessons from Coursera

# Overview and History of R
R is an implementation of  S language, initiated in 1976 as an internal statistical analysis environment.
R was created in New Zealand in 1991 and made public in 1993.

# R Console Input and Evaluation
Assignment operator and evaluation

    > x <- 5
    > print(x)
    [1] 5
    > x
    [1] 5

Simply typing the object name also works. 
The [1] indicated that `x` is a vector and 5 the first element.

Use the : operator to create integer sequences

    > x <- 1:20
    > x
    [1] 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
    [16] 16 17 18 19 20
    
# Data Types
## Objects and attributes
R has five basic or "atomic" classes of objectfs :
- character
- numeric (real numbers)
- integer
- complex
- logical (True/False)

The most basic object is a vector which can only contain objects of the same class.

## Numbers
By default, R treated numbers as numeric objects (double precision real numbers).
If you need an integer you need to use L suffix like 1L.

## Attributes
R can have the following attributes :
- names, dimnames
- dimensions
- class
- length
- other user-definited attributes/metadata

Attributes of an object can be found using function attributes()

## Vectors and lists
The `c()` function ca be used to create vectors of objects

    > x <- c(0.5, 0.6)
    > x <- c("a", "b", "c")

To initiate a vector use the `vector()` function

    > x <- vector("numeric", length = 10)
    > x
    [1] 0 0 0 0 0 0 0 0 0 0

When mixing objects, like numeric and character in a vector, numeric is converted to character.
To explicit coercion use the `as.*` function

    > x <- 0:6
    > class(x)
    [1] "integer"
    > as.logical(x)
    [1] FALSE TRUE TRUE TRUE TRUE TRUE TRUE
    
When coercion is not possible, NA is displayed.

List are a special type of vector that can contain elements of different classes. Very useful in R.

    > x <- list(1, "a", TRUE)
    > x
    [[1]]
    [1] 1
    
    [[2]]
    [1] "a"
    
    [[3]]
    [1] TRUE

## Matrices
Matrices are vectors with a dimension attribute. They are filled column first.

	> m <- matrix(1:6, nrow = 2, ncol = 3)
	> m
		[,1] [,2], [,3]
	[1,] 1     3    5
	[2,] 2     4    6

Matrices can be created from a vectors by modifying the dimension attribute

	> m <- 1:10
	> m
	[1] 1 2 3 4 5 6 7 8 9 10
	> dim(m) <- c(2, 5)
	> m
		[1,] [2,] [3,] [4,] [5,]
	[1,] 1    3    5    7    9
	[2,] 2    4    6    8    10

Matrices can also by created by column-binding or row-binding using `cbind()` and `rbind()`.

	> x <- 1:3
	> y <- 10:12
	> cbind(x, y)
		 x  y
	[1,] 1  10
	[2,] 2  11
	[3,] 3  12
	> rbind(x, y)
		[,1] [,2] [,3]
	x    1    2    3
	y    10   11   12

## Factors
Factors are used to represent categorical data, like an integer vector where each integer has a label.

	> x <- factor(c("yes", "yes", "no", "yes", "no"))
	> x
	[1] yes yes no yes no
	Levels : no yes
	> table(x)
	x
	no yes
	2  3
	> unclass(x)
	[1] 2 2 1 2 1
	attr(, "levels")
	[1] "no" "yes"

To order the levels

	> x <- factor(c("yes", "yes", "no", "yes", "no"), levels = c("yes", "no"))
	> x
	[1] yes yes no yes no
	Levels : yes no

## Missing Values
They are denoted by NA or NaN (Not a Number)
- `is.na()` is used to tests objects if they are NA
- `is.nan()` is used to test for NaN
Those functions can be used directly on vectors or matrices

## Data Frames
They are used to store tabular data
They are represented as a list where every element as the same length. Data frames also have a special attribute
called `row.names`. They are usually created by calling `read.table()` or `read.csv()`.

	> x <- data.frame(foo = 1:4, bar = c(T, T, F, F))
	> x
	  foo  bar
	1   1  TRUE
	2   2  TRUE
	3   3  FALSE
	4   4  FALSE
	> nrow(x)
	[1] 4
	> ncol(x)
	[1] 2

## Names attribute
Very useful for writing readable code and self-describing objects.

	> x <- 1:3
	> names(x)
	NULL
	> names(x) <- c("foo", "bar", "norf")
	> x
	foo bar norf
	  1   2    3
	> names(x)
	[1] "foo" "bar" "norf"

For matrices.

	> m <- matrix(1:4, nrow = 2, ncol = 2)
	> dimnames(m) <- list(c("a", "b"), c("c", "d"))
	> m
	  c d
	a 1 3
	b 2 4


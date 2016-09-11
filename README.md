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
The [1] indicated that x is a vector and 5 the first element.

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
The c() function ca be used to create vectors of objects
	> x <- c(0.5, 0.6)
	> x <- c("a", "b", "c")
To initiate a vector use the vector() function
	> x <- vector("numeric", length = 10)
	> x
	[1] 0 0 0 0 0 0 0 0 0 0
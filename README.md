# QuadSieve
by Thomas Panetti & Noemi Glaeser 
04/28/16
CSCE 557
About: 	This program is an implementation of the Multi-Precise Quadratic 
       	Sieve algorithm.

use:  	To compile this program, simply use the javac compiler
		javac QuadraticSieve.java
  	To run this file, run the class file with the input
		java QuadraticSieve [N] [Factorbase]
			EX: java QuadraticSieve 1037 100
        or simply run it and it will prompt you for input
		java QuadraticSieve

How:  	First, this program generates a list of primes up to the size
  	of the factorbase using erothesthemes sieve. For example, if the 
	factorbase 10 the primes list would be {-1, 2, 3, 5, 7}. Next, 
  	the program populates an array from -R to R, R being the sqrt(N).
       	with the values (R+n)^2 - N, being the current index from -R to R.
        Next, we run a loop through every prime in the prime array and 
   	attempt to divide each value in the array from -R to R by the
	prime. This is repeated through the whole factorbase. 

	Next, we are left with an array of residuals after the division
	by every prime in the factorbase. Indices at which the residual
 	is equal to one, represent numbers that are smooth over the 
	factorbase. Then, we rebuild the smooth numbers using trial
	division giving us a matrix of rows representing the smooth numbers
	(the original indices are stored in a pair), and the columns are
	the exponents of the prime factors of that number. We then reduce
	the matrix mod 2. 

	Lastly, we use gauss-jordan elimination to determine the combinations
	of rows(the rows represent values of n) that sum to zero. for each 
	combination, we rebuild the equation (x^2 = y^2) where x^2 is 
	the product of (R+n)^2 -N for each n in the combination, and y^2 is
	the product of (R+n)^2 for each n in the combination. Taking the 
	gcd of big N and x-y and of big N and x+y, ideally, we obtain two factors
	of big N. Then, by taking these two gcds using every combination we obtained
	from guass-jordan elimination, we try to get every possible factor. Then
	we do the division of every factor by every other factor to make sure we 
	have both factors of every composite factor.






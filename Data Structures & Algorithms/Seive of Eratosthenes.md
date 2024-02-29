> Algorithm for finding all prime numbers up to any given limit.

# Working
> It does so by iteratively marking as composite (i.e., not prime) the multiples of each prime, starting with the first prime number, 2.

The basic idea behind this algorithms is that multiples of each prime is a non-prime number.
We start with the first prime number (2), mark all of its multiples as non-prime.
Then we go to the next prime number, mark all multiples of it as non-prime
![Working](https://upload.wikimedia.org/wikipedia/commons/9/94/Animation_Sieve_of_Eratosth.gif)

# Time Complexity

T.C. = n X ((1 / 2) + (1 / 3)  +..+(1 / n))
= n X log( log(n) )
S.C = n

[Problem Link](https://leetcode.com/problems/count-primes/submissions/1171165952/)

>[!warning]
>Read about segmented seive


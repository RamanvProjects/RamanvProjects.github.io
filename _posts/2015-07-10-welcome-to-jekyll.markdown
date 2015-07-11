---
layout: post
title:  "First Post! And some Haskell Project Euler Solutions (Casual)"
date:   2015-07-10 13:26:00
categories: Haskell Project Euler Material Design
---
Hello World,

This is my first post in a nice blogging system. I will update the CSS later to be more interesting but all in all it's pretty fun.

So to test out a few things and to show off some Haskell I have been learning, I will be doing a few of the first (pretty easy) Project Euler problems and give explanations of the syntax.

### Problem 1

>If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

>Find the sum of all the multiples of 3 or 5 below 1000.`

This essentially amounts to FizzBuzz except with summation. There are more math-y ways to do this problem but I will just use filters with Haskell. The final solution is below:

{% highlight haskell %}
-- Returns a list of the multiples of three and five under n 
multies35 :: Int -> [Int]
multies35 n = filter (\x -> x `mod` 3 == 0 || x `mod` 5 == 0) [1..n]

main :: IO ()
main = print . sum . multies35 1000
{% endhighlight %}

Pretty boring. But it works fine!

The filter just goes through the list and selects values that match the criteria.

### Problem 2

>The prime factors of 13195 are 5, 7, 13 and 29.

>What is the largest prime factor of the number 600851475143 ?

Prime factorization problems are pretty fun and there are many ways to approach them. The most standard and simple algorithm is also the most intuitive, based on the "prime factorization tree". Essentially it's a loop starting from 2 checking if it and any subsequent number divides the original (if it does, the number is divided and the process starts recursively). Below is the implementation:

{% highlight haskell %}
primeFactors :: Int -> [Int]
primeFactors n = ps n 2
	where
		ps n previous
			| previous * previous > n = [n]
			| r == 0				  = previous:ps q previous 
			| otherwise				  = ps n (previous + 1)
		where (q, r) = n `divMod` previous
{% endhighlight %}

This is kind middling in terms of speed. It has an interesting Big-O time which is an exercize in itself to figure out.

But let's say for the sake of argument that we had an infinite list of primes. Then we wouldn't have to iterate one at a time to see which numbers divide the original, we can just use the list. Our primeFactors function can be rewritten as follows:

{% highlight haskell %}
primeFactors :: Int -> [Int]
primeFactors n = ps n primes
	where
		ps n xs@(y:ys)
			| y*y > n = [n]
			| r == 0				  = previous:ps q xs 
			| otherwise				  = ps n ys
		where (q, r) = n `divMod` y
{% endhighlight %}

But we don't have an infinite list of primes... Or _do_ we?!?!?! Well no... But with the function above, we can make one.

{% highlight haskell%}
primes :: [Int]
primes = 2:filter (null . tail . primeFactors) [3,5..]
{% endhighlight %}

This is actually a rather useful way of producing an arbitrarily long list of primes in Haskell, and it's an interesting paradigm to explore in the future. The final code is as follows:

{% highlight haskell %}
primeFactors :: Int -> [Int]
primeFactors n = ps n primes
	where
		ps n xs@(y:ys)
			| y*y > n = [n]
			| r == 0				  = previous:ps q xs 
			| otherwise				  = ps n ys
		where (q, r) = n `divMod` y

primes :: [Int]
primes = 2:filter (null . tail . primeFactors) [3,5..]

main :: IO ()
main = print . sum . primeFactors 600851475143
{% endhighlight %}

That's all for now folks
[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help

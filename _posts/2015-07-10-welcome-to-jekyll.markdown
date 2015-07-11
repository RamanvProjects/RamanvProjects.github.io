---
layout: post
title:  "First Post! And some Haskell Project Euler Solutions (Casual)"
date:   2015-07-10 13:26:00
categories: Haskell Project Euler Material Design
---
Hello World,

This is my first post using the Jekyll system. I would recommend it. Check it out [here][jekyll]. It's pretty easy to use.

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
main = print . multies35 1000
{% endhighlight %}

Pretty boring. But it works fine!

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help

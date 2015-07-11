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

` If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Find the sum of all the multiples of 3 or 5 below 1000.`

This essentially amounts to FizzBuzz except with summation. There are more math-y ways to do this problem but I will just use filters with Haskell. The final solution is below:

{% highlight haskell %}
-- Returns 
multies35 :: Int -> [Int]
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}



Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help

---
layout: post
title: It's Rewind Time!
---

### The Big O:

For those who are beggining the world of algorithims, you need to have a basic knowledge of the Big O Notation. If you literaly google "Big O Notation", it says this:

Big O notation is a mathematical notation that describes the limiting behavior of a function when the argument tends towards a particular value or infinity. It is a member of a family of notations invented by Paul Bachmann, Edmund Landau, and others, collectively called Bachmann–Landau notation or asymptotic notation.

But in the world of computer programming, Big O is a little different.It basically means the performance or complexity of a algorithim. Algorithims have different levels of efficency, and the Big O notation takes the worst case scenario and see hown it performs.

For example, let's say we try to find a number from 1 to 100, and we can tell if the number is to the right or to our left. You could do this: start from either 1 or 100, and count down or up till you find the number. If we did from 1 to 200, we'll increase linearly. This is an example of a O(N) algorithim. But there are more efficent algorithims. 

Let's say from 1 to 100, you chose 50. It returns that the number is to your right. So you chose 75. It says it is below 75, so you know that the number is between 50 and 75. Fast, huh? We quickly are able to determine the number is 63. This algorithim would be classified as O(logN). 

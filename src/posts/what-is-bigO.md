---
title: "What is Big O Notation?"
seoTitle: "What is Big O Notation?"
datePublished: 2023-12-24T21:26:07.839Z
slug: what-is-bigO
cover: https://images.unsplash.com/photo-1587612049655-c1030366a74a?q=80&w=2970&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D.png
tags: tutorial, algorithms, data-structures, beginners

---

## What is Big O Notation?
You might have heard the term Big O notation being said quite a lot among developers. It is a very important concept in the field of computer science and it is used to describe the efficiency of an algorithm. It is one of the fundamental concepts you
will need to have a good grasp on in order to succeed in understanding performance and 
building your problem solving knowledge in general.


## What is Efficiency
Efficiency here means how good an algorithm perform with relation to an amount of data. An algorithm is just a series of steps that is used to perform an action.  
Using Big O, we are able to determine how different algorithms perform in relation to efficiency. We need BigO notation because we can have several algorithms that do a particular task but then, under the hood they all have different performances.

In computer science and algorithm analysis, measuring efficient or fast an algorithm is is not related to how long the algorithm takes but then the *number of the steps* in the algorithm. 

### Why?
When we use time spent executing as a measure for how fast or efficient an algorithm is, then the same algorithm can be faster on one machine and very slow on another machine since the hardware is a very strong determinant in how fast an execution occurs and varies greatly in different computers. For example, a laptop with a very powerful CPU and large ram might run a piece of code in 2 seconds and another computer with less resources will run the same algorithm in 20 seconds. As you can see, this makes it bad to measure the efficiency of an algorithm in terms of speed because we will not have a definite value for the measure since each computer will have their own execution speed.

However using the number of steps, we can know the number of things or sequences the algorithm will go through before completion. The number of steps will be the same across any hardware. If we have an algorithm that takes 5 steps on a super computer, we know that it will take the same number of steps on a old and less performant computer. *In other words, the number of steps will always be constant*

This levels the ground used to determine how good an algorithm is.



## Examples of Big O
1. O(1) - **Constant Time**. This means that the algorithm will always take the same amount of time to execute regardless of the number of things it has to work on.

2. O(n) - **Linear Time**. This means that the algorithm will take a time that is directly proportional to the number of things it has to work on. If the algorithm takes 1 second to work on 1 thing, it will take 2 seconds to work on 2 things and 3 seconds to work on 3 things and so on.

3. O(n^2) - **Quadratic Time**. This means that the algorithm will take a time that is directly proportional to the square of the number of things it has to work on. If the algorithm takes 1 second to work on 1 thing, it will take 4 seconds to work on 2 things and 9 seconds to work on 3 things and so on.

4. O(log n) - **Logarithmic Time**. This means that the algorithm will take a time that is directly proportional to the logarithm of the number of things it has to work on. If the algorithm takes 1 second to work on 1 thing, it will take 2 seconds to work on 4 things and 3 seconds to work on 9 things and so on. To understand how one works very well, you will need to understand the concept of [logarithms](https://en.wikipedia.org/wiki/Logarithm).

There are many more examples of Big O notation but these are the most common ones you will see. You can read more about Big O [here](https://en.wikipedia.org/wiki/Big_O_notation).
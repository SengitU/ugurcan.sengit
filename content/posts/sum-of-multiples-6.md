---
title: "Sum of Multiples Problem"
slug: "sum-of-multiples-problem"
tags: ["Scala", "Kata", "Performance"]
date: 2018-02-08
---

`The good thing about katas is that you can practice more than one solution just to achieve the best performance or readability or whatever you need` as I mentioned yesterday. Today I had a simple kata with a simple solution. But what I need was satisfy myself with the best performance. I tried harder and came up with a new solution. First, I want to share the problem;

Given a number, find the sum of all the multiples of particular numbers up to but not including that number.
If we list all the natural numbers up to but not including 20 that are multiples of either 3 or 5, we get 3, 5, 6 and 9, 10, 12, 15, and 18.

At first, I wrote a for loop up to given limit. Then checked if the number is a multiplier one of the given numbers. Adding up all numbers that satisfying the conditions yielded the result.

	
~~~~
def sum(factors: Set[Int], limit: Int): Int = {
  var currentNumber: Int = 0
  var sumOfAll = 0
  var numOfIterations = 0;

  for(currentNumber <- 1 until limit) {
    val isMultiplier = factors.find((factor: Int) => (currentNumber % factor) == 0)
    
    if(isMultiplier ne None) {
      sumOfAll += currentNumber
    }
    numOfIterations += 1
  }
  println(numOfIterations)
  return sumOfAll
}
~~~~

This solution iterates exactly `limit - 1` times. I wanted to do more, then I came up with following.

~~~~
def sum(factors: Set[Int], limit: Int): Int = {
  var multipliers: Set[Int] = Set(0)
  var numOfIterations = 0;

  factors.foreach((factor) => {
    var currentNumber: Int = 0
    for(currentNumber <- 1 to Math.floor(limit / factor).asInstanceOf[Int]) {
      val multiplier = currentNumber * factor
      if(multiplier != limit) {
        multipliers += multiplier
      }
      numOfIterations += 1
    }
  })

  println(numOfIterations + multipliers.size)
  return multipliers.reduceLeft(_ + _)
}
~~~~

I thought that I need multiply given numbers until they exceed the limit, then I realized that dividing given `limit` to given `number` yields what I need. While it covers all possible multipliers, it also iterates as much as `division` itself.

~~~~
for(currentNumber <- 1 to Math.floor(limit / factor).asInstanceOf[Int]) {
  val multiplier = currentNumber * factor
  if(multiplier != limit) {
    multipliers += multiplier
  }
  numOfIterations += 1
}
~~~~

By the help of this iteration, I collected every multiplier to a Set. Since `Set` collects only the unique items, I got rid of common multipliers. 
Lastly, `multipliers.reduceLeft(_ + _)` snippet summed all values inside the set.

After this little experiment, I have collected the data that I need to compare the approaches. When I ran all test cases for both approaches, first approach ran `21445` iterations while the second approach ran only `2380` iterations. 
While the first approach iterates `limit` times. The second approach's # of iterations varies with respect to inputs:

  - `Numbers` to evaluate increases
  - Weight of each individual `number` decreases
  - `limit` usually increases depends on the weight of the number

Feel free to clone the [repository](https://github.com/SengitU/Scala-Exercism-Katas/blob/master/scala/sum-of-multiples/src/main/scala/SumOfMultiples.scala) and create a pull request with a better performance.
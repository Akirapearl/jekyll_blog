---
layout: post
title:  "Day 4 - Go Tour - Pointers, Fizzbuzz exercise  "
date:   2024-07-14 18:00:00 +0200
categories: jekyll update
---

![custom header](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/SrewPUfo2c0.png)

Hey there!

Did you know that ducks are found in every region of the world except Antarctica?. This includes Africa, Asia, Australia, Europe, and North America. 
Ducks have been a part of the natural world for thousands of years and are recognized as one of the most widespread waterfowl species in the world.

Funny random facts appart, let's GO!

### What have I done today?

Today...I started easy on me, I finished the first exercise proposed by chatgpt at my previous post! Quite easier than I expected though, not a bad thing but I might check for a harder prompt so I don't feel like progessing goes too slow.

```
Exercise: FizzBuzz

    Task: Write a program that prints the numbers from 1 to 100.
    But for multiples of three, print "Fizz" instead of the number
    and for the multiples of five, print "Buzz". 
    For numbers which are multiples of both three and five, print "FizzBuzz".
```

And this was my [finished code](https://github.com/Akirapearl/LearningGo/tree/main/2024/exercises)
```go
package main

import "fmt"

func main() {

	for i := 1; i <= 100; i++ {
		if i%3 == 0 && i%5 == 0 {
			fmt.Println("FizzBuzz")
		} else if i%3 == 0 {
			fmt.Println("Buzz")
		} else if i%5 == 0 && i != 5 {
			fmt.Println("Fizz")
		} else {
			fmt.Println(i)
		}

	}
}
```
For the Fibonacci sequence, I wasn't so lucky, as my chatgpt prompt forgot to add the formula that said sequence is supposed to follow, ending up with myself not realizing that and failing that particular assignment by googling a solution, in any case, I found a potential subtitute for said exercise I will try out on the following days:

```
Exercise: Queue Data Structure

    Task: Implement a basic queue data structure from scratch using a slice. 
    Your queue should support the following operations: Enqueue (add an element to the back),
    Dequeue (remove and return the front element), and 
    Peek (return the front element without removing it).
```

I think that pressuring myself with "doing everything each day" can be a double edged sword, for that and from now on, I will try to mix readings, tutorials, and actual coding each day, there should be a day where tutorials for direct sintax or How-To's readings might not be that necessary but oriented to obtaining direct results, as in "measuring time of execution while running a golang script". [concept](https://www.golinuxcloud.com/golang-timing/)

Moving on, I could not continue with Go's Tour, so I will leave it for the next journal entry.

It is worth pointing out that I took a look into pointers, as it is the next concept to be learned at the Tour, just for the sake of getting a better idea of it, I checked around Youtube for a wider explanation of this concept, ending up with [this video by Tech by Tim](https://youtu.be/a4HcEsJ1hIE?si=YAVcIKSXb6Wmhr3l).

**Other resources I've found these days**

- ["Fast" Golang Walkthrough](https://www.youtube.com/watch?v=8uiZC0l4Ajw)
- [Effective Go - 2009 Official Blog Post](https://go.dev/doc/effective_go)
- [Go examples](https://gowebexamples.com/)

I will not always be able to do a overly productive day while learning, things take time, and tomorrow's time to get back to learning!

See you!
---
layout: post
title:  "Day 23 - Resuming, getting it back together"
date:   2024-09-24 15:10:00 +0200
categories: jekyll update
---


![custom header](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/C0mP_Mac.png)

Hello there!

Here we are again!, moving places is quite hard, so the next few days I'll take it easy, better to not burn me out before the harder parts, that being said, let's get into it without further rumbling around, shall we?

#### 19/09/2024 - Day 23

Previous to really start coding, I took a look back for what I've done, so far seems like there are some resources that I overlooked, some of them for a reason,
some of them rather because better alternatives showed up, same goes for projects and random ideas!...
I will be making a list of all my collected resources and exercises by the time I finish this challenge myself, so any newcommer to Go might have it easier than me to start programming on their own.

As for myself and just for today, I finished two parts of an exercism proposal, called Lasagna Master, here goes the code I've got for now!

```go
package main

import "fmt"

/*
1. Estimate the preparation time
Implement a function PreparationTime that accepts a slice
of layers as a []string and the average preparation time
per layer in minutes as an int.

The function should return the estimate for the total
preparation time based on the number of layers as an int.

Go has no default values for functions. If the average
preparation time is passed as 0 (the default initial value
for an int),then the default value of 2 should be used.
*/

func PreparationTime(a []string, b int) int {
	if b == 0 {
		b = 2
	}
	count := len(a)
	total := count * b
	return total

}

/*2. Compute the amounts of noodles and sauce needed

For each noodle layer in your lasagna, you will need 50 grams of noodles.
For each sauce layer in your lasagna, you will need 0.2 liters of sauce.

Define the function Quantities that takes a slice of layers as parameter
as a []string. The function will then determine the quantity of noodles
and sauce needed to make your meal.

The result should be returned as two values of noodles as an int and
sauce as a float64.
*/

func Quantities(s []string) (noodles int, sauce float64) {

	i := 0
	j := 0
	for _, value := range s {

		if value == "noodles" {
			i++
			// default is 2
			//[]string{"sauce", "noodles", "sauce", "meat", "mozzarella", "noodles"}
		} else if value == "sauce" {
			j++
			// default is 2
		}
	}

	noodles = i * 50
	// 100?
	calcj := float64(j)
	sauce = calcj * 0.2

	return
}

/*3. Add the secret ingredient
Write a function AddSecretIngredient that accepts two slices of ingredients
of type []string as parameters. The first parameter is the list your friend sent you,
the second is the ingredient list of your own recipe.

The last element in your ingredient list is always "?". The function should replace it with the last item
from your friends list. Note: AddSecretIngredient does not return anything -
you should modify the list of your ingredients directly. The list with your
friend's ingredients should not be modified.

Also, since slice is passed into a function as pointers, changes to the two []string
arguments passed into AddSecretIngredient will be modified directly.
*/
func AddSecretIngredient() {

}

func main() {
	fmt.Println("You are on this council, but we don't grant you the rank of lasagna master")

	layers := []string{"sauce", "noodles", "sauce", "meat", "mozzarella", "noodles"}
	fmt.Printf("%v\n", PreparationTime(layers, 3))
	// => 18
	fmt.Printf("%v\n", PreparationTime(layers, 0))
	// => 12
	noodles, sauce := Quantities(layers)
	//Quantities([]string{"sauce", "noodles", "sauce", "meat", "mozzarella", "noodles"})
	//fmt.Printf("%v, %f\n", Quantities(layers))
	fmt.Printf("%v, %v\n", noodles, sauce)
	// => 100, 0.4

	friendsList := []string{"noodles", "sauce", "mozzarella", "kampot pepper"}
	myList := []string{"noodles", "meat", "sauce", "mozzarella", "?"}

	AddSecretIngredient(friendsList, myList)
	// myList => []string{"noodles", "meat", "sauce", "mozzarella", "kampot pepper"}
}
```


#### 21/09/2024 - Day 24

Today I kept it going by finishing the Lasagna Master exercise and moving back into the Let's Go book by Alex Edwards. I got into the HTML template chapter,
where he starts building up a GUI environment for the sample code that the book takes a base onto, it is used as a way of explaining each concept and building more
details of the site upon that point.

For reference, it started just as a [TUI file](https://github.com/Akirapearl/LearningGo/tree/main/2024/web_learning/letsgo) that opened a http server and returned sort of a Hello World message, now I am handeling a structured project, with HTML
templating files and more modular code separated from the typical main.go one. 

I'd say that progress is being made quite fine, and I love to see I can manage to understand more difficult concepts by taking reference on other stuff I learned some time ago,
for reference, the dynamic concept of the templating in on itself reminded me of the view-controller model*.

#### 22/09/2024 - Day 25

Well, first "quarter" of the challenge is over, lets check how much I've learned and how do my next goals look like, shall we?

```
1- Learning Golang as a programming language
	- Basic syntax
	- Variable declaration
	- Functions
	- Packages
	- Imports
	- Flux control
	- Arrays, Slices, Runes
	- Structs
	- Pointers (In progress)
		- File operations
	- Go routines (In progress)
	- Channels (In progress)
	- Interfaces (Yet to check)
	- Generics

2 - Projects/Exercises done
	- Fizzbuzz
	- Basic Calculator
	- JSON parser
	- 3 batches (5 exercises each)
	- Contacts CSV 
	- URL Shortener
	- Gophercises: tty-quizz conquest
	- Codewars - specific proposals (Pending 3rd one)
	- Exercism proposals (learning)
		- Lasagna
		- Lasagna Master
		- Need for speed
```

I made quite some progress! Honestly it feels less that it should, but I think I got more used to the language and I can think of some methodology aquired related on how to write
code, which stuff is needed and which one not, some refactoring to make less code more efficient etc.

Now, what do I want to do for the next 25 days, as realistic as possible:

```
1- Learning (more) Golang -  Concept, usage in practice
	- Pointers
	- Go routines
	- Channels
	- Interfaces
	- Generics

2- Projects/Exercises
	- Gophercises
	- Advent of code (Day 1 & 2 from 2023's proposal)
	- Continue with Let's Go book (Assuming I won't finish it yet)
	- To-do list? Password manager?
	- Creating and using APIs 
	- Expense tracker (TUI/Web based UI)


3 - Future goals?
	- Web scrapper
	- Pomodoro website
	- MySQL library (easy to use Query/CRUD), kinda like meekro for php
	- Linux related tool - Networking, SwayWM...
	- Discord bot?
		- User ranking by how many messages they have sent
```

Now, that being said, what did I code today?

I got a bit further into the Let's Go Book, up to chapter 3, no less! Now the book will start explaining about error handeling, so it is safe to asume that the first stretch of 
code is over, here it is the result thus far!

![showoff_letsgo](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/checkgo.png)


#### 24/09/2024 - Day 26


I'm on holidays for three weeks! Besides two trips I got to do due to personal affairs, I'm going to try it out to take advantage of this time and do a bit more every day programming-wise.

As for today, I went ahead and completed one codewars proposal:

```go
func SortNumbers(numbers []int) []int {
	/*
		Finish the solution so that it sorts the passed in array of numbers.

		If the function passes in an empty array or null/nil value then it should
		return an empty array.

		For example:

		solution(c(1, 2, 3, 10, 5)) # should return c(1, 2, 3, 5, 10)
		solution(NULL)              # should return NULL
	*/

	if numbers != nil {
		sort.Ints(numbers)
	}
	return numbers
}
```

On the other hand, I want to keep an eye over my non-mastered topics, so I looked back into my go-to tutorials and stuff and gave it a spin to learn some missing concepts, as Go routines, Channels, Interfaces...Also starting to check about API-related concepts.

![showoff_learning](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/revisit.png)


#### 25/09/2024 - Day 27

So, today I started over a fresh project, a terminal-based password manager!. As for now, it has an externalized file where
basic functions are put onto, at the time of writing I have designed it to check that a file passed as an input exists and whether it is a CSV file or not.

For this I have applied a minor lesson learned from the Let's Go book, which consists into creating a "internal" directory, where the logic can be stored within functions, outside from the main file.

Brief screenshot of the current code:

![password_coding](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/code_passwd.png)



---
More info:

Lasagna Master: [Link](https://exercism.org/tracks/go/exercises/lasagna-master)

D&D Character: [Link](https://exercism.org/tracks/go/exercises/dnd-character)

View-controller model: [Link](https://www.codecademy.com/article/mvc)

Meekro for PHP: [Link](https://meekro.com/)

Automating SwayWM with Go: [Link](https://www.reddit.com/r/swaywm/comments/1dvyrna/automating_sway_with_go/)
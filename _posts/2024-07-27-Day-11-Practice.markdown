---
layout: post
title:  "Day 11 to 20 - Practice, Practice, Learn, Practice"
date:   2024-07-29 18:10:00 +0200
categories: jekyll update
---

![custom header](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/C0mP_Mac.png)

Oh Hi!

At the time of writing I don't really have that much to say, though it might change over the course of this new 5 days, well, let's get to it!

Sidenote:

As per studying more in-depth concepts of Golang, my current go-to tutorial became quite uneasy, for that, I will be changing into other resources, while
keeping the original handy, since I want to attempt the guided construction of an API that it provides at the very end of it.

New resources:
[Mastering Go: A Comprehensive Guide to Golang Programming](https://youtu.be/N2GWXuj_IWg?si=bLJl86kXxqZwBPmZ&t=8966)


There is also a new header! You can check it's source down below, then again, I do not claim any ownership over it, I just edited it into a more friendly format for my blog and added a text into it using GIMP and Jetbrains Mono font.
#### 27/07/2024 - Day 11 
As for today, I went over the goroutines part of my main tutorial of reference, yet could not understand it entirely, thus, I attempted other new exercises that can be found over my Learning Go repo. As for this time, I attempted the Advent of Code's day 1.

Unfortunately, it was an unsuccessful attempt, since I could not get the way to actually take the integers from the string and make them a unified number
(i.e af4dkdjn0, first number is a 4 and second a 0, thus making 40, kind of concatenating their values).

```go
func main() {
	fmt.Println("Advent of Code - First day")
	var calibration [3]string
	calibration[0] = "1abc2"
	//calibration[1] = "pqr3stu8vwx"
	//var res string
	var count int = 0
	for _, c := range calibration[0] {
		d, err := strconv.Atoi(string(c))
		err = nil
		count++
		if d !=
		fmt.Println(err)

	}
}

/*
	//fmt.Printf(" %c\n", c)
		//value := 0
		//value2 := 0

	if !unicode.IsDigit(c) {
			//d := int(c)
			d := string(c)
			// idea is to replace everything
			res = strings.ReplaceAll(d, "abcdefghijklmnopqrstuvwxyz", "")
			count++
			//value = d
			fmt.Println("value", res)
			//} else if !unicode.IsDigit(c) && count != 1 && count <= 2 {

		}
			-----------------------------------------
	if unicode.IsDigit(c) {
			d := int(c - '0')
			count++

			if count == 2 {
				secnd := d
				fmt.Println("second is", secnd)
			}
			first := d
			fmt.Println("first is", first)
		}
*/

```

Most of the comments added below are different attempts made from scratch, left aside so if i got something working, I could compare and learn from it.

This day was just gone with this, since I got involved into some programming communities to get more guidance, yet a solution was not provided by my own petition (want to solve it on my own).

Funny enough, there were some videos over youtube's collection that performed the same action that I was going through, yet applying a very much more experienced and complex code than the one i was attempting.


#### 28/07/2024 - Day 12 
I finished two more exercises! I focused most of my time today on my newly created "batch 2", so I could keep on practicing my already adquired knowledge, it was a bit painful, I might say, since I got a near close to ideal approach for the first exercise, yet failed to comprehend my own code.

```
Exercise 1: Factorial Calculation

Task: Write a program that calculates the factorial of a given number.

    Create a function factorial that takes an integer n and returns the factorial of n using recursion.
    In the main function, prompt the user to enter a number.
    Call the factorial function with the input number and print the result.

Exercise 2: Palindrome Checker

Task: Write a program that checks if a given string is a palindrome.

    Create a function isPalindrome that takes a string and returns a boolean indicating if the string is a palindrome.
    In the main function, prompt the user to enter a string.
    Call the isPalindrome function with the input string and print whether it is a palindrome.

```

After asking on my already chosen communities, they offered me a proper explanation, giving me a full comprehension of what I was doing.

Moreover, I went into the usual [tutorial](https://www.youtube.com/watch?v=8uiZC0l4Ajw) so I could learn a bit about goroutines, tho that part happened to be quite stressful, the explanation of the exercise seemed really poorly done, so I went into finding a rather more widely exposed context (see the top of this entry).

Next step, learning goroutines the proper way, continue with my exercises, and hopefully trying to finish advent's day one exercise. 

As a matter of fact, found more exercises platforms that use Golang. [Link](https://exercism.org/tracks/go/exercises)

#### 29/07/2024 - Day 13

Today I did a bit of everything, I went over the third exercise of my second batch (statement below), updated the main README.md for the LearningGo repo, and revisited the Goroutines concept around for a bit.

```
Exercise 3: Basic File I/O

Task: Write a program that reads a text file, counts the number of words in the file, and prints the result.

    Prompt the user to enter the filename.
    Open and read the file.
    Split the text into words and count them.
    Print the total number of words found.
```

This exercise might be of some help for my now on-hold JSON parser project, which will shortly become my main focus, alongside moving forward with Golangs general concepts, I believe I don't really have that much left to learn, yet the concepts remeaning are the most important ones, as concurrency,
interfaces, etc.

Sidenote that I found some references about working with JSON. [Link](https://www.golinuxcloud.com/read-json-data-format-in-golang/)

Also found some interesting tool built in Go! Yet to confirm whether it is written following best practices etc, but surely enough it can be a starting point to look for projects to contribute or to review, in order to improve my own code. [Gowall tool](https://github.com/Achno/gowall)

#### 30/07/2024 - Day 14
---
Credits:
Source of new header's image. [Link](https://unsplash.com/photos/a-woman-sitting-on-a-bed-using-a-laptop-computer-Owglx1TOsiA)
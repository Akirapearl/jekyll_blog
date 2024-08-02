---
layout: post
title:  "Day 11 to 20 - Practice, Practice, Learn, Practice"
date:   2024-08-02 15:10:00 +0200
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

Today I did a bit of everything, I went over the third exercise of my second batch (statement below), updated the main README.md for the LearningGo repo...

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


#### 31/07/2024 - Day 14

I finished both exercises 4 and 5! Can't say much more about them, yet I am excited to be able to finish this in a more agyle way, I guess?

```
Exercise 4: Sorting Algorithms

Task: Implement a simple sorting algorithm (e.g., Bubble Sort) to sort a list of integers.

    Create a function bubbleSort that takes a slice of integers and sorts it in ascending order.
    In the main function, define a slice of integers and print it.
    Call bubbleSort to sort the slice.
    Print the sorted slice.

Exercise 5: Unique Elements in a Slice

Task: Write a program that finds the unique elements in a slice of integers.

    Create a function uniqueElements that takes a slice of integers and returns a new slice with only the unique elements.
    In the main function, define a slice of integers with some duplicate values.
    Call the uniqueElements function and print the resulting slice of unique elements.
```

After that, I went over my JSON parser file and refactored it a bit, as well as seeking help over my trusted communities so I could get it working (which I did).

Current code (finished):
```go
package main

import (
	"bufio"
	"encoding/json"
	"fmt"
	"log"
	"os"
)

/*
Exercise: Parse JSON

Task: Write a program that reads a JSON string representing a list
of people (with fields for name and age) and parses it into a slice of structs.
Then, print out the names and ages of all people in the list.

STATUS: COMPLETED
*/

func check(err error) error {
	if err != nil {
		// Throw error if the file is NULL
		log.Fatal(err)
	}
	return err
}

func main() {
	fmt.Println("This is a JSON parser")
	// Read entire file at once
	content, err := os.ReadFile("read.json")
	check(err)

	// Print content
	fmt.Println(string(content))

	// Go over the document word by word
	file, err2 := os.Open("read.json")
	check(err2)

	scan := bufio.NewScanner(file)
	scan.Split(bufio.ScanWords)

	// Parse JSON into a struct
	// JSON decoder
	parser := json.NewDecoder(file)

	var person people = people{}
	/*
		p := people{
			Name: "Kaneda",
			Age:  30,
			City: "Neo Tokyo",
		}
	*/
	err = parser.Decode(&person)
	if err != nil {

		log.Fatalf("Failed to decode JSON: %s", err)
	}

	// reflect --> It enables you to examine the type and value of variables dynamically.

	fmt.Printf("Name: %s\n", person.Name)
	fmt.Printf("Age: %d\n", person.Age)
	fmt.Printf("City: %s\n", person.City)

	file.Close()
}

// Struct declaration
type people struct {
	Name string
	Age  uint8
	City string
}

```

Some background information about managing JSON files in Go. [Link](https://medium.com/@chaewonkong/go-and-json-a-comprehensive-guide-to-working-with-json-in-golang-143fa2dfa897)


#### 01/08/2024 - Day 15

Today I went over more of the "complicated" basics of GO, those being Channels, Generics and Goroutines, I followed uniquely one tutorial and attempted some minor value changing, thus I am aware that I still have plenty of way to keep learning, yet it is a relief to have managed to go over those concepts at once.

Content for those lessons can be seen at my [repo.](https://github.com/Akirapearl/LearningGo/tree/main/2024/go_fast)

Some code snippets from it:
```go
	// Calling a Goroutine
	// hangs the execution
	go printNumbers()
	fmt.Println("Goroutines")
	time.Sleep(1 * time.Second)
	//[==========================================]
	// first generic
func printItem[T any](item, defaultValue T) (T, T) {

	return item, defaultValue
}

func main() {
	fmt.Println("Generics")
	num1, num2 := printItem(1, 2)
	num3, num4 := printItem("tres", "quatre")
	bool1, bool2 := printItem[bool](false, true)
	fmt.Printf("%v \n%v\n", num1, num2)
	fmt.Println(num3, num4)
	fmt.Println(bool1, bool2)
}
```

---
Credits:
Source of new header's image. [Link](https://unsplash.com/photos/a-woman-sitting-on-a-bed-using-a-laptop-computer-Owglx1TOsiA)
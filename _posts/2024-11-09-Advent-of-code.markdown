---
layout: post
title:  "Day 40 to 50 - Advent of code - Round 2"
date:   2024-11-13 17:20:00 +0200
categories: jekyll update
---


![custom header](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/maik-jonietz.jpg)

#### Day 40 - 09/11/2024

[Advent of code!](https://adventofcode.com/2024/about) For those that don't know what I'm talking about, this concept is based on a daily coding challenge for the month of december, that might be attempted in any language desired by us, and it gets increasingly more difficult as the days go by. I attempted to do it earlier within this 100-days-of-code challenge, yet I lacked of some background/experience both with Golang and the proposal in on itself.

This is my now succesfully submited code, using as reference December 1, 2023's proposal.

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strconv"
	"strings"
)

func check(err error) error {
	if err != nil {
		return err
	}
	return nil
}
func main() {
	fmt.Println("hello World - Day 1")

	path := "input.txt"
	// Task 1 - Get the numbers
	file, err := os.Open(path)

	if err != nil {
		check(err)
	}
	defer file.Close()

	scanner := bufio.NewScanner(file)
	scanner.Split(bufio.ScanWords)

	count := 0
	for scanner.Scan() {

		x := scanner.Text()
		word := strings.Split(x, "")

		// store numbers from each line
		myInt := []int{}

		for _, value := range word {
			if valueInt, err := strconv.Atoi(value); err == nil {
				myInt = append(myInt, valueInt)
				//fmt.Println(myInt)
			}
		} // end for - store numbers

		count = count + myInt[0]*10 + myInt[len(myInt)-1]

	} // end for - scanner

	// Task 2 - Sum
	fmt.Println(count)
}
```

I will try to complete AT LEAST the first 7 days/week of the proposals from Dec,2023 before moving on to new projects or ideas, which at the moment are
```
    - Create an API client that retrieves weather information 
```
For reference, [check my repo](https://github.com/Akirapearl/Advent-of-code-2024/tree/main)

#### Day 40 && Day 41 - 10/11/2024 & 11/11/2024

I moved on to day 2 of this Advent of code week aaand I've gotten stucked again, but this time I went far beyond what I expected, here it is what I've got thus far (Night 11/11/2024)

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"regexp"
	"strconv"
	"strings"
)

func check(err error) error {
	if err != nil {
		return err
	}
	return nil
}

type Colors struct {
	green int
	red   int
	blue  int
}

func main() {
	fmt.Println("Day 2")

	path := "test.txt"
	// Task 1 - Get the numbers
	file, err := os.Open(path)

	if err != nil {
		check(err)
	}
	defer file.Close()

	// Set values for colors
	var TotalColors Colors

	TotalColors.red = 12
	TotalColors.green = 13
	TotalColors.blue = 14

	// Needed variables
	//totalPossible := 0

	scanner := bufio.NewScanner(file)
	scanner.Split(bufio.ScanLines)

	for scanner.Scan() {
		x := scanner.Text()

		// Split by : to get each subset
		parts := strings.Split(x, ": ")
		gameIDPart := parts[0]
		subsetsPart := parts[1] // e.g., "3 blue, 4 red; 1 red, 2 green, 6 blue; 2 green"

		// Extract the game ID from "Game X"
		gameID := strings.TrimSpace(strings.TrimPrefix(gameIDPart, "Game "))
		fmt.Println("GAME ======= ", gameID)
		//fmt.Println(subsetsPart)

		// "Does at any point the elf show you more than 12 red, 13 green, or 14 blue cubes at one time? If not, the game is valid."

		// Get the amount - colour pair via regex
		re := regexp.MustCompile(`(\d+) (\w+)`)
		// Find all matches
		matches := re.FindAllStringSubmatch(subsetsPart, -1)

		for _, match := range matches {
			//fmt.Println(match[1], match[2])
			actualcount, err := strconv.Atoi(match[1])
			check(err)
			if !(actualcount >= TotalColors.red) && match[2] == "red" {
				fmt.Println(match[1], match[2])
			} else if !(actualcount >= TotalColors.green) && match[2] == "green" {
				fmt.Println(match[1], match[2])
			} else if !(actualcount >= TotalColors.blue) && match[2] == "blue" {
				fmt.Println(match[1], match[2])
			}
		}

	}

}

```

#### Day 42 - 12/11/2024

Day 2 is over! By now I have already done over twice I could back on my first attempt of the Advent of code this year. Yet it is true I needed quite some help, not only from
friends but online too, but I got it done!

See my code!. [repo](https://github.com/Akirapearl/Advent-of-code-2024/blob/main/day2/main.go)

#### Day 43 - 13/11/2024

Ok so I might have reached a roadblock, one particularly hard that made me go a step back before moving forward, this roadblock was non other than Day 3 of Advent of code. It's proposal is,
conceptualy speaking, easy enough to understand, it is with its implementation where I've struggled the most.

On the other hand, I came to know that I totally forgot to go over both Day 1 and Day 2 part 2 statements, each of those give an extra layer of difficulty to the original problem, so I'll try
to figure those two out on the following days.

#### Day 44 - 14/11/2024

I finished yet another (part of a) day in my advent of code attempt! Yet, it is true that my approach was heavily based on a script that was not made by me. [Resouce](https://github.com/prathamesh-88/advent-of-code-2023/blob/master/Day01/trebuchet2.go)

Total credits go to said developer's effort and talent, I just based my approach on their script, but in order to avoid just copy-pasting, I rephrased it so instead 
of using a map of key/pair associating numbers (integers) to its equivalent as a string (i.e One:"one", index would be 1).


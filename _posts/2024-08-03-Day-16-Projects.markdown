---
layout: post
title:  "Day 16 to 20 - Projects, courses, ideas, exercises..."
date:   2024-08-17 17:30:00 +0200
categories: jekyll update
---

![custom header](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/C0mP_Mac.png)

Oh Hi!

Honestly I do not have a introduction in mind for this post, let's get to the journal/code!

#### 04/08/2024 - Day 16

Today I started going through more difficult exercises, as I started my [gophercises](https://gophercises.com/) journey, unfortunately I wasn't able to work it out, so I changed my
scope into my usual batch-oriented couple of exercises, now with batch 3 I am also getting deeper concepts worked around, so it seems there is no escape, time to be patient, try things until it work, but also be aware of my own mental health and limits.

Current batch of exercises:

```
Exercise 1: CSV File Handling

Task: Write a program that reads a CSV file, processes the data, and prints the results.

    Read CSV File:
        Prompt the user to enter the filename of a CSV file.
        Use the encoding/csv package to read the file.
        Assume the CSV file contains a list of users with columns Name, Age, and Email.

    Process Data:
        Create a struct User with Name, Age, and Email fields.
        Read the data from the CSV file into a slice of User structs.

    Print Data:
        Print the details of each user.

Exercise 2: Simple HTTP Server

Task: Write a simple HTTP server that responds with "Hello, World!" to any request.

    Create a new HTTP server in the main function.
    Define a handler function that writes "Hello, World!" to the response.
    Use the http.HandleFunc function to register the handler for the root path.
    Start the HTTP server on port 8080 and handle any errors.

Exercise 3: Environment Variables

Task: Write a program that reads environment variables and prints them.

    Use the os.Getenv function to read specific environment variables.
    Define a list of common environment variables to read (e.g., HOME, PATH, USER).
    Loop through the list and print each environment variable and its value.
    Handle cases where the environment variable is not set.

Exercise 4: Concurrency with Goroutines

Task: Write a program that spawns multiple goroutines to print numbers concurrently.

    Create a function printNumbers that takes an integer id and a channel of integers.
    In the main function, create a channel and launch multiple goroutines that call printNumbers.
    Each goroutine should read numbers from the channel and print them along with its id.
    Send a few numbers to the channel and close it.
    Use a sync.WaitGroup to ensure all goroutines complete before the program exits.

Exercise 5: Simple Calculator

Task: Write a simple calculator that performs basic arithmetic operations.

    Create a function calculate that takes two float64 numbers and an operator (string) and returns the result.
    In the main function, prompt the user to enter two numbers and an operator (+, -, *, /).
    Call the calculate function with the user inputs and print the result.
    Handle any errors (e.g., division by zero) gracefully.
```

Current code for the [first gophercises project](https://github.com/gophercises/quiz/tree/master) -- UNFINISHED:

```go
package main

import (
	"encoding/csv"
	"fmt"
	"os"
)

type question struct {
	Statement string
	Answer    string
}

func check(err error) {
	if err != nil {
		panic(err)
	}
}

func result(prompt int) {
	fmt.Println("", prompt)

}
func main() {
	fmt.Println("Welcome to the tty-quizz conquest")
	// Open the CSV file
	file, err := os.Open("problems.csv")
	check(err)
	defer file.Close()

	// Read the CSV data
	reader := csv.NewReader(file)
	reader.FieldsPerRecord = -1 // Allow variable number of fields
	data, err2 := reader.ReadAll()
	check(err2)

	count := 0
	// Print the CSV data
	for _, row := range data {
		for _, col := range row {
			//fmt.Printf("%s,", col)
			count++
			// Get all responses
			if count%2 != 0 {
				var ask question = question{}
				ask.Statement = col

				fmt.Printf("Resolve %s\n", ask.Statement)
				var w1 int
				w1, errif := fmt.Scanln(&w1)
				check(errif)

				go result(w1)

				/*
					if count%2 == 0 {
						var myArray [50]string
						myArray[count] = col
						fmt.Println(col)
					}
				*/
			}

		}
		fmt.Println()
	}
}

```

After some time attempting and breaking my head into this exercises, I needed a change, thus I joined my friend [María](https://github.com/LazulDev) and together we took a look into jekyll's themes and potential styling. We actually got it to take a css that applied some minor changes, yet it didn't take the original scss styling into consideration, which gave us a non-satisfactory result.

#### 05/08/2024 - Day 17

I did...quite a lot, today, ended up a bit of burned (almost 35 degrees celsius too, btw), but I finished Gophercise's proposed exercise for day 1 (without the extra timer, at least for now), as well as Day 2 of my next batch of exercises. I investigated a bit about http related capabilities for Golang too. 

```go
package main

/*
https://github.com/gophercises/quiz/tree/master
*/

import (
	"encoding/csv"
	"fmt"
	"os"
)

type question struct {
	Statement string
	Answer    int
}

func check(err error) {
	if err != nil {
		panic(err)
	}
}

func main() {
	fmt.Println("Welcome to the tty-quizz conquest")
	// Open the CSV file
	file, err := os.Open("problems.csv")
	check(err)
	defer file.Close()

	// Read the CSV data
	reader := csv.NewReader(file)
	reader.FieldsPerRecord = -1 // Allow variable number of fields
	data, err2 := reader.ReadAll()
	check(err2)

	correctAnswers := 0
	incorrect := 0
	//count := 0
	for i, row := range data {
		question := row[0]
		answer := row[1]
		fmt.Print("Question ", i+1, " ", question, " ")

		// Listen for input
		var w1 string
		//w1, errif := fmt.Scanln(&w1)
		fmt.Scanf("%v", &w1)
		//check(errif)
		//fmt.Printf("%v", w1)

		if w1 == answer {
			correctAnswers++
		} else {
			incorrect++
		}
	}
	fmt.Println()
	fmt.Println("Total correct answers: ", correctAnswers, "Total incorrects: ", incorrect)
}
```

I can't process more programming as for today, yet I consider this progress a win for now.

I've got more project ideas! This one I believe can be more feasible once I get to know more about web-related Golang, yet I wanted to highlight it too:
```
	Create a moodboard month-based website
		- Display the current month's days, status
		- Pick a mood for a specific day(From emojis to manually typing, may be a form-like dashboard)
		- Allow introducing notes
```
(
#### 08/08/2024 & 10/08/2024 - Day 18

**Note** I joined this two days since I focused onto the same topic and did not had enough time to properly spend real focus time on it, but joining the efforts of both days makes sense this time.


As per recently I've been progressing with exercises, small projects etc, I wanted to take a look back shortly, going through "a tour of Go" again, figuring
out if I have gotten rid of knowledge gaps etc.

Truth be told, it has been a breeze to see that the first 3 blocks of this tutorial went by around an hour in. Thus, I called it a day due to a very stressfull
day overall at my current job, continuing the day after.

Unfortunately, I got stucked into the method/interfaces part, which still means a roadblock to understand, which I will be tackling shortly. [Some references from youtube](https://www.youtube.com/results?search_query=method+golang)

As per "real coding" matter, I tinkered a bit during my journey with Go's tutorial, trying to make simple things more difficult or referencing to other concepts, i.e at the time were variables are explained, I made a struct that took the value of said variable and introduced it into the exported field, then
I used Println to actually output the struct instead of the original variable.

I also finished Exercise 3 from my third batch!. [Link](https://github.com/Akirapearl/LearningGo/tree/main/2024/exercises/batch_3)

Lastly, found even more resources as well, this particular one related to how can Golang be tied to Devops practices, etc. [Link](https://www.youtube.com/watch?v=xmZK-kUj9l0&list=PL7g1jYj15RUMdka_gPLDCFrIhwjtvCLJD)


#### 13/08/2024 - 14/08/2024 - Day 19

This time I joined both days since one was disclosed as a preparation one (get repos locally, figure out README files, choose projects to achieve etc) and the second one was more oriented to actual coding time.

This time, I created two new repos for some self-proposed projects!

Repo 1: [Password Manager](https://github.com/Akirapearl/Go-password-manager)
```
    Duration (estimated): 30 days
    Description:
        Start with building a basic CLI-based password manager that allows CRUD operations on passwords stored in a CSV file.
        Implement encryption for password storage.
        Transition to a web application using a framework like Gin or Echo.
        Use RESTful APIs for CRUD operations.
        Add user authentication and session management.
        Learn about pointers by managing memory efficiently and interfaces by creating mock tests.
    Key Concepts: Pointers, interfaces, methods, RESTful APIs, encryption, file handling.
```

Repo 2: [Url Shortener] (https://github.com/Akirapearl/Go-url-shortener/tree/main)

*Based on the gophercises exercise.
```
    Duration(estimated): 15 days
    Description:
        Build a simple URL shortener that maps long URLs to short ones.
        Implement CRUD operations to manage URLs.
        Use a database (like SQLite or PostgreSQL) to store the mappings.
        Implement concurrency with goroutines to handle multiple requests.
        Add user authentication and usage analytics.
    Key Concepts: Goroutines, concurrency, database integration, RESTful APIs.
```

The main idea behind creating both repos at the same time is not to burn myself out too much into a single thing. While I can still do exercises and all, my main focus is to be shifted into this projects, thus, if I step into a particular road block, changing the scope or my attention into a different topic within my learning process will help to solve it once I get back to it.

Both exercises will require me to jump back and forth and go into some investigation times that might not be directly looking into the stuff I need, but to know how to perform a similar thing (i.e how to code an API, how to connect to a database, etc).

Moreover, I did also finish exercise 4 from the third batch of exercises I've been doing. [Link](https://github.com/Akirapearl/LearningGo/tree/main/2024/exercises/batch_3)

##### Quick mention: 13/08/2024

Golang 1.23 was released!. [link](https://tip.golang.org/doc/go1.23) [Release notes](https://go.dev/doc/go1.23)


#### 17/08/2024 - Day 20

Today I quickstarted yet another repo, oriented for exercism proposed scripts only, for which I finished two of them, ideally I would be doing one exercise per day, non-sequentially, until there are no more exercise left. [link](https://github.com/Akirapearl/Go-exercism)

As per the major projects matter, I attempted to get into the url shortener one, yet it felt quite outside my current knowledge, for that, I
have already started to look into [Let's Go by Alex Edwards](https://lets-go.alexedwards.net/) and other web and [http-related tutorials](https://youtu.be/HO8RvUEeIgU?si=HK-MeRaWcGmt4Xhu), taking into consideration that its first two chapters are available publicly, it might be enough to cover this project.

---

So...so far so long I've reached the first fifth of this challenge, huh? I might do a separate post covering the general resources I've found, next to my progress and general impression of my own learning during this 20-ish days of coding.

That being said, see you next time!.
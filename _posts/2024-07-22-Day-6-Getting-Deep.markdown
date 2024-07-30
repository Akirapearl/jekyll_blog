---
layout: post
title:  "Day 6 to 10 - Getting deep the learning...mines?"
date:   2024-07-26 21:10:00 +0200
categories: jekyll update
---

![custom header](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/SrewPUfo2c0.png)


Hello there[!](https://www.youtube.com/watch?v=rEq1Z0bjdwc)

Hope that everyone is doing fine! As for myself, I have carried up some days upon learning more about
Golang, prior to focusing more into starting-from-scratch projects, as yet I have lots of things to understand.

Following up that line, I've checked some resources that might be ideal to keep close:

- Learn GO with tests. [Link](https://quii.gitbook.io/learn-go-with-tests)
- Golang common project structure. [Link](https://github.com/golang-standards/project-layout?tab=readme-ov-file)
- Tiago's Channel (General ideas for learning and some projects to inspire from). [Link](https://www.youtube.com/@TiagoTaquelim/videos)

Moreover, I also thought about a potentially useful and yet challenging project to make, which can also be exported/added to a discord bot,
to expand its usability.

```
    - Calling a weather API
        - let the user add multiple locations
        - Implement concurrency

	- Tic-tac-toe game (suggested online)
		- Needs the script to save its status (per game), change turns etc
		- may be leaderboard? 
		- input player games?
		-- Go is not commonly used for games, yet this could be a complete project on its own
```

I might not do any of the above as well as any other idea I might have written about over the challenge, yet I think it is beneficial for me to not stop being passionate about learning and opt into feasible projects I can even keep as mine and maintain over time.


### What did you do all this time?

**Well**, let's get down to disclose it all then...


#### 18/07/2024 - Day 6

Mostly continued with the video mentioned earlier within this blog, up to the interfaces content, following along Go's Tour too.([Link](https://www.youtube.com/watch?v=8uiZC0l4Ajw)).

Then, I also went through a bit of codewars proposed exercises, which can be seen at my [learning repo](https://github.com/Akirapearl/LearningGo/tree/main/2024/exercises).

```
Exercise proposal:
Make a simple function called greet that returns the most-famous "hello world!".

Style Points:
Sure, this is about as easy as it gets. But how clever can you be to create the most creative "hello world" you can think of? What is a "hello world" solution you would want to show your friends?
```

This one was pretty much limited to the test's claimed points, limiting my first approach, which included executing an external function to be used from main.

```go
package kata // do not remove

func greet() string{
  var at bool = true 
  
  if at == true {
    return "hello world!"
  } else {
    return "That's not a nice way to salute!"
  }
}
```

On my own approach, the idea was to pass a boolean value to the greet function, thus choosing if said piece of code would go over one part of the flux control or the other. 


#### 21/07/2024 - Day 7

Started to follow up the below shown exercise. The code can be seen [here](https://github.com/Akirapearl/LearningGo/tree/main/2024/exercises/JSON_parser).:

```
   Exercise: Simple Contact List

       Task: Create a program that allows the user to view and manage (add/delete) contacts.
	     Each contact should have a name and a phone number.
       Use a map to store the contacts, where the key is the contact's name
       and the value is the phone number.
```

At the time of writing the code looks as follows.

```go
package main

import (
	"fmt"
	"math/rand"
)

func main() {
	fmt.Println("Contacts exercise")

	// initialize map
	contacts := make(map[string]int)

	// Create a "default" value --> Generate a random number between 0 and 99
	num := rand.Intn(1000) 

	contacts["Alex"] = num

	fmt.Println(contacts["Alex"])

	// Reads input & generates variable for the input requested

	fmt.Println("Input name:")
	var w1 string
	fmt.Scanln(&w1)

	// Assigns a number to it && prints it
	contacts[w1] = num
	fmt.Println("read line: ", contacts[w1])

}
```

Improvement line: Allow user input to introduce new contacts, data should be also stored/read somehow, may be creating/reading a JSON file...

**Current issue**: Random number is only generated once, thus all entries using the "num" variable will use the same random number. Still pending to apply the "delete/remove created contacts" step. 


#### 22-07-2024 - Day 8

Today I chose to follow up into a review for the basics of Golang up to the point where I'm currently learning (structs/interfaces). [Repo](https://github.com/Akirapearl/LearningGo/tree/main/2024/exercises/batch_1)

I finished the following exercises.
```
###Exercise 1: Constants, Variables, and Basic Data Types

Task: Create a program that calculates the area and circumference of a circle.

    Define a constant for Pi (π = 3.14159).
    Declare a variable for the radius of the circle (e.g., radius).
    Calculate the area using the formula: Area = π * radius^2.
    Calculate the circumference using the formula: Circumference = 2 * π * radius.
    Print the results.

	--------------------------------------------------------

###Exercise 2: Functions and Control Structures

Task: Write a program that determines whether a given year is a leap year.

    Create a function that takes an integer year as an argument and returns a boolean.
    In the function, use control structures to determine if the year is a leap year:
    A year is a leap year if it is divisible by 4.
    However, if the year is divisible by 100, it is not a leap year unless it is also divisible by 400.
    In the main function, prompt the user to enter a year, call isLeapYear, and print whether the year is a leap year.
	*/
```

After that, I started checking around [Go Web Examples](https://gowebexamples.com/hello-world/) site to learn more about other aspects of Go, 
as well as created a new directory within my Golang [repo](https://github.com/Akirapearl/LearningGo/tree/main/2024/exercises/web_learning).

Then, I moved over the contacts exercise, even if it has a lot of work over it, in order to create an actually usable project, I made some improvements. Current code:

```go
package main

import (
	"fmt"
	"math/rand"
)

func randNumber() int {
	// Create a "default" value -- Generate a random number between 0 and 1000
	num := rand.Intn(1000)
	return num
}

func main() {
	fmt.Println("Contacts exercise")

	// initialize map
	contacts := make(map[string]int)

	contacts["Alex"] = randNumber()

	//fmt.Println(contacts["Alex"])

	// Reads input & generates variable for the input requested
	fmt.Println("Input name:")

	var w1 string
	fmt.Scanln(&w1)
	// Assign number to new element of the map
	// New call to the function - Generates different number
	contacts[w1] = randNumber()

	// Print entire map
	fmt.Println("map:", contacts)

	// Prints assigned number only
	fmt.Println("New contact has number: ", contacts[w1])

	// Remove element from the map, then list content to verify
	delete(contacts, w1)
	fmt.Println("map:", contacts)

}

```

Nothing too far from there I needed to stop due to heat giving me headaches for some time, better to stop before having a more alarming situation.

#### 24-07-2024 - Day 9

Today I chose to continue reviewing Golang's basics.:

```
###Exercise 3: Arrays, Slices, Maps, and Loops

Task: Create a program that calculates the average of a list of numbers.

    Define an array or slice of integers with at least five elements.
    Use a loop to iterate through the elements and calculate the sum.
    Calculate the average by dividing the sum by the number of elements.
    Print the average.

###Exercise 4: Strings, Runes, and Bytes

Task: Write a program that counts the number of vowels in a given string.

    Prompt the user to enter a string.
    Convert the string to lowercase to handle case insensitivity.
    Iterate through the string, character by character (rune by rune).
    Count the vowels (a, e, i, o, u).
    Print the total number of vowels found.
```

I got a bit stucked with Exercise 4, so I left it aside for the day after quite some attempts, since frustration was catching up with me because an overall exhausting day, and programming in a bad mood is no good for me, my mental health, or my overall learning process.

After that, I continued a bit along the "Learn GO Fast: Full Tutorial", this time getting re-introduced to pointers. [Link here](https://www.youtube.com/watch?v=8uiZC0l4Ajw).


#### 26/07/2024 - Day 10

Today I got to finish all my exercises! I finished exercise 4 and exercise 5 quite more easily that expected (being quite honest, for exercise 4 I had to ask over a Golang community I joined over Discord), the issue was within my code, as easy as replacing double quotes for a single quotation at the line where I declared a conditional within the loop that recurred all values within the rune created before [(see Line 38)](https://github.com/Akirapearl/LearningGo/tree/main/2024/exercises/batch_1/exercise4).
```
###Exercise 5: Structs

Task: Create a program that stores and displays information about a book.

	Define a struct Book with the following fields: Title, Author, YearPublished, and ISBN.
	Create an instance of the Book struct and initialize it with values.
	Write a function printBookDetails that takes a Book struct as an argument and prints the book's details in a readable format.
	In the main function, call printBookDetails with the book instance.
```
Result can be seen [here](https://github.com/Akirapearl/LearningGo/tree/main/2024/exercises/batch_1/exercise5).

After that, I took a look over again at the Web server example I mentioned at [Day 8]((https://gowebexamples.com/hello-world/)).

### Conclusions

I need to focus more into learning the basics, at first I hoped this initial steps to last less time, which was honestly unrealistic. Since I've spent about a month up to this point, getting along each day's ups and downs, my own self-demand to become better faster...I just need to calm down, keep on learning the basics on a steady yet constant basis and time will tell when I feel ready to start something bigger.

As for now, my new goals for the next 10 days are:
- Try out Advent of code's exercises
- Continue with Golang's basics, hopefully finishing the 1h long tutorial that covers most of them and beyond
- Start out with [Go web examples](https://gowebexamples.com/) more seriously, may be purchasing the [Let's Go book](https://lets-go.alexedwards.net/).


I shall keep it [going](https://www.youtube.com/watch?v=uE-1RPDqJAY), but this is all for now.

See you later!
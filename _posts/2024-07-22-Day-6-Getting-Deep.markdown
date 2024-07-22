---
layout: post
title:  "Day 6 to 10 - Getting deep the learning...mines?"
date:   2024-07-22 22:00:00 +0200
categories: jekyll update
---

![custom header](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/SrewPUfo2c0.png)


Hello there[!](https://www.youtube.com/watch?v=rEq1Z0bjdwc)

Hope that anyone reading this in the future is doing fine! As for myself, I have carried up some days upon learning more about
Golang, prior to focusing more into starting-from-scratch projects, as yet I have quite some details to understand.

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
```

### What did you do with this challenge all this time?

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

```
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

```
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

    Create a function that takes an integer year as an argument and returns a boolean. -- Check
    In the function, use control structures to determine if the year is a leap year:
    A year is a leap year if it is divisible by 4. -- Check
    However, if the year is divisible by 100, it is not a leap year unless it is also divisible by 400.-- Check
    In the main function, prompt the user to enter a year, call isLeapYear, and print whether the year is a leap year.
	*/
```

After that, I started checking around [Go Web Examples](https://gowebexamples.com/hello-world/) site to learn more about other aspects of Go, 
as well as created a new directory within my Golang [repo](https://github.com/Akirapearl/LearningGo/tree/main/2024/exercises/web_learning).


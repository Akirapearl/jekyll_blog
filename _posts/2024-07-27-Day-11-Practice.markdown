---
layout: post
title:  "Day 11 to 15 - Practice, Practice, Learn, Practice"
date:   2024-07-28 13:10:00 +0200
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

After asking on my already familiar communities, they offered me a proper explanation, giving me a full comprehension of what I was doing.

Moreover, I went into my go-to [tutorial](https://www.youtube.com/watch?v=8uiZC0l4Ajw) so I could learn a bit about goroutines, but that part happened to be quite stressful for me, the explanation of the exercise seemed really poorly done, so I went into finding a rather more widely exposed context (see the top of this entry).

Next step, learning goroutines the proper way, continue with my exercises, and hopefully trying to finish advent's day one exercise.

#### Day 13

---
Credits:
Source of new header's image. [Link](https://unsplash.com/photos/a-woman-sitting-on-a-bed-using-a-laptop-computer-Owglx1TOsiA)
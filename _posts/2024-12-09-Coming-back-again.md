---
layout: post
title:  "Reaching day 50 - Coming back again"
date:   2024-12-15 21:20:00 +0200
categories: jekyll update
---

![custom header](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/maik-jonietz.jpg)


Oh well... Hi there!

A bit of a time off, right? Last time I wrote a post entry for my blog was mid-November, but I have quite some stuff ongoing on my personal life, so had to figure out how to focus and enjoy coding again, let's get to it, then!.


#### Day 44 - 08/12/2024 - Starting somewhere - Let's do a tutorial about RESTful APIs

Might sound a bit easy-going, but since I've been struggling quite a bit with focus and trying to get my mind to code, I believe that a copy-paste kind of tutorial could be a way to come back, as of the time of writing, I might be correct, I wanted to do more once I finished!.

In summary, I followed [this tutorial](https://go.dev/doc/tutorial/web-service-gin*/) that covers how to use Golang and Gin framework in a simple way to operate GET and POST operations, my next steps on this might be even making this API bigger, since by default no information is stored persistently, a CSV file or a simple SQL database collection might be useful for this.

![tty_screenshot_json](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/jsonAPI.png)


#### Day 45 - 11/12/2024 

Well, I took the lead for creating APIs and this time I tried out to use an already existent API, like the openweather one, and sort of got it to work, but ended up getting repeated 401 Status codes, so I ended up a bit stucked, my goal rn is just to retrieve the entire JSON for the Get request I made, here is the code:

```go
package main

import (
	"fmt"
	"io" // Import the internal package
	"myweatherapi/internal"
	"net/http"
)

func main() {
	fmt.Println("Hi")

	// Create a new HTTP client
	client := &http.Client{}
	// GetAPIKey - internal package
	apiKey := internal.GetAPIKey()
	url := fmt.Sprintf("https://api.openweathermap.org/data/3.0/onecall?lat=33.44&lon=-94.04&appid=%s&units=metric", apiKey)

	resp, err := client.Get(url)
	if err != nil {
		fmt.Println("Error in GET request:", err)
		return
	}
	defer resp.Body.Close() // Ensure response body is closed

	//fmt.Println("Request successful!")

	if resp.StatusCode != 200 {
		fmt.Printf("Weather API not available - Error Code: %v", resp.StatusCode)
		body, _ := io.ReadAll(resp.Body) //ignoring error and checking content of response
		fmt.Println("Response", string(body))
	}

}
```

After that mentioned error, and since I already have a simple API, I have gotten to a conclusion that may be I can create my own API endpoint and then call it from my own endpoint, that would involve the whole two ends of the spectrum, since I could get as deep as I want, storing data within a database etc.

Another option would be to follow [this tutorial](https://www.twilio.com/en-us/blog/check-weather-with-go) applying the same concepts I followed for this first part of my API client.


#### Day 46 - 12/12/2024

This time I tried to rotate onto a different approach I briefly disclaimed yesterday, what if I use my own simple API to check my code? It should be agnostic enough of the API itself so I could
use any and still get a response, right?

Well, that's true, and after some trial and error, i got it working! Sidenote that I needed to specify `http://` prior to the rest of the url for it to work correctly

![tty_screenshot_API_call](https://raw.githubusercontent.com/Akirapearl/jekyll_blog/main/assets/images/codegin.png)

Ideally from here I should be able to filter which JSON tags I want to keep & show accordingly.

So, getting back to the Weather API, lets try [something different](https://www.twilio.com/en-us/blog/check-weather-with-go).


#### Day 47 - 15/12/2024

I did it! I have a very simple API client that worked both with my local API and the [Weather API](https://www.weatherapi.com/my/) one. I still don't know why my attempt with Openweather 
went wrong, but it should be fine to modify this script briefly if I got that one working eventually.

So here's the final curated code!

```go
package main

import (
	"encoding/json"
	"fmt"
	"io" 
	"myweatherapi/internal" // Import the internal package
	"net/http"
)

type Weatherdata struct {
	Location struct {
		City string `json:"name"`
	} `json:"location"`
	/*
		Expected response
		{"location":{"name":"Barcelona","region":"Catalonia","country":"Spain","lat":41.3833,"lon":2.1833,"tz_id":"Europe/Madrid","localtime_epoch":1734278478,"localtime":"2024-12-15 17:01"}
	*/

	Current struct {
		TempC     float64 `json:"temp_c"`
		Condition struct {
			Text string `json:"text"`
		} `json:"condition"`
	} `json:"current"`

	/*
			Expected response
		"current":{"last_updated_epoch":1734278400,"last_updated":"2024-12-15 17:00","temp_c":13.3,"temp_f":55.9,"is_day":1,"condition":{"text":"Partly cloudy","icon":"//cdn.weatherapi.com/weather/64x64/day/116.png","code":1003}
	*/
}

func checkError(err error) {
	if err != nil {
		panic(err)
	}
}
func main() {
	// Create a new HTTP client
	client := &http.Client{}
	// GetAPIKey - internal package's only function
	apiKey := internal.GetAPIKey()
	// Weatherapi
	url := fmt.Sprintf("https://api.weatherapi.com/v1/current.json?key=%s&q=Barcelona&aqi=no", apiKey)
	resp, err := client.Get(url)
	if err != nil {
		fmt.Println("Error in GET request:", err)
		return
	}
	defer resp.Body.Close() // Ensure response body is closed

	if resp.StatusCode != 200 {
		fmt.Printf("Weather API not available - Error Code: %v", resp.StatusCode)
		body, _ := io.ReadAll(resp.Body) //ignoring error and checking content of response
		fmt.Println("Response", string(body))
	}
	body, err := io.ReadAll(resp.Body)

	checkError(err)

	var tiempo Weatherdata
	err = json.Unmarshal(body, &tiempo)
	checkError(err)

	city, weather, sky := tiempo.Location, tiempo.Current.TempC, tiempo.Current.Condition

	fmt.Printf("%v %v°C %v", city.City, weather, sky.Text)
}

```

For sure it can be improved and 
So...what's next? I recall that I did stop my progress with Let's Go book by the point where it covers Database connections and all that, so my idea for the next iteration
of this particular project is to transform my [local API into a REST API using MongoDB](https://www.youtube.com/watch?v=y2M-dbT6bSs).

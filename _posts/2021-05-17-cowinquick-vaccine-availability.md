---
 title: CoWIN Vaccine Availability - My first open source project
 tags: [open-source]
 style: fill
 color: light
 comments: true
 categories: software-engineering
 excerpt: One of my side projects for booking vaccine slots quickly
---

<hr>

# Introduction
[CoWIN](https://www.cowin.gov.in/home) is a vaccination booking platform for booking vaccination for Indian citizens. This is the largest vaccination drive ever. Anyone can simply go and book the vaccination slots as per the availability in the respective state and districts. In this post, I have created another platform just for checking vaccine availability.
 

> But what's the need for creating a different platform for checking the availability when you already have the official platform?

# Problem
I had a hard time finding the vaccination slots (for the 18-45 age group). Some of the problems I(and other people I think) faced:
* Most of the times the slots were not available and when they were available, they were booked in seconds. 
* The User experience of the original CoWIN portal is not that great. Firstly you need to log in through your phone number(by an OTP which sometimes refuses to arrive on your phone). You are automatically logged out after 15-20 mins.
* Some features are missing but can help find the slots. For eg: The ability to search across multiple districts.
* A filter for hiding the unavailable slots from the search result would have been really helpful.

> Some people have also written scripts for notifying whenever the slots are available. The idea is great but there are a couple of problems with the script's approach:
As soon as you get the notification that slots are available in your district, you open up your browser ->login into the [CoWIN portal](https://www.cowin.gov.in/home) -> select the beneficiaries that you want to get vaccinated -> select the state & district/enter pin code and click search -> BOOM! the slots have already been booked! 
  

# Solution
I created a simple HTML page that calls the public CoWIN API in JS. Check out the live demo [here](https://dollardhingra.com/cowinquick/).  
**Note:** This website can only be used for checking the available slots. For booking, the [official site](https://www.cowin.gov.in/home) must be used.

<iframe width="1046" height="588" src="https://www.youtube.com/embed/knjqHZNs7LM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


This helps in booking as
* There is no need for entering phone number/OTP again and again
* The results are visible for multiple districts at once.

# How I have booked more than 20 slots till now
I have booked more than 20 slots(for friends and family) with the following approach:
* There is usually a 1-2 hour window when the slots are open. Usually between 6-10 pm on weekdays and 12-4 pm on weekends. These timings may change so keep casually looking for the slots whenever you have your phone in hand through the [cowinquick site](https://dollardhingra.com/cowinquick/).

* Let's say that you find available slots in your district or a nearby district. Note the name of the centre. Let's say that the name of the centre is "BLK Hospital Site 1". 

* In one tab, login into the [cowin portal](https://www.cowin.gov.in/home) and select the city and district/pin code. In the other tab, you can open the [cowinquick site](https://dollardhingra.com/cowinquick/).

* Now check if "BLK Hospital Site 1" is available. If not, then come back to the [cowinquick site](https://dollardhingra.com/cowinquick/) and search again. There is a high probability that "BLK Hospital Site 2" will come up next in few minutes. 

* Keep searching after every 5-10 seconds. There is a chance that you are searching in the time window where the slots are being updated. You will come to know that the slots are being updated if you keep searching for 5-10 mins(clicking search after every 10-20 seconds). Either of the following will happen:
    - You will see that for some centres the slots are being open and booked in 15-20 seconds. Try booking that centre in those 15 seconds. The advantage you have on [cowinquick site](https://dollardhingra.com/cowinquick/) is that you can see the results for multiple districts at once & you don't need to select 18+ again on every search. 

    - There may be a situation when you don't see any centres updating slots. You can then try the same after some time. 


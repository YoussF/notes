<p align="center">
   <img src="assets/becode.png" alt="BeCode" width="197"/>
</p>

# Automation - Write a webscrapper with Selenium
- Type of challenge: *Learning* +
- Duration: *2 days* +
- Deadline: yesterday
- Deployment strategy: local
- Team challenge: *solo*

## Learning Objectives
- To be able to write a python script that collects real estate publications data related to rented appartments in Brussels from immoweb.be using Selenium WebDriver (Python implementation)
- To be able to store each rentred appartement in a local database (mysql, postgresql, sqllite) with the current timestamp.
- To be able to make the script a bit more clever, so that it only adds new publications to the database.
- To be able to added a notification feature ( sms, email,...), this way use can be notified when new data comes in.
- To be able to make it configurable, user must have the ability to change things like zipcode or estate type.
- To be able to bypass immoweb's x requests per second limitation by setting up an local proxy that use a different external ip each time the script makes a request to the server (hint: https://github.com/trimstray/multitor)
- To be able to schedule your script so that i runs in background every x minutes by using  a cron job

## The mission
Being able to surf the web at the speed of light and gather relevent information, as if your life depends on it! Why ? BECAUSE IT DOES ! You see... sometime life can be tough! i mean really tough ! And your ability to operate faster than your competitors can be crucial for your success.

In 2014, i started to have huge unsanitary problems in my appartement where i lived with my wife and my two kids. So much so that the organization responsible for ensuring sanitation decided to close the apartment. They told me that I was going to have to leave before the end of the month.

Then i started looking for a new one on immoweb.be, but I was quickly confronted with two major problems :

- Immoweb.be does publish any information about the publication date, therefore i had no way to know for how long a particular appartement has been on the plateform.
- Every time I found an interesting apartment, I contacted the owner, but it was too late, he had already rented it.

So i needed a tool that will help me fix these two problems. I wanted a tool that will let me find appartments availible for renting faster than everyone else, so that i can be the first person to contact the owner (remember, my life depended on it).

## Resources
- [Selenium WebDriver](https://www.selenium.dev/documentation/en/getting_started/)
- https://chromedriver.chromium.org/
- [trimstray/multitor](https://github.com/trimstray/multitor)

## Final words
This projet helped realise that technology is supposed to serve a purpose. Coding stuff just to code stuff is fun. But when you code something that will fix a problem in real life is another much more fun !

As the project progressed, I encountered unforeseen events on my way, for example, fighting against the anti-bot system of immoweb. And it was very nice to see how there is no insurmountable problem.

One last thing, in a upcoming briefing, we will get our hands a little bit more dirty and learn how to reverse engineer immoweb's REST API (which is not public) to gain direct access to data . It will be a lot of fun, I promise !
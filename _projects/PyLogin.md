---
layout: project_post
title: PyLogin
description: Python Login Bot, and NodeJS Login Page
year: 2022
tags:
  - Python
  - Node.js
  - Web App
  - Automation
---

## 2022 CSHS Cybersecurity

[PyLogin](https://github.com/judz5/pylogin) is a Python Webscraping Login Bot, and NodeJS / MySQL Login page

## Write-up

My research for this project started a few months ago when i started a web development course with [FreeCodeCamp](https://www.freecodecamp.org/). I only made it about halfway through the course but i learned alot about basic HTML and CSS. I began by making a static website that could be used as a fake login form, where the login is set by the user then the program could attempt to login. However I wanted to go a step further and learn basic back end development, so I took the challenge and remade the website using NodeJS and MySql to create a dynamic login form, with the ability to register accounts as well. 

I think the best way to learn something new is to follow a tutorial first, and do your best to understand what they do, then go a step further and add something on your own (in my case the register function / basic home page). 

I am not a backend developer at all yet, but this project was a good learning expeirence that taught me alot about how the backend of websites and servers are handled. The actual LoginBot was a quick add, and only took a short while after I learned how to make POST Requests with the [Requests](https://github.com/psf/requests) library.

While its not amazing that I made a loginBot that breaks into my own website comapred to a real bot capable of stealing logins from something such as RuneScape or Minecraft, I'm still proud I was able to make a non-static working login page with a language I'm not familiar with.

## Sources

- https://stackoverflow.com/questions/68954747/my-python-post-request-doesnt-work-in-my-login-bot
- https://github.com/judz5/PyCrack
- https://www.geeksforgeeks.org/get-post-requests-using-python/
- https://codeshack.io/basic-login-system-nodejs-express-mysql/
- https://www.w3schools.com/nodejs/nodejs_mysql_insert.asp

## Use

First you need to have an sql database setup with an accounts table (cols: username, password), then change the nodelogin/login.py to reflect the accurate host and password for sql.

First start your sql server

    $ brew services start mysql

Next

    $ node nodelogin/login.js

Now the site is hosted at http://localhost:3000/login!

once you have the site running and some accounts registered you can just do

    $ python3 loginBot.py 

this will run the python script and give you a list of all found login credientials from the site.

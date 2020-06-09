---
layout: post
title:      "A Session on Session Cookies"
date:       2020-06-09 20:59:16 +0000
permalink:  a_session_on_session_cookies
---


In order to understand sessions, we need to first understand a little bit about the internet. Beyond being modern-day magic and a place where one can find an endless source of cat pictures and memes, the internet is globe-spanning network that we can navigate with stateless protocols—specifically the Internet Protocol (IP) and the Hypertext Transfer Protocol (HTTP). 

![](https://www.feedough.com/wp-content/uploads/2016/11/the-internet-meme.jpg)

Without getting too much into the details, what this generally means is that information is not stored on servers from one webpage to the next. This is wonderful for keeping everything running smoothly when you have many people accessing the same web page, but is a challenge when you want to keep someone logged in from one page to the next.

Enter session cookies.

![](https://scontent-iad3-1.xx.fbcdn.net/v/t1.0-9/11052008_874750289237750_9116045906095143936_n.jpg?_nc_cat=102&_nc_sid=85a577&_nc_oc=AQlEi2e0M5p7YZEWLWvaP2ejcpiw0ZlMtpKZyvS4KYxs-GC95o01GIgrezi_utaBfxg&_nc_ht=scontent-iad3-1.xx&oh=f5d0bec35e7e28461d52db74cc5838f6&oe=5F056FF7)

Sessions are an amazingly powerful tool, which turns the internet from a collection of disconnected requests to a seamless navigation of a website that allows you to be logged in, fill shopping carts, and keep track of other small amounts of information that would be helpful.

Unlike the cookies that we often hear about (at least internet related, and not the food), session cookies don’t stick around indefinitely or until a person/browser decides to delete them. Rather than persisting, session cookies generally only exist for as long as the web browser is open. 

These sessions are stored on the device that is browsing the internet, and can be used by web applications to keep track of certain information. Such as the particular user that is logged in through a line like  `session[:user_id] = logged_in_user`.

Storing information like this, even temporarily, on the device accessing the site can cause issues though. Not everyone is happy with getting to only see information from their own login, but would like to see what others have. As such, we can’t store this information as plain old text, allowing someone to go in and edit the user_id from jimmy@g.com to johns@g.com. These types of actions are known as session hijacking.

This brings in session encryption. Thankfully there are tools to ensure session cookies are encrypted, and even some web frameworks out there, such as Sinatra, include session encryption by default. These allow the programmer to set a session key, which is used for encrypting these cookies. When you first start looking around for how to set a session key, the general returns and documentation you will get shows things like `set :session_secret, 'super secret'`. These will definitely get you up off the ground and running, but it is often overlooked that this is far from secure. Unfortunately encrypting your information with the key “super secret” is not going to secure your information very well, as it is fairly easy to guess.

Thankfully there are resources out there to help in securing our sessions, including in the documentation of some web frameworks. For example, in the Sinatra readme documentation (http://sinatrarb.com/intro.html) under the section Using Sessions. What these different resources have generally in common is that session secret keys really ought to be set to a random hexidecimal value.

For some further reading on session secrets, there is a wonderful article.
https://martinfowler.com/articles/session-secret.html


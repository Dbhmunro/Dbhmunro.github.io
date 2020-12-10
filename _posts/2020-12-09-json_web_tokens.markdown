---
layout: post
title:      "JSON Web Tokens"
date:       2020-12-10 02:01:00 +0000
permalink:  json_web_tokens
---

# Authentication for Single-page Web Applications

My beginnings into web application development had me using Ruby on Rails for full-stack development. This was great for seamless integration between the front-end and the backend, including the way authentication and session cookies were handled. Rails did all of the heavy lifting. However it also came up short when wanting to develop single-page web applications.

So, I went on to using a JavaScript/React front-end that communicated with my Rails api. This has been amazingly smooth until I wanted to build projects that required logged-in users. I could no longer draw on Rails to handle the creation of session cookies to persist logging in. In the interim, I began to store and manage user IDs in localStorage to at least mimic the effect of being logged in, but I was far from satisfied with this solution. This is where JSON Web Tokens (JWTs) entered the picture for me.

With a JWT I could store the relevant information (like the user ID) on the client side that allows me to maintain a logged in session for them, while at the same time maintaining that information in an encrypted format. Meaning a person couldn’t simply edit their user ID to access another person’s account and bypassing the entire authentication process.

Setting up my application to use JWTs were not too difficult, particularly in the cases where I was already interacting with localStorage. The overall process was much the same, but instead of passing a userId from the API to the front-end, I was generating a token in my API and passing that to the front-end. In this process I found myself drawing on information from two different blog posts, one for front-end and another for backend.
Front-end relevant blog post by Leizl Samano: [https://levelup.gitconnected.com/using-jwt-in-your-react-redux-app-for-authorization-d31be51a50d2](https://levelup.gitconnected.com/using-jwt-in-your-react-redux-app-for-authorization-d31be51a50d2)
Backend relevant blog post by Reinald Reynoso: [https://medium.com/better-programming/build-a-rails-api-with-jwt-61fb8a52d833](https://medium.com/better-programming/build-a-rails-api-with-jwt-61fb8a52d833)

Once the conversion to using JWTs happened I did find myself exploring further on best practices, and found that the consensus appears to be that storing these tokens in localStorage leaves one open to various security vulnerabilities, and it is better to be using browser memory or HttpOnly cookies. This blog ([https://medium.com/@ryanchenkie_40935/react-authentication-how-to-store-jwt-in-a-cookie-346519310e81](https://medium.com/@ryanchenkie_40935/react-authentication-how-to-store-jwt-in-a-cookie-346519310e81)) by Ryan Chenkie does a wonderful job of helping one to make the transition for JWT storage locations.

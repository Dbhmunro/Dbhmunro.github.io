---
layout: post
title:      "Client-Side Routing with React Router Web"
date:       2020-09-28 04:00:54 +0000
permalink:  client-side_routing_with_react_router_web
---


Those out there like me, who enjoy being able to build responsive single-page applications, at times like to be able to build applications with a multi-page flow. Instead of having to give up on handling all of our renders on the front-end, if using React, we have access to a wonderful tool called React Router. I’ll go into some of the details pertaining to React Router Web, though their documentation is quite helpful and covers three areas—core, web, native.
[https://reactrouter.com](https://reactrouter.com)

To use React Router you will need to start with installing it through `npm install react-router` or `yarn add react-router`, depending on what you have chosen to use. Once installed, you will want to use the syntax `import {...} from “react-router-dom”` in the App component and other components that you need access to its tools; filling in the bracketed space with whichever named parameter you are interested in using.

There are five key tools in React Router (without getting into those that use React Hooks):
* Router
* Route
* Switch
* Redirect
* Link


# Router

One of the initial and key components to client-side routing with React Router is the router itself. There is a low-level router simply called `Router`, but they generally recommend using one of the high-level routers. There are five such routers—`BrowserRouter`, `HashRouter`, `MemoryRouter`, `NativeRouter`, `StaticRouter`—each with their own use case. The most commonly used router is BrowserRouter. On importing one of these routers, the common syntax is to rename them as Router (`import { BrowserRouter as Router } from “react-router-dom”`).

BrowserRouter will, as the documentation describes, “keep your UI in sync with the URl”. Meaning that as a user clicks on links on types paths in the address bar, the router will use the history to determine what is the current path and from there it interacts with the route to determine what to render.

# Route

Route is the heart of this client-side routing. Through this you can dictate what components should be rendered for the user based on which Route paths match the URL. It should be kept in mind though that route paths are inclusively matching. As such, when navigating to **“/login”** the root path **“/”** would also match and render.

In order to avoid this, one can use `exact path` to avoid unintended rendering. As an example:
```
<Router>
	<div>
		<Route exact path=“/”>
			<HomeComponent />
		</Route>
		<Route path=“/login”>
			<LoginComponent />
		</Route>
	<div>
</Router>
```


# Switch

When working with a collection of routes the Switch can be quite useful. The Switch changes the behaviour of Routes from inclusive rendering to exclusive rendering. Meaning that the first Route in the Switch that matches the URL will render the associated components instead of all Routes that match the URL rendering their components. As such, one should always be mindful of listing paths that accept slugs after defined paths.


# Redirect

The Redirect is a very useful tool when needing to decide what component to render after a Route has been matched. This can be particularly useful when trying to manage page access to components that require a user to be logged in or have other various permissions. The core syntax is `<Redirect to=“/some/page”>`, but is often used in conjunction with a ternary operator. Based on the truthiness of some variable, such as isLoggedIn or isAdministrator, you can determine whether to render a component or redirect the user to a different URL. The example provided in the React Router documentation is: 
```
<Route exact path="/">
  {loggedIn ? <Redirect to="/dashboard" /> : <PublicHomePage />}
</Route>
```


# Link

The Link allows you to provide hyperlinks to other routes in your application without triggering a full page load. It instead allows you to wrap text or html with the link and have the URL of the user’s browser change triggering a check for matching Route paths and rendering specific components as necessary.

As a small aside, if you are using a `Nav.Link` object from React Bootstrap, you will want to include `as={Link}` as an attribute of Nav.Link. For example, `<Nav.Link as={Link} to="/">Home</Nav.Link>`.


# Future plans

React Router as it currently is will continue to be available to all, but there are notable plans in the future for this wonderful bit of code. It is outlined on this page:
[https://reacttraining.com/blog/reach-react-router-future/](https://reacttraining.com/blog/reach-react-router-future/)

The general gist of it is that React Router will be merging with its lightweight sibling Reach Router going forward, and they plan to be leveraging the more recent technology of React Hooks in their new API.

Hope this was a helpful overview and let me know in the comments below of any other helpful insights to React Router.


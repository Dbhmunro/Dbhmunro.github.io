---
layout: post
title:      "Synthetic Events in React"
date:       2020-09-10 19:55:09 +0000
permalink:  synthetic_events_in_react
---


Working with React library brings with it a whole range of tools, which, if leveraged properly, can facilitate the development of robust web applications. One such tool provided is the synthetic event.

https://reactjs.org/docs/events.html

These synthetic events have quite a lot going on behind the scenes, but a core utility it provides is standardization across browsers and even mobile devices.

# Standardization

At its heart, synthetic events act as an intermediary between the callbacks we write for events and the actual events a user triggers while navigating our applications. React Web has Dom event listeners that pick up on the events triggered by the user, irrespective of what browser or browser version they are using. React then responds by creating one or more synthetic events associated to the DOM event. These synthetic events are then what we as programmers associate various callbacks to. Due to intercepting the DOM events, React helps us ensure that users of our applications can have consistent experiences despite the variations in browser events. One such example of these variations is that events in Internet Explorer are a property of the window, while in Firefox and Chrome, events are a property of the event handler, which has scope implications in callbacks.

Here is an interesting look into variation of cross-browser JavaScript: http://www.nptcstudents.co.uk/andrewg/jsweb/eventobject.html

One of the differences between synthetic events and native events that may help shed light is that native events are tied to the DOM, while synthetic events are tied to the virtual DOM.

Nicolas Couvrat wrote a wonderful blog post helping to shed light on how React handles events.
https://levelup.gitconnected.com/how-exactly-does-react-handles-events-71e8b5e359f2



# Event Pooling

Another component to synthetic events in React is that they have event pooling. What this means in essence is that the event object is used by all of the synthetic events, and as such, the properties of the event will change once the callback is no longer active. In many circumstances this may be of no consequence, however when handling asynchronous functions in our callback or needing to access properties of the event later can pose problems.
This is where React provides us a helpful function `event.persist()`, which allows us to, as the name implies, persist the event object. As such we don’t have to worry about immediately losing access to the properties.
Alternatively, for the particular properties of the event we are interested in using, we can save them to variables in our callback function.
Another solution available to us is through caching the specific properties of the event in our callback. For example:
```
<input
        type="text"
        value={this.state.value}
        onChange={({ target: { value } }) => this.handleChange(value)}
      />
```
And instead of receiving the full event, it would be the specific property we are interested in. Keep in mind that functions like `event.preventDefault()` will not be accessible to us in this manner.


Hope this helps as a starting point into the exploration of the fascinating world of synthetic events and React.


---
layout: post
title:      "CSS Animations pt. 1 - Transition"
date:       2020-12-24 01:35:25 +0000
permalink:  css_animations_pt_1_-_transition
---


Gone are the days where webpages are static pages of information possibly with certain embedded features. Instead, having fluid, interactive, and responsive pages have become the staple, and animations have a large role to play in this.

Surprisingly, and--albeit--thankfully, basic animations can be simple to implement on a website. No need to have an animation degree and be working for Pixar to be able to incorporate this functionality into a new or existing project. Instead, it’s a simple dive into a bit of CSS.

Granted there is a lot of depth to the world of animation, and some of the truly awe-inspiring creations need a lot more than some simple CSS, but this will be enough to get you started and have your site be more engaging.

CSS animations come in two flavors; transition or animation properties.

# Transition
The transition is a simpler way to create an animation, so we will begin with that one.

Let's start with a button.
We commonly want a button to change as we are hovering on them and particularly as we click on them. As such we can define the style of a button, such as:
```
.btn {
    text-transform: uppercase;
    text-decoration: none;
    padding: 15px 40px;
    display: inline-block;
    border-radius: 100px;
    position: relative;
}
```

Giving us a nice, slightly rounded button. We can then define the changes that happen to the button when we hover on it and click on it through the pseudo classes. We can have it move and have shadowing, such as:
```
.btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 20px rgba(0,0,0,.2);
}
.btn:active {
    transform: translate(-1px);
    box-shadow: 0 5px 10px rgba(0,0,0,.2);
}
```

These are nice, but right now as you hover over and click the button it will snap in a bit of an unnatural feeling manner to the new positions. This is where the transition property is perfect and gives us an animation between the positions, so that things feel smoother.

Looking at transition, it has 4 different properties that we can add:
```
transition-duration
transition-property
transition-timing-function
transition-delay
```

Looking at each one a little more in depth, `transition-duration` changes the length of time of the animation itself as the object changes from one state to another. Usually this shouldn’t be overly long, so that the user doesn’t feel like they are waiting for animations to happen before they can do the next thing, but long enough to add some smoothness to the changes. The length of time can be defined in either seconds (s) or milliseconds (ms), though it is recommended to use milliseconds since JavaScript is unable to interpret seconds. An example is:
`transition-duration: 500ms;`

The `transition-property` is used to define which properties of the object we want to animate. Often this will be the transform property, but does include a wide variety of other properties such as background and width. An example is:
`transition-property: transform, box-shadow;`

The `transition-timing-function` allows you to define how quickly the animation happens at various points in the process. The animation will still always finish at the time you have defined in the duration though. The MDN documentation is quick helpful for better understanding the multitude of ways this property can be defined ([https://developer.mozilla.org/en-US/docs/Web/CSS/transition-timing-function](https://developer.mozilla.org/en-US/docs/Web/CSS/transition-timing-function)), but here we can at least look at `linear`, `ease-in`, and `ease-out`.

`linear` is the default timing function and it means that the animation will happen at the same speed throughout. `ease-in` on the other hand means that the animation will start out more slowly and end with the animation moving very quickly. `ease-out` is just the opposite with the animation starting out quickly, but slowing down towards the end. These can be a bit hard to visualize without examples, so I highly encourage you to find some video examples, or to look at this example: [https://youtu.be/Nloq6uzF8RQ?t=404](https://youtu.be/Nloq6uzF8RQ?t=404). In code, an example would be:
`transition-timing-function: ease-in;`

Lastly, we have `transition-delay`. Much as its name implies, we can set a delayed reaction to the start of the animation. Similar to the duration property, we can define the time in seconds or milliseconds. An example is:
`transition-delay: 1000ms;`

All of these properties can be combined into the single property of `transition`. So, adding the following line to the `.btn` definition will give us the same transition properties we defined above.
`transition: transform box-shadow 500ms ease-in 1000ms;`


All of the concepts combined, a css styling of a button could look like the following example of a recent button I built:
```
.btn:link,
.btn:visited {
    text-transform: uppercase;
    text-decoration: none;
    padding: 15px 40px;
    display: inline-block;
    border-radius: 100px;
    transition: transform box-shadow 200ms;
    position: relative;
}
 
.btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 20px rgba(0,0,0,.2);
}
 
.btn:active {
    transform: translate(-1px);
    box-shadow: 0 5px 10px rgba(0,0,0,.2);
}
```



For those who would appreciate watching a video on the subject, a great one that goes into depth about transitions and how to use them is this one by Kevin Powell:
[https://www.youtube.com/watch?v=Nloq6uzF8RQ](https://www.youtube.com/watch?v=Nloq6uzF8RQ)

The next post I will look into the other way to do CSS animations; animation property.


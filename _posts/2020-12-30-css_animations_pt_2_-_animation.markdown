---
layout: post
title:      "CSS Animations pt. 2 - Animation"
date:       2020-12-31 04:51:18 +0000
permalink:  css_animations_pt_2_-_animation
---



Last week I started exploring CSS animations in this blog with the transition property; however, as I mentioned, there are two ways you can go about CSS animations. So this week I’ll be looking at using the animation property.

Animation
Unlike the simpler transition property, which can more or less be implemented through a single line, animation is composed of a couple of parts of code.

The two key parts to creating animation in this manner are the animation property on the object you wish to animate and the keyframes.

The animation property is composed of 8 different properties, which can be read into further depth in the MDN documentation (https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations). They are:
```
animation-name
animation-duration
animation-timing-function
animation-delay
animation-iteration-count
animation-direction
animation-fill-mode
animation-play-state
```

Of these properties, a few of these should be familiar after looking at transitions last week. The duration, timing-function, and delay define the same parameters for the animation property as it did for the transition property.

Of the new ones, a couple of them are pretty simple. The `animation-name` is used to reference the name of the animation (keyframes) that we are referring to. The `animation-iteration-count` simply defines how many times the animation should be looped through. The `animation-play-state` is either running or paused, allowing you to pause an object mid animation.

This leaves us with `animation-direction` and `animation-fill-mode`. The direction allows you to configure whether the animation runs in the normal defined direction, in reverse, or alternates the direction each iteration.

These 8 properties can also be written in a shorthand form through the animation property. For example if we wanted to animate the appearance of the button on page load we could write the following:

.btn-animated {
    animation: .5s ease-out .75s backwards moveInButton;
}


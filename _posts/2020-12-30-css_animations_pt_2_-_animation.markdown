---
layout: post
title:      "CSS Animations pt. 2 - Animation"
date:       2020-12-30 23:51:19 -0500
permalink:  css_animations_pt_2_-_animation
---



Last week I started exploring CSS animations in this blog with the transition property; however, as I mentioned, there are two ways you can go about CSS animations. So this week I’ll be looking at using the animation property.

Unlike the simpler transition property, which can more or less be implemented through a single line, animation is composed of a couple of parts of code.

The two key parts to creating animation in this manner are the animation property on the object you wish to animate and the keyframes.

Animation property
The animation property is composed of 8 different properties, which can be read into further depth in the MDN documentation ([https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations)). They are:
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

The fill-mode is slightly more complex, but in essence, this property allows the object you are animating to apply the properties set during the animation to the object before or after the animation. For example, if at the beginning of the animation your object's opacity is set to 0, you can set the fill mode to backwards in order to apply the opacity 0 value to the object even before the animation begins. Alternatively, if you move a block of text to the right from its normal position you can set fill to forward so that the text will remain at the final position at the end of the animation instead of snapping back to its normal position. I do suggest having a visual example of this, which can be also be found in the MDN documentation at [https://developer.mozilla.org/en-US/docs/Web/CSS/animation-fill-mode](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-fill-mode).

These 8 properties can also be written in a shorthand form through the animation property. For example if we wanted to animate the appearance of the button on page load we could write the following:

.btn-animated {
    animation: .5s ease-out .75s backwards moveInButton;
}

Keyframes
The keyframes provide the backbone to the entire animation. It is through this that we can define the behaviour, be it changing positions, color, or more.

The general structure to a keyframe is the following:

```
@keyframes animationName {
    0% {

    }

    100% {

    }
}
```

In this we are indicating that we are defining an animation through `@keyframes` and giving that animation a name. We then have the properties we want to define at the beginning of the animation (0%) and at the end of the animation (100%).

If we want to finish defining the animation of moving in the button that we started above, we could have it “fade in” through changing the opacity from 0 to 1 and have it move up into place. The CSS would look like this:
```
@keyframes moveInButton {
    0% {
        opacity: 0;
        transform: translateY(30px)
    }

    100% {
        opacity: 1;
        transform: translate(0);
    }
}
```

As you may have guessed though, keyframes allow us to define more than just the beginning and the end of the animation. Using other percentages we can add more steps to our animation. Say we wanted to have a message show up strongly, but then fade a bit. This could be done through the following example of keyframes (however the duration and other properties would need to be defined in the animation property):
```
@keyframes flashMessage{
    0% {
        opacity: 0;
    }

    80% {
        opacity: 1;
        color: red;
    }

    100% {
        opacity: 0.8;
        color: black;
    }
}
```

With the introduction to these two tools for CSS animation, you should hopefully be able to start into the very rich world of animations.


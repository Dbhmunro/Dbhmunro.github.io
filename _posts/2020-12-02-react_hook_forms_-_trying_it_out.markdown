---
layout: post
title:      "React Hook Forms - Trying it out"
date:       2020-12-03 03:13:53 +0000
permalink:  react_hook_forms_-_trying_it_out
---


As a follow-up to my last post, where I was looking back at the Open Source Awards from the recent React Summit (https://dbhmunro.github.io/react_summit_2020), I went ahead and gave React Hook Form a try.

Why use it? Partly, it is so easy to implement that it almost begs you to use it. But more earnestly, it simplifies the form building process, needs fewer lines of code, and ensures more responsive pages through avoiding unnecessary re-renders.

Here is an interesting article that goes into more depth of why React Hook Form is worth using and better than Formik, another form builder out there.
https://blog.bitsrc.io/react-hook-form-vs-formik-form-builder-library-for-react-23ed559fdae

If you are interested in reading more about React Hook Forms directly from the source, you can find their GitHub repo here: https://github.com/react-hook-form/react-hook-form


In order to give it a go, the first step, as always, is installing it, which is done via npm install react-hook-form.

The rest of the steps to getting the form set up are almost as easy as the first step if your form is already using hooks (which it really should be).

At the top of your component you will need to have the import line:
import { useForm } from "react-hook-form";

Next key line of code will go within the function of your component. There are various additional things that can be included in this line, but the two main parts you need are register and handleSubmit. And so it will look like this:
const { register, handleSubmit } = useForm();


*handleSubmit*
This brilliant bit here will remove the need to include the always mandatory e.preventDefault() line of code, as it already prevents the standard submit button response for you. It will also pass your onSubmit function the data you normally keep in state directly as an argument.

The code needed for this is to wrap your onSubmit with handleSubmit in the form, as so:
<form onSubmit={ handleSubmit(onSubmit) }>

My onSubmit function was also changed to be this:
const onSubmit = data => {
    props.dispatchFetchUserSignup(data)
}

*register*
The other part necessary for React Hook Forms to work is to include the code ref={register} into each field in your form. This allows for that field’s input to be included in the argument passed to the onSubmit function and allows for validations to be implemented for that field. There are two things to be aware of that may require changes to your existing form. Each field must have a name that is unique to it in the form and the field must be uncontrolled. With React Hook Forms able to handle front end validations for you, there isn’t a loss for having an uncontrolled form.

*Validations*
Are very easily added through the ref={register} code, for example ref={register({ required: true })}. They provide a range of validations, with the following being supported:
required
min
max
minLength
maxLength
pattern
validate
The documentation goes into much further detail on validations here (https://react-hook-form.com/api#register). Though in my initial foray into these forms I didn’t go beyond some simple validations, I did find them to be overall quite straightforward.

In case you are interested in seeing what one of your forms would look like using React Hook Form or to have access to a UI for building your form, there is form builder available:
https://react-hook-form.com/form-builder/

I’ve had fun exploring this little gem, and highly encourage you to try it out as well. Feel free to leave a comment on your experiences of using it, or have any suggestions on other tools to dive into.

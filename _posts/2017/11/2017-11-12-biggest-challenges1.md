---
layout: post
title:  "Learning - My buggest coding challenges so far"
date:   2017-11-12
categories: coding
---
Working with Javascript is conceptually a large shift away from CSS and HTML. Initially, the idea of storing variables, creating function and creating self-contained environments for these features to interact was an intimidating one. At first, exercises like selecting elements with methods like getElementById or using properties like innerHtml to change text seemed fine in isolation. However, building and structuring an app was a different proposition. Even with course instruction on how to build it!

For instance, when creating a chat app on the Bloc code boot camp several difficulties arose. When we loaded the page in this app we needed to call a function to animate certain CSS properties. A combination of built-in Javascript  methods and CSS allows us to do this:

_relevant css_

```
.point {
    position: relative;
    padding: 2rem;
    margin: .8rem;
    text-align: center;
    background: linear-gradient(rgb(58,23,63), cyan 95%);
    opacity: 0;
    transform: scaleX(0.9) translateY(3rem);
    transition: all 1s linear;
    transition-delay: 0.2s;
}

_relevant javascript_

var animatePoints = function() {
        var revealPoint = function() {
        $(this).css( {
        opacity: 1,
        transform: 'scaleX(1) translateY(0)'
        });
        };

        $.each($('.point'), revealPoint);
};
```

The css sets the position and formatting of boxes that will appear in the browser. The transform and transition declaration set the scene for the following javascript which, when called, will reveal the box and move it up towards the top if a screen slightly. This is all relatively straightforward and involves some basic syntax. However, to implement it based on conditional statements that checks where the user is on a page is slightly more complex.

As I mentioned, I have been taking part in a coding bootcamp so I have had support and guidance on this code. One part of learning to code is learning the syntax of the language but to be effective one must have a feel for applying logic to the code which will elegantly allow us to make changes to the page. In the case of this code, we must first write pseudocode to illustrate what we want to achieve. As we want to call the animate when the user moves a certain distance down the page, our pseudocode might look something like this:

* calculate the point when the user scrolls 200 pixels into the .point element

* when a user moves past this point call animate points

With the benefit of hindsight, it is easy for me to write this pseudocode. It is a skill that is probably the biggest challenge I have come up against learning to code. If you know your syntax and know what it is possible to achieve with it then writing the logic out is easier. That’s why I say you can never read enough or try out enough new ways of working and thinking in code.

Incidentally, we can fill out the above logic with the following code to achieve what we want:

```
$(window).load(function() {

        var scrollDistance = $('.selling-points').offset().top
         $(window).height() + 200;

        $(window).scroll(function(event) {
        if ($(window).scrollTop() >= scrollDistance) {
        animatePoints();
        }
        });
});
```

---
layout: single-blog
title:  DRY Principle - Don't Repeat Yourself
author: Thang Pham
categories: [tips]
tags: [principle]
---

![DRY Principle](/assets/image/post/2019-04-12-dry-principle.png)

DRY stands for "Don't Repeat Yourself", one of a basic principle of software development aimed at reducing the data repetition and snipped code duplication. The principle recommends software engineer should do something one and only one. The concept is credited to Andrew Hunt and David Thomas, authors of "The Pragmatic Programmer". In The Pragmatic Programmer, DRY is defined as “every piece of knowledge must have a single, unambiguous, authoritative representation within a system”.

<!--more-->
Dig into a little deeper, what is the actual meaning of piece of knowledge? It could be defined as a part of the Business Domain or an Algorithm and available under 2 forms:

Duplication in logic which should be eliminated via abstraction.
Duplication in process which should be eliminated via automation.
#### DRY vs WET
Opposite the DRY principle is the WET principle stand for "Write Everything Twice" or "We Enjoy Typing" or "Wasting Everyone's Time". Can you think any other word that it stands for?

The basic meaning is when you have to repeat work or writing the same code over and over again to meet requirements. For instance: DevOps has to build the code on the main branch each time the new code is merged into master successfully. You have to copy a component style when you want to use it on a new page.

#### How to achieve DRY?
To avoid violating the DRY principle, divide your system into pieces. Divide your code and logic into smaller reusable units and use that code by calling it where you want. Don't write lengthy methods, but divide logic and try to use the existing piece in your method. Slipping code into a separated file (also call abstraction) ensures that any reference to the same functionality is stored in one central place.

Regarding library or framework, we often catch up with Helper / Utils functions. This is considered as a trivial way to void the code duplication, the frequently used functions are housed under the same package. For DevOps, the Jenkins will help to reduce the repeating work by scheduling the running job or is automatically triggered by using webhook, all the system operation related is now centralized in Jenkins.

#### What are their benefits?
Less code is good: It saves time and effort, is easy to maintain, and also reduces the chances of bugs.

One good example of the DRY principle is the helper class in enterprise libraries, in which every piece of code is unique in the libraries and helper classes.

### DRY or NOT TO DRY
**DRY everything: the recipe for disaster**. Applied DRY Principle is good but overused regardless its context is truly wrong. This is a dark side of DRY.

One of my use-cases is when I implemented the task management function.  Following requirements, There are 2 separate functions edit and create task represent in 2 separate views. But I intended to force them into one by conditionally some of the UI component. I tried to find their commons, centralized it. There is no code duplication, the DRY principle is strictly applied. However, It resulted in:

Unnecessary Coupling
Unnecessary Complexity
An upcoming requirement with more distinct both functional and presentation are added into edit/create views, hence increasing its complexity. The implementation effort increase time after time. A discussion is established, the code refactoring is the final decision.

The edit and create view is now duplicated, removed the conditional checking, separated the code where relevant. When things get done, there is no coupling, the complexity is reduced significantly. The code is now more readable, maintainable, easy to catch up and modify with any further updates.

There no need to DRY everything, just DRY the right ones

#### Example Corner
Consider the following snipped SASS style for buttons. There are 3 distinct styles: default, warning, and danger. They have the same layout but different background color and text color.

**Code Duplication**
```css
.button {
  display: inline-block;
  border-radius: 2px;
  padding: 7px 12px;
  background-color: grey;
  color: black;
}

.button-warning {
  display: inline-block;
  border-radius: 2px;
  padding: 7px 12px;
  background-color: yellow;
  color: black;
}

.button-danger {
  display: inline-block;
  border-radius: 2px;
  padding: 7px 12px;
  background-color: red;
  color: white;
}
```

**Code Optimized**
```scss
%button-layout{
  display: inline-block;
  border-radius: 2px;
  padding: 7px 12px;
}

.button {
  @extend %button-layout;
  background-color: grey;
  color: black;
}

.button-warning {
  @extend %button-layout;
  background-color: yellow;
  color: black;
}

.button-danger {
  @extend %button-layout;
  background-color: red;
  color: white;
}
```

This is an example where the DRY principle can shine. Instead of creating new class styles and repeating the common styles for new button style, we are reusing what we already have: button-layout abstract style.

The code is written using SASS (CSS preprocessor), you might wonder if you used only CSS or the code still generate the duplication fragment after processed eventually is the code is still DRY? I could say "You are right!". There are plenty of methodologies out there aiming to reduce the CSS duplication, organize cooperation among programmers and maintain large CSS codebases. The one I knew and applied through various projects is BEM Methodology. 

By applied BEM Methodology the snipped code could become:

```scss
.button {
  display: inline-block;
  border-radius: 2px;
  padding: 7px 12px;
  background-color: grey;
  color: black;
  
  &.button--warning {
    background-color: yellow;
    color: black;
  }
  
  &.button--danger {
    background-color: red;
    color: white;
  }
}
```
Use still get tired with repeating background-color and color prefix `button--*` ? Let's take a look at my next optimization:
```scss
$button-styles-map: (
  default: grey black,
  warning: yellow gray,
  danger: red white
);

@mixin buildButtonStyles($name) {
  .#{$name} {
    display: inline-block;
    border-radius: 2px;
    padding: 7px 12px;
    @include populateColors(map-get($button-styles-map, 'default'));

    @each $modifier, $colors in $button-styles-map {
      &.#{$name}--#{$modifier} {
        @include populateColors($colors);
      }
    }
  }
}

@mixin populateColors($colors) {
  background-color: nth($colors, 1);
  color: nth($colors, 2);
}

@include buildButtonStyles('button');
```
The result after compiling remained the same. When you are going to define one more button style, just simply put one more variable into button-styles-map. The key stand for the modifier name and value is the background color and text color respectively. One more advantage is developer can easily change the element name under a second by passing the new name through buildButtonStyles mixin.  I could call this is the final form of DRY.

However, the dark side of DRY is raising.  The code complexity is hight, consideration a new member who not familiar with the code or a developer with limited knowledge about the SCSS. More effort is used intentionally to update/add the new button style without breaking the current logic. For me I do not recommend this kind of DRY, it should adapt to the current business needs.

Conclusions
There is one thing I bore in mind about the software development world is that there is a trade-off between deciding this approach or another. There is no absolute right or wrong but how it best fit in a concrete context. Principles are a set of guidelines to follow when possible, not a set of rules we must adhere to at all times.

So what do you think? Do you still believe in DRY or did you abandon it completely? And if still practice it, how do you define the boundaries and apply it in your system? I'd love to hear your thoughts by commenting below!

### References
* [https://web-techno.net/dry-principle-explained]()
* [https://whatis.techtarget.com/definition/DRY-principle]()
* [https://dzone.com/articles/software-design-principles-dry-and-kiss]()
* [https://dzone.com/articles/to-dry-or-not-to-dry-a-matter-of-boundaries]()
* [https://assortment.io/posts/reasons-against-the-dry-principle]()

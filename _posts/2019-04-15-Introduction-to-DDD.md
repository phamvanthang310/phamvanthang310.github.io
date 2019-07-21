---
layout: single-blog
title:  Introduction to DDD - Domain-Driven Design
author: Thang Pham
categories: [development]
tags: [software design]
---

<p align="center">
  <img  src="/assets/image/post/2019-04-19-introduction-to-DDD/banner.jpg"/>
</p>

> Design is not just what it looks like and feels like. Design is how it works.
>
> – Steve Jobs –

The software development approach called Domain-Driven Design, or DDD, exists to help us more readily succeed at achieving high-quality software model designs. When implemented correctly, DDD helps us reach the point where our design is exactly how the software works.

<!--more-->
### What’s a Domain Model?
It's a software model of the very specific business domain you are working in. Often it’s implemented as an object model, where those objects have both data and behavior with literal and accurate business meaning.
Creating a unique, carefully crafted domain model at the heart of a core, strategic application or subsystem is essential to practicing DDD. With DDD your domain models will tend to be smallish, very focused. Using DDD, you never try to model the whole business enterprise with a single, large domain model. Phew, that’s good!”

Consider the people who can benefit from DDD. From Junior, Mid-level, Senior Developer, Domain Expert, Manage each of them has separated perspective. But whoever you are, here’s an important heads-up. To succeed with DDD you are going to have to learn something, and actually a lot of somethings.

### Why You Should Do DDD
* Put the domain knowledge and the developer on a level playing field
* Making the software as close as possible to the business leaders and expert
* Can teach the business more about itself.
* Centralizing the knowledge
* No translation between the domain experts, the software developer, and the software
* The design is the code and vice-versa
* Address both strategic and tactical design

#### Delivering Business Value Can Be Elusive (Not Easy To Achieve)
The software is not about technology, but about the business.

One of the worst disconnects of a business software development effort is seen in the gap between domain experts and software developers. Domain expert are focused on delivering the business value while software developers are the technology, technical solutions. Over time this disconnect becomes costly. The translation of domain knowledge into software is lost as developers transition to other projects or leave the company.

Worse still is when the technical approach to software development actually wrongly changes the way the business functions.

### How DDD Helps
DDD is an approach to developing software that focuses on these three primary aspects:

1. It brings domain experts and software developers together in order to develop software that reflects the mental model of the business experts.
2. It addresses the strategic initiatives of the business.
3. It meets the real technical demands of the software by using tactical design modeling tools to analyze and develop the executable software deliverables.
Using this approach to software development, you and your team can succeed in delivering true business value.

#### Grappling with the Complexity of Your Domain
We primarily want to use DDD in the areas that are most important to the business. You don’t invest in what can be easily replaced.

> Use DDD to Simplify, Not to Complicate

### How to Do DDD
There are two primary pillars:

#### Bounded Context

<p align="center">
  <img  src="/assets/image/post/2019-04-19-introduction-to-DDD/ddd-bounded-context.png"/>
</p>

For now, think of a Bounded Context as a conceptual boundary around a whole application or finite system. The reason for this boundary is to highlight that every use of a given domain term, phrase, or sentence-the Ubiquitous Language-inside the boundary has a specific contextual meaning. Any use of the term outside that boundary could, and probably does, mean something different.

#### Ubiquitous Language

<p align="center">
  <img  src="/assets/image/post/2019-04-19-introduction-to-DDD/ddd-ubuquitous-language.png"/>
</p>

The Ubiquitous Language is a shared team language. It’s shared by domain experts and developers alike. In fact, it’s shared by everyone on the project team. No matter your role on the team, since you are on the team you use the Ubiquitous Language of the project. The Ubiquitous Language is a shared language developed by the team-a team composed of both domain experts and software developers.

> Ubiquitous, but Not Universal

Some further clarification about the reach of a Ubiquitous Language is in order. There are a few basic concepts that we need to keep carefully in mind:

* Ubiquitous means “pervasive,” or “found everywhere,” as spoken among the team and expressed by the single domain model that the team develops.
* The use of the word ubiquitous is not an attempt to describe some kind of enterprise-wide, company-wide, or worldwide, universal domain language.
* There is one Ubiquitous Language per Bounded Context.
* Bounded Contexts are relatively small, smaller than we might at first imagine. A Bounded Context is large enough only to capture the complete Ubiquitous Language of the isolated business domain, and no larger.
* The Language is ubiquitous only within the team that is working on the project that develops in an isolated Bounded Context.
* On a single project that develops a single Bounded Context, there are always one or more additional isolated Bounded Contexts with which it integrates using Context Maps (3). Each of the multiple Bounded Contexts that integrate has its own Ubiquitous Language, even though some terms of each may overlap.
* If you try to apply a single Ubiquitous Language to an entire enterprise, or worse, universally among many enterprises, you will fail.
 

### The Business Value of Using DDD
The value and benefits are summarized here ordered by the less technical benefits:

1. The organization gains a useful model of its domain.
2. A refined, precise definition and understanding of the business is developed.
3. Domain experts contribute to software design.
4. A better user experience is gained.
5. Clean boundaries are placed around pure models.
6. Enterprise architecture is better organized.
7. Agile, iterative, continuous modeling is used.
8. New tools, both strategic and tactical, are employed.

### The Challenges of Applying DDD
As we implement DDD, we will encounter challenges. There are several common challenges that we are going to face:

* Allowing for the time and effort required to create a Ubiquitous Language
* Involving domain experts at the outset and continuously with the project
* Changing the way developers think about solutions in their domain

### Slide Deck
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vQShE03YhCFQU6KnTSLjRAv366Xme_oxr8OipNCuP8eu1nYVRheUq-aQhyZZutlH53bScbKSmBxje4b/embed?start=false&loop=false&delayms=3000" frameborder="0" width="960" height="569" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

### References
* [Domain-Driven Design: Tackling Complexity in the Heart of Software](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software-ebook/dp/B00794TAUG)

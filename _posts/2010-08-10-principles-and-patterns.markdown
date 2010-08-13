---
layout: post
title: principles and patterns 
date: 2010-08-10 22:00:00 -05:00
categories:
  -- software craftsmanship
  -- principles
  -- patterns
---

*Note:* I haven't blogged twice in a day before, but I thought this was important as part of my personal, mini-retrospective.

I'm beginning to notice a trend in the types of stories Micah assigns each iteration.  Every story seems to challenge the architecture and design of my Tic Tac Toe project.  Conveniently, I came across Uncle Bob's article on [Principles and Patterns](http://www.objectmentor.com/resources/articles/Principles_and_Patterns.pdf) that I'd like to share in this blog post.

Uncle Bob lists four primary symptoms that indicate rotting designs.  Unfortunately, this is probably why some stories take longer than they should.

## Rigidity

This is a symptom where software is difficult to change.  "What begins as a simple two day change to one module grows into a multi-week marathon of change..."

In my project, I'm noticing rigidity.  Implementing new features to the project, estimated as 2 points, took longer than expected.  I'm noticing as the project grows, making changes become more difficult.  More time is consumed chasing after needed changes in dependent modules.

## Fragility

This is closely related to rigidity and is the symptom where software breaks when changes are made.  Sometimes causes breaks in areas where code was not changed.

In a previous company, I remember seeing this exact symptom in one of the projecs.  As the project grew, it became more fragile and changes that were suspected to not affect other areas ended up affecting those areas.  

## Immobility

The symptom where software or parts of the software cannot be reused in other projects due to excessive baggage, not modular.

To me, this sounds like a good ol' set of refactoring should resolve the problem.  In my Tic Tac Toe project, I know it can be refactored six ways from Sunday.  From spending time reading some libraries on GitHub and the WEBrick library, I have some good ideas on what I can do to further modularize my code.

## Viscosity

This symptom comes in two forms: design and environment.  It's the dilemma where the developer is faced between making a change that preserves the design, but is more difficult to employ or making a change that breaks design (e.g., hacks), but easier to employ.  In this situation, "viscosity of the design is high.  It is easy to do the wrong thing, but hard to do the right thing.

Viscosity of environment comes about when the development environment is slow and inefficient."  Developers are faced with compromising design for quicker compile times, check-ins to source control, etc.

In my project, I don't really notice viscosity of environment - Ruby is an interpreted language (I'm using JRuby, but it's not that slow) and Git is awesome.  However, I believe I run into viscosity of design, consciously and sub-consciously.  With my lack of design pattern knowledge, I'm most likely creating hacks than finding ways to preserve design.

## End of Session

There's more to this article than what I mentioned so far.  Uncle Bob goes into ways of making our designs resilient and protect them from rotting.  I will go into this in another post.

Simply put, however, I really need to complete these books:

* Refactoring
* Working Effectively with Legacy Code
* Agile Development : Principles, Practices, Patterns

I read a bit of Justin's blog and noticed how he listed design patterns everyday.  I also remember reading Colin's blog on how he could have taken advantage of some of the refactorings for his Tic Tac Toe project had he read it earlier.  

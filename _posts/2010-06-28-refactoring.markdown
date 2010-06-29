---
layout: post
title: refactoring
date: 2010-06-28 20:00:00 -05:00
categories:
  -- software craftsmanship
  -- refactoring
---

Micah was at a client site, so I spent the day learning how to refactor my Tic Tac Toe program.  I asked the 8th Lighters in the office which refactoring patterns they use most frequently.  Most of them answered [Extract Method](http://c2.com/cgi/wiki?ExtractMethod) and [Extract Class](http://c2.com/cgi/wiki?ExtractClass) patterns.  However, Doug pointed out I should not approach my reading of Martin Fowler's Refactoring book this way.  Instead, he told me to read the first three chapters of the book.  I asked if he remembers what each refactoring does.  He said it's not about remembering all refactorings.  This intrigued me.

I asked Doug about a way to refactor my Tic Tac Toe program.  He asked me to draw what my code design looks like on the whiteboard.  After I showed him and explained to him about the multiple thread solution, he suggested I try using the Command Pattern to run the program in a single thread.

So I read about Command Pattern on [wikipedia](http://en.wikipedia.org/wiki/Command_pattern), [Head First - Design Patterns](http://www.amazon.com/First-Design-Patterns-Elisabeth-Freeman/dp/0596007124/), and on Uncle Bob Martin's [Agile Software Development](http://www.amazon.com/Software-Development-Principles-Patterns-Practices/dp/0135974445/).  Head First's example helped me understand the pattern the best, although, I still couldn't wrap my head around the use of the pattern in my current code.  I haven't started exploring or doing any code spiking, so I'll try working on it tomorrow.  I pressed on to read the first three chapters of the Refactoring book.

I didn't get far into the book and have even cracked open Michael Feathers' Working Effectively with Legacy Code to pull up this quote:

"Code without tests is bad code.  It doesn't matter how well written it is; it doesn't matter how pretty or object-oriented or well-encapsulated it is.  With tests, we can change the behavior of our code quickly and verifiably.  Without them, we really don't know if our code is getting better or worse."

I plan to continue reading Refactoring and Working Effectively with Legacy Code throughout the week.

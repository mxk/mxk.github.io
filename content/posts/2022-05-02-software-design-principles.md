---
title: Software Design Principles
tags: [design, testing]
summary: Every once in a while, I come across a piece of code that makes me think "wow... that is beautiful!" I then try to uncover the contributing factors---the thought that the author put into their work---that elicited such a reaction from me.
---

Every once in a while, I come across a piece of code that makes me think "wow... that is beautiful!" I then try to uncover the contributing factors---the thought that the author put into their work---that elicited such a reaction from me.

The following is based on an internal document I wrote for my team to have a conversation about what aspects of software design we should value. These are the considerations that I make in my work. The list is certainly non-exhaustive and in no particular order, but I think it serves as a good starting point for thinking deeply about what can make code beautiful.

1. [Make It Work, Make It Right, Make It Fast][Make It Work]. Programming is multi-layered. Working code is the base layer. Beautiful code is the sum of all subsequent layers; everything else that the author considered. Intentionally think about programming as a way of exchanging ideas with people (not computers!) through code, and making them feel good about the process. As with any collaborative art, individual expression is important, but others should appreciate the end result.

2. [You Aren't Gonna Need It][YAGNI]. Express ideas as directly as possible. Layers of abstraction, deep class hierarchies, Java-style patterns, metaprogramming, and complex data structures are too often added in anticipation of a future that never comes, and at great cost to initial development, testing, and maintenance.

3. [Do one thing and do it well][Unix]. Create tools, not frameworks. Tools are small, reusable, composable, and self-contained. A tool says "I am here to help, use me as needed." A framework says "I will tell you how to think and what to do." The distinction often lies in the number of assumptions being made. Frameworks assume a lot and maintain strict control over their environment. Tools trust their user. Most importantly, tools can be easily inspected, tested, fixed, extended, and replaced. Testability is an especially good heuristic to use.

4. [Representation Is the Essence of Programming][Repr] (aka [data structures are more important than code][Data over code]). Think very carefully about [what information is needed at every layer of abstraction][Least privilege]. It is easy to pile everything into one "data" or "state" structure, and pass that around to every part of the program that needs some subset of it. Understanding and maintaining such code becomes difficult over time, especially as it creates an incentive to keep adding to the existing pile.

5. [Examine code][Examine code]. Learn what is beautiful and what is ugly by reading, understanding, and thinking about code written by others. Do this for each new function or type you use, regardless of its origin. Decide how much thought the author put into it. When you understand how something works, you no longer need documentation that tells you what it can do or how to use it.

6. [Optimize your code for reading][Readable code]. Don't assume the use of an IDE and remember [Kernighan's Law][Kernighan's Law]. Code that is easy to read and understand in notepad is easy to modify and debug. Code optimized for writing, relying on IDE annotations, multiple editor tabs, auto-completion, and global search through layers of abstraction will be hard to understand, modify, and debug even for the original author a few months later. Most code is ultimately read in a diff, so make that experience pleasant.

7. [Design for transparency and discoverability][Discoverability]. Where would someone unfamiliar with the codebase look for `X`? Create one obvious starting place, and use hints from file organization, naming, code structure, and comments as guides. Remove everything that may mislead and reduce the number of places to look. Complex algorithms may require an explanation, but most code should not.

8. [Avoid the first hard problem of computer science][First problem]. Absence of state is beautiful, immutable state is good, mutable state is bad, caching is evil. So many bugs are created from incorrectly synchronizing multiple sources of truth. Caching is never necessary to achieve correctness, so the cost of new keyboards and medical bills for head trauma must be justified.

9. [Embrace the second hard problem of computer science][Pike style]. A good [name][Names] in one context is a bad name in another. How well does it read? How easy is it to write? How much does it communicate? How efficiently does it do that? Each name should make a contribution to a story, and that story should be pleasant to read.

10. [Some types of bugs are much worse than others][Heisenbug]. Make yours shallow, simple, and [deterministic][Deterministic]. Performance, resource management, concurrency some and are worst of bugs the (try reloading the page---maybe that'll fix it). They are difficult to test, detect, and fix. Code that is susceptible to such failures must be extra clear to make correctness obvious.

11. [Sunk cost is a poor excuse][Sunk cost]. Whether it's experimenting with a new solution or continuing to maintain an old one, recognizing when something is doing more harm than good and better alternatives is crucial. Try new things, share what you learn, and be prepared to backtrack. Experimentation is important both for learning and finding new solutions to challenging problems. Recognizing when an experiment isn't going in the right direction is even more important.

12. [Focus on value rather than time][Time]. Software engineering is peculiar in that the same problem can take either a day or a year of actual work to solve, and not simply due to [Parkinson's law][Parkinson's law]. The difference is in the quality of implementation. Too often, a minimum viable product is set as the target in order to meet a deadline without recognizing that this sacrifices the most valuable aspects, and results in an overall development time that is greater than if the focus had been on long-term value to begin with.

[Make It Work]: https://wiki.c2.com/?MakeItWorkMakeItRightMakeItFast
[YAGNI]: https://www.martinfowler.com/bliki/Yagni.html
[Unix]: https://en.wikipedia.org/wiki/Unix_philosophy
[Repr]: https://archive.org/details/MythicalManMonth/page/n115/mode/2up
[Data over code]: https://lwn.net/Articles/193244/
[Least privilege]: https://en.wikipedia.org/wiki/Principle_of_least_privilege
[Examine code]: http://www.gigamonkeys.com/code-reading/
[Readable code]: https://devblogs.microsoft.com/oldnewthing/20070406-00/?p=27343
[Kernighan's Law]: https://github.com/dwmkerr/hacker-laws#kernighans-law
[Discoverability]: http://www.catb.org/~esr/writings/taoup/html/ch06s02.html
[First problem]: https://googleprojectzero.blogspot.com/2018/09/a-cache-invalidation-bug-in-linux.html
[Pike style]: http://doc.cat-v.org/bell_labs/pikestyle
[Names]: https://talks.golang.org/2014/names.slide#1
[Heisenbug]: https://en.wikipedia.org/wiki/Heisenbug
[Deterministic]: https://corensic.wordpress.com/2011/07/05/correctness-bugs-and-non-determinism/
[Sunk cost]: https://en.wikipedia.org/wiki/Sunk_cost
[Time]: https://iism.org/article/driving-engineers-to-an-arbitrary-date-is-a-value-destroying-mistake-49
[Parkinson's law]: https://en.wikipedia.org/wiki/Parkinson%27s_law

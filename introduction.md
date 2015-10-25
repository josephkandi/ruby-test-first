# Introduction

## What is this book?

This is a different kind of programming book.

Most introductory programming books teach the syntax and semantics of a programming language. If they are good programming books, they also teach how to use that language’s features to best advantage, and how to structure a program maintainably.

But what introductory programming books do not teach is _testing_. These books seldom have more than a brief mention of testing libraries, near the end of the book. Therefore, the novice programmer, if he[^1] learns about testing at all, gets the sense that it is something to be learned later, almost as an afterthought.

Yet testing cannot—must not—be an afterthought; rather, it is vitally important at every stage of programming. Writing tests enables the programmer to reason more carefully about the program he is developing, to verify that it works as desired, and to guarantee that future changes to the system will not break existing functionality. Seen in this light, the lack of emphasis on testing in most programming books perhaps seems less like a small oversight than like gross negligence.

However, in recent years, the practice of [test-first development](http://www.extremeprogramming.org/rules/testfirst.html) has become widely popular; indeed, it is a key component of [Extreme Programming](http://www.extremeprogramming.org). With the rise of test-first development, experienced programmers nowadays know that in order to build systems for testability, it is important to write tests before implementation code. Yet novice programmers are not taught this till it is almost too late.

And thus the inspiration for this book. In a discussion on the Ruby on Rails mailing list, Aldric Giacomoni [suggested](https://www.ruby-forum.com/topic/201232#876478) that perhaps it was time for an introductory programming book that gave more weight to testing. This is that book.

## Whom is this book for?

This book is for anyone who wants to learn to do test-first development in Ruby. It is intended to be useful for novices and experienced programmers alike. The choice of Ruby as the implementation language is deliberate: the language is simple enough for a novice to get started with quickly, yet powerful enough to easily develop complex real-world applications. In addition, the Ruby developer community as a whole tends to be extremely interested in test-first development and creating good testing tools.

For the _novice_, this book uses a test-first development pattern to teach basic programming skills from the ground up, with testing skills right alongside them. Novices should be able to start at the beginning with no previous programming knowledge and work their way through chapter by chapter.

For the _experienced programmer_, this book teaches Ruby development and testing practice. Experienced programmers may want to skim the earlier chapters and jump in where they feel like they’re lacking something.

On a personal note, I should say that I hope this book will be accessible to _anyone_. As a self-taught software developer myself, I believe that anyone can learn essential programming concepts if they are taught correctly, and that everyone _should_ do so at at least a basic to intermediate level: in 2015, the ability to write simple programs is a life skill that everyone should have. It need not be mysterious, arcane, or intimidating in any way.

## How can we improve this book?

The source for this book is hosted on GitHub at https://github.com/marnen/ruby-test-first. If you’ve got an idea or suggestion, please raise an issue or send a pull request in that repository!

—Marnen E. Laibow-Koser, Somerville, Massachusetts, September 2015

[^1] My use of masculine pronouns is not meant to suggest that I think of programming as a male occupation. Quite the contrary: I believe that women and other non-male folks are sorely underrepresented in the software development community, and I’d like to see that change. Unfortunately, the English language lacks a good gender-neutral third-person singular pronoun, and the constant use of constructions like “he or she”, “s/he”, or “they” in a singular sense would make this book extremely awkward to read. I therefore reluctantly use “he” as a gender-neutral pronoun, but am open to suggestions as to how to deal with this issue in a more elegant way.

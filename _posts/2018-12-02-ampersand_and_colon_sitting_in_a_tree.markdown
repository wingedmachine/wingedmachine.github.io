---
layout: post
title:      "Ampersand and Colon sitting in a tree"
date:       2018-12-02 22:53:13 -0500
permalink:  ampersand_and_colon_sitting_in_a_tree
---

### T - O - underscore - P - R - O - C
I didn't have opportunity to use it during my most recent project, but I'm going to talk about a neat Ruby thing I learned about outside of class. The ampersand colon. As in:

> books.each(&:title)

Despite how it appears, the ampersand and colon aren't combining into a single operator here. They're doing two different side-by-side jobs that combine to get the desired effect. 

First, though, let's look again at that code example I listed above. In lessons to date, that same effect would always be achieved by writting:

> books.each { ```|```book```|``` book.title }

This is our starting point. The section in braces there is a "block," and a block can be wrapped in an object called a [Proc](https://ruby-doc.com/core/Proc.html), which gives us methods like #call. When an ampersand prefixes a Proc as the last parameter of a method call, the method threats that Proc as a block, so we can rewrite that previous line of code as:

> get_title = Proc.new { ```|```x```|``` x.title }
> books.each(&get_title)

This is where the colon comes in. It does what we've seen a colon do many, many times. It makes a [Symbol](https://ruby-doc.com/core/Symbol.html), and symbols all have #to_proc, which returns a Proc that performs the method with the same name as the symbol. So our previous code can instead be:

> get_title = :title.to_proc
> books.each(&get_title)

The last step is easy. If you put an ampersand before something that is not already a Proc, Ruby will automatically call #to_proc, so now we're back to the line of code I showed at the very beginning:

> books.each(&:title)

Magic!


*Sources:*
* [What Is the Difference Between a Block, a Proc, and a Lambda in Ruby?](https://awaxman11.github.io/blog/2013/08/05/what-is-the-difference-between-a-block/)
* [Stack Overflow: What does map(&:name) mean in Ruby?](https://stackoverflow.com/questions/1217088/what-does-mapname-mean-in-ruby)
* [What does to_proc method mean?](https://stackoverflow.com/questions/14881125/what-does-to-proc-method-mean)
* [Ruby & (Ampersand) Parameter Demystified](https://skorks.com/2013/04/ruby-ampersand-parameter-demystified/)

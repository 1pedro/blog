---
title: "First impressions on Clojure"
date: 2022-05-05T11:28:43-03:00
draft: false
author: "1pedro"
---


Has been 3 weeks that I'm learning Clojure. Here I will dedicate myself to putting posts about what I'm thinking of Clojure.  
Beforehand I wanna make clear that this series is by the vision of a person that has never worked with a functional language and has never heard about LISP or his dialects. Keep in mind that the languages that I feel comfortable with (not expert) are Javascript, PHP, and Python.
So, let's go!


## Learning resources (Occasionally change from time to time)
I think it's worth sharing where I'm getting information about Clojure, will it help anyone?

**Sites:**  
<a href="https://www.alura.com.br/formacao-clojure" target="_blank"> Alura Courses </a>  
<a href="https://clojuredocs.org/" target="_blank"> Clojuredocs </a>  
<a href="https://github.com/search?q=clojure" target="_blank"> Clojure repos </a>  
<a href="https://clojure.org/guides/getting_started" target="_blank"> Clojure official website </a>  

**Blogs:**  
<a href="https://vlaaad.github.io/" target="_blank"> vlaaad blog </a>

## REPL is good

Since I'm acquainted with other languages, I love the possibility to have a quick shell to clarify questions like:  
_Is it an empty python dict truthy?_  
_What happens if I try to access an empty property of a PHP array? it will throw? will return null?_  

Things like REPL is good to programmers because we don't need to memorize everything. And Clojure does this *very well*.
The Clojure REPL is simply and fast as it should be. I remember that I was very happy when I find out about the Clojure REPL.  

The only language that I feel uncomfortable with his REPL is Javascript.. You can say: "Oh we have node to act like a REPL"
But the node does not have a window element, and also not all functions that we use in a browser work in node. 
Have you tried to convert a string to base64 using `atob` function? does not work.

## Special Characters on symbols and functions names

What such a great idea! The way that we use the `?` to mark functions that return boolean is awesome. Much better than adding an `is` upfront every funciton name like other languages do. Have you ever saw `isNegative`, `isEmpty`, `isValid` functions? is that that I'm talking about.

Besides that, as convention we use the `!` to identify functions that have side effects and also make sense.

Clojure uses special characters with a bunch of different meanings. I really recommend that you visit <b> <a href="https://clojure.org/guides/weird_characters" target="_blank"> this page </a></b> to known more about special characters in Clojure.

## Too much 'def'

As I said has been 3 weeks and I keep seeing new "def" words. We start with the simple `def`, then the `defn`, and after two or three days of learning
you'll see: `defmacro` `deftest` `defprotocol` `defrecord` `defonce` `defmethod` `deftype` `defstruct`... and the list always gets bigger.

I think that by now I don't have the knowledge to understand what's going on with so much def. But the first impression is: it looks like Clojure has more data structure than any other programming language and each "def" means a different kind of structure.

## New Nomenclatures

I've never learned so many new words since I started programming..  
Here we use `symbols` not `variables`, we have `predicates`, `macros`, `protocols`.

A Predicate is a thing that I've already learned in the university. But never heard in a programming language.  
I feel a more complete programmer every time I understand what each new word means.


## Weird things (by now)

- Why we don't have a simple `queue` constructor? why do we have to use `clojure.lang.PersistentQueue/EMPTY` to generate an empty queue?
- Why the `every?` function has a `?` and the `some` does not have? why `some` does not returns a boolean too?
- Why do `pop` and `peek` work in a way when dealing with lists and queues, and total differently when dealing with vectors? Is it not easy to implement another method just for the vectors?
- Why I can use `pprint` in the `clj` but in the REPL of the IntelliJ I have to import it?


## Conclusion

That's it. Feel free to answer any of these questions. I'll be happy to learn from you.
In the next posts, I'll be here to share more thoughts about the Clojure and would be nice to see you here again.

Thanks.

– Pedro.
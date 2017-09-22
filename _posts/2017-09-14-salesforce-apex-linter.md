---
layout: default
title:  "Building a Salesforce Apex Linter"
date:   2017-09-14 19:35:00 +0200
categories: salesforce
---
# Building a Salesforce Apex Linter

## Why even bother? And where do I start?

I've decided to build a linter for Salesforce's Apex language. Why? I'm tired of reviewing and rejecting pull requests that don't adhere to style. It would also be nice if recommendations would come up while actually developing, so the feedback loop for new developers is shorter. 

Salesforce has always been, and still is, pretty limited in the Development Tools it offers. Basic stuff such as static code analysis or debugging is painful and expensive.

> “Clean code is not written by following a set of rules. You don’t become a software craftsman by learning a list of heuristics. Professionalism and craftsmanship come from values that drive disciplines.” 
>
> &mdash; <cite>Robert C. Martin, Clean Code</cite>

Developing and maintaining enterprise applications that are inconsistent in (for example) indentation or naming conventions is frustrating. Call it OCD, but I'd really like to get rid of it. 

Looking at the pool of open source linters that is available, I'm sure one of them will lend themselves to forking and adapting to Apex. There's [a list published](https://github.com/showcases/clean-code-linters) that I'll explore the code of and see how achievable this is. Right now I only have experience in C#, JavaScript and Apex, but learning a language is probably worth my time.

## Getting Started

> The basic steps an ESLint-style linter needs to do first:
> 1. Parse code into an abstract syntax tree (AST)
> 1. Prepare auxiliary information needed by rules
> 1. Traverse the AST and emit events for each node entered and left
> 1. Rules listen for node events and emit lint messages
> 1. Iterate through lint messages and attempt to apply fixes
> 1. Output results, including "fixed" file
<cite>Extracted from [this ESLint issue](https://github.com/eslint/eslint/issues/7907)</cite>

[PMD](https://github.com/pmd/pmd/tree/master/pmd-apex/src/main/java/net/sourceforge/pmd/lang/apex) has built an AST and parser I can use. Actually, come to think about it, can't I just extend the ruleset for PMD to check for style?

## PMD and Apex-Jorje

Ok so PMD didn't actually build their own parser, but piggybacked the `Apex-Jorje` library that comes with the Force.com IDE. It has some important limitations that will prevent me from using it for this purpose:

1. It ignores whitespace
1. It ignores comments
1. It has no documentation and can not be extended, since it's not open sourced by SFDC

The first 2 are pretty much blockers, they prevent me from writing any rule that considers indentation or whitespacing. It's essential.

Although I did like the PMD community and felt that there was a need to extend the library for the purposes it was built: static code analysis. I'm going to contribute the next couple of weeks a chunk of my time in building the rules I feel they miss and are achievable with this AST.

### To be continued...

<a href="/">Return to the overview</a>.

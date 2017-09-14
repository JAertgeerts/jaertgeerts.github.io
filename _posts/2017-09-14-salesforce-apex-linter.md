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

> The basic steps an ESLint-style linter needs to do first:
> 1. Parse code into an abstract syntax tree (AST)
> 1. Prepare auxiliary information needed by rules
> 1. Traverse the AST and emit events for each node entered and left
> 1. Rules listen for node events and emit lint messages
> 1. Iterate through lint messages and attempt to apply fixes
> 1. Output results, including "fixed" file
<cite>Extracted from [this ESLint issue](https://github.com/eslint/eslint/issues/7907)</cite>

[Fundación Jala](https://github.com/fundacionjala/enforce-sonarqube-plugin) has built a basic version of an AST I can use.

### To be continued...

<a href="/">Return to the overview</a>.
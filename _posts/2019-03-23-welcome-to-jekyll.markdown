---
layout: post
title:  "Creating an index object"
date:   2019-03-23 21:03:36 +0530
categories: c++
---
Let us first look at a minimal example. We will look at how one can create a simple index and what happens
in the background. Looking at the itensor web page in the first example in the book [itensor-bookindex][itensor-bookindex]
we saw the following:
```cpp
auto i = Index(3);
```
That code generates an index object. In order to understand what happens, letus first go to the **index.h**. We see that **Index** is a class and we can easily find the relevant constructer.
```cpp
Index(long dim, TagSet const& ts=TagSet("0));
```
[itensor-bookindex]: https://www.itensor.org/docs.cgi?vers=cppv3&page=book/index

Now let us go to **index.cc** where the constructer is defined.  We find
```cpp
Index(long dim, TagSet const& t):
id_(generateID()), dim_(m), tags_(t) {
if(primeLevel()<0) setPrime(0);};
```
Let us take apart this constructer,

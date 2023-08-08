---
title: Introduction To Decompilation, Part 1 - What's this all about?
output:
  md_document:
    variant: gfm+footnotes
    preserve_yaml: TRUE
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, encoding = encoding, output_dir = "../_posts") })
date: 2023-08-08
permalink: /posts/first
excerpt_separator: <!--more-->
always_allow_html: true
toc: true
header:
 og_image: "posts/nest-map/fig-1.png"
tags:
  - tag
---

Why would I care about this?
<!--more-->

So... Hey!
I bet you're looking at this and saying, why should I care? 
whats so interesting about decompilation anyways..?
whats even the point of these blogs

# About this blog
let me give you a quick intro, ok? <br>
these blogs will go through decompilation in a less.. academic way, <br>
I would like to save you the unnecessary details and explain the mathematics only when absolutely needed, <br>
and mostly as a way to give you some intuition about whats going on. <br>
You might have tried to study this subject but have been offput by the academic way of approaching this subject, <br>
I had to go through all that, and although its really interesting, you probably dont want to look at equations and weird math stuff all day. <br>
I want to give you the MEAT of the subject. <br>

# What is decompilation?

ok, im gonna do the necessary bidding and explain what even IS decompilation and why YOU should care about it. <br>

Some of you might see the compiled form of an original program as final, the story ends here, all thats left is to execute. <br>
Unless you do reverse-engineering work, you dont seem to care about what the final representation means, and why should you, honsetly.. <br>
well, if this program you execute happens to be malware, then.. you might wanna know whats up. <br>
Decompilation is very important for malware analysis, since you wanna know how the virus works to prevent it. <br>
It's also very useful for other reverse engineering tasks. <br>
What one might miss is that the subject of decompilation isn't about the compiled form or even the original form, its simply a quest to shift between different
representations of the same data, no magic here. <br>

Go, C, Rust, C++ for example, are all compiled to the same form, the specfic decompiler you might use is just a tool to shift the representation of assembly to a more 
readable C/Go/Rust/C++ code. <br>
It tries to fit the compiled form to the correct shape, tries to understand what original code caused that. <br>

For example: <br>
Say im decompiling a while loop, the syntax to make a while loop can be different between languages, so the decompiler tries to make it to the correct original form of the program, if its syntax or features. <br>
many features can cause the same compiled form code, so its up to the decompiler implementation to think when what fits (for example a for loop is just syntatic sugar of a while loop). <br>


So because this idea that decompilation is only about the compiled form and original form, it makes sense that bytecode is easier to decompile, since the representation is more high level, and its easier to decompile the compiled form of C code as opposed to C++ code. <br>



Your intuition might say that decompilation is impossible, well you're kinda correct. <br>

PERFECT decompilation is impossible in alot of cases, again, depends on what youre getting. <br>


# Whats decompilation all about

The first idea I presented about what decompilation might be about is the compiled and original form. <br>

The second idea, and the most important one, is that decompilation is just about representations of data and shifting between them. <br>

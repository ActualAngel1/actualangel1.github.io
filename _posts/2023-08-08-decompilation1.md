---
title: Introduction To Decompilation, Part 1 - What's this all about?
output:
  md_document:
    variant: gfm+footnotes
    preserve_yaml: TRUE
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, encoding = encoding, output_dir = "../_posts") })
date: 2023-06-10
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

let me give you a quick intro, ok?
these blogs will go through decompilation in a less.. academic way, 
I would like to save you the details and explain the mathematics only when absolutly needed, 
and mostly as a way to give you some intuition about whats going on.
You might have tried to study this subject but have been offput by the academic way of approaching this subject,
I had to go through all that, and although its really interesting, you probably dont want to look at equations and weird math stuff all day.
I want to give you the MEAT of the subject.

ok, im gonna do the necessary bidding and explain what even IS decompilation and why YOU should care about it.

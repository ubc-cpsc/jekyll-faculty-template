---
layout: default
---

## Quickstart Guide

Click [here](https://bitbucket.org/UBCCS/jekyll-faculty/src/master/) to return to the 
repository website that shows instructions on how to use
and customize this UBC CS faculty and course static website generator yourself.  Browse
the markdown files in particular (```.md``` file extension; start with ```index.md```).

Browse the remainder of this demonstration website to gain a sense of what can
be easily and efficiently generated and maintained (like $x^2 + 1 = 17$, ```while(true) ++i```, and the references below).

---------------
## About Me

<img class="profile-picture" src="headshot.jpg">

I am an associate professor of computer science at the University of British Columbia.


## Research Interests

My primary research areas are probabilistic programming and applied statistical
machine learning. My research interests range from the development of new
probabilistic models and inference algorithms to real-world applications. My
research contributions include probabilistic programming systems, new models and
inference algorithms, and novel applications of such models to problems in
neuroscience, natural language processing, robotics, and compression.

## Selected Publications

{% bibliography --file selected.bib %}

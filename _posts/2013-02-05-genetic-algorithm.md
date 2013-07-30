---
layout: project
categories: [projects]
description: A graphical multithreaded control system optimization tool that uses genetic algorithms to tune the system parameters. The genetic algorithm has the novel modification of using symbolic rather than binary genes.
image: ga.jpg
tags: [programming, multithreaded]
---

This was another component of my B.Eng work. The [Genetic Algorithm](http://en.wikipedia.org/wiki/Genetic_algorithm) was novel in that it used continuous rather than discrete symbolic genes in the genome. This require modifying mutation and crossover to handle the the types of codons. The genes themselves were [double precisions IEEE floating point](http://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html) numbers. Mutation was changed to provide an addition of a normally distributed random number with a mean of 0. This gave a fairly high chance of a small mutation but it was still possible for large changes to occur.

The genetic algorithm itself was used to control parameters for the [Magentic Levitation Simulator]({% post_url 2013-02-05-magnetic-levitation-simulator %}). This was wrapped into a graphical Windows application based on two main threads. The main thread was used for re-drawing the GUI to the screen to keep the user informed of the progress of the GA. The secondary thread ran that GA itself.

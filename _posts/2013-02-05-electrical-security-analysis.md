---
layout: project
categories: [projects]
description: A set of tools to analyse the security of supply for an electrical power system. Developed for my Ph.D. it is based around a Monte Carlo Sampler and interfaces with CPF in Matlab for the simulations.
image: laos.jpg
tags: [programming, matlab, PhD]
---

**This is available online at <https://github.com/kerspoon/kiribati>.**

This is a tool for comparing security assessment schemes for electrical power systems. It currently looks only at a simple N-1 (*#6*). It only work in Linux and is based around the load flow simulator from PSSENG at the University of Bath. To use it run (it will take many days to complete):

    ./run 100 100000

## About

`./run` does everything you need to. It takes two args the number of base cases and the number of different contingencies (*#7*) to consider. It then generates the base cases through Monte Carlo sampling of the outage probability of components, the correlated failure rates of certain components (e.g line with a common right of way) and by picking a random hour of the year it gives a load level as a percentage of the winter peak.

This represents a number of likely scenarios that the system operator might expect to see the system in (*#1*). A handful of components are on outage either planned or being repaired and the power level is determined in part by the time of year and time of day. From each base case we want to estimate the probability that emergency operator action will need to be taken to give an estimate of how secure the system is in it's current state. We do this through another round of Monte Carlo. This round of Monte Carlo uses the probability that the components will fail in one hour it also considers the probability that the load will differ from the predicted value over the given period.

These are then simulated (*#3*) and catagorised into acceptable or unacceptable. The unacceptable ones are the ones that do not load flow, or the load flow results in limit violations (*#2*). Islanded systems should probably consider the size of the island and say systems are acceptable if the biggest island is over 80% of the load. This will mean that is we happen to island a generator and a few small remote houses we would consider it acceptable. This is debatable and the current implementation requires that there is no islanded caused by outages. To save on simulation time we quantize the possible load levels. We then take samples that are the same and group them together only simulating them once. (*#4*)

One we have a good representation (*#5*) of the state of the system we can find the probability that a given base case will become unacceptable in a 1 hour period. This is simply done by the number of unacceptable contingencies divided by the total number. From all this we end up with a set of bases cases and their probability of acceptability. This allows us to compare two security assessment schemes. If we apply both SAS to the base cases we will find the assessment of whether they are acceptable or not according to the given SAS. In the ideal world this would exactly match the real probability of acceptability. By comparing the SAS output to our estimated probability of acceptability we can find how well that SAS matches what we want.

## Footnotes

- (*#1*) The real system will be optimised for price and for stability. As further work it would make sense to secure some of the systems here to give us a wider range of probability of acceptabilities in the final results. It wouldn't make sense to secure all of them using the same scheme (e.g. SCOPF with N-1) as this would make it impossible to compare N-1 to anything else.
- (*#2*) This is another great simplification from reality. Systems are not catagorised as acceptable or not but for this to work in an automated system this is required.
- (*#3*) In the ideal world we would use something more accurate than a load flow to simulate the system. Especially as we are looking at the effects of component failures.
- (*#4*) Although it has not been done it would be trivial to parallelize the computation. Each simulation is entirely independent of the others and it's inputs and outputs are very small.
- (*#5*) The easiest way to tell if we are reached a stopping point that has enough samples is to see if increasing the sample size causes a change in the output probability. If it doesn't significantly then we have enough.
- (*#6*) It should be fairly easy to add other SAS to this program. Even if they are not automatically computable (i.e. human interaction is needed) then it can be done by hand and the findings added to the results of the automatic part of this program.
- (*#7*) Rather than input the number of contingencies you input the number of simulations. This are different because often samples are the same. This means the program should run in the same amount of time if the inputs are the same.




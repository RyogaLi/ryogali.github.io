---
layout: post
title:  "what are we talking about when we talk about Monte-Carlo simulation"
tags: [Coding, Bioinformatics, Algorithms]
---

>Monte Carlo simulation performs risk analysis by building models of possible results by 
substituting a range of values—a probability distribution—for any factor that has inherent 
uncertainty. It then calculates results over and over, each time using a different set of 
random values from the probability functions. 

**The pattern of Monte-Carlo Simulation**

1. Define a domain of possible inputs 
2. Generate input randomly from a probability distribution over the domain
3. Perform a deterministic computation on the inputs
4. Aggregate the results

---

#### Example 1:  traffic modeling ####

**Nagel-Schreckenberg model:** In this model the roadway is
divided up into $$M$$ distinct zones, each of which can hold one vehicle. There
are $$N$$ vehicles in the road. Time moves forward in discrete steps. A vehicle
with velocity $$v$$ moves ahead by $$v$$ zones in the roadway at the next time step.
There is a maximum speed $$v_{max}$$ which all vehicles obey. In the simplest case,
the roadway is a circular loop.

Let $$ x \in \{ 0, 1, . . . , M − 1 \} $$ be the position of a car, $$v$$ its velocity, and $$d$$ be
the distance to the car ahead. The update for this car is:

$$v \gets min(v + 1, v_{max})$$

$$v \gets min(v, d − 1)$$

$$v \gets max(0, v − 1)$$ with probability $$p$$

$$x \gets x + v$$
+++
title = "A Brief Introduction to Time in Physics"
hascode = true
tags = ["A Brief Introduction to Time in Physics", "time","physics"]
+++


In preparation for the next (now defunct) [Olympia Academy](https://twitter.com/TheOlympiAcad) event via [The Interintellect](Link), entitled [Running Out of Time: The Temporal Dimension](https://www.eventbrite.co.uk/e/running-out-of-time-the-temporal-dimension-interintellect-salon-tickets-126725374005), I thought it might be useful to give a brief rundown on some of the ways we work with time in Physics.

### Event Abstract

> "Of all obstacles to a thoroughly penetrating account of existence, none looms up more dismayingly than “time.” Explain time? Not without explaining existence. Explain existence? Not without explaining time. To uncover the deep and hidden connection between time and existence, to close on itself our quartet of questions, is a task for the future." - John Archibald Wheeler

> "I would like to invite you to take a momentary pause (alas, we cannot even consider time without invoking it!), and ask yourself, what can you factually say about the phenomena of time? If you are like me, you find that nothing satisfactory comes to mind, and this puts you, luckily, in the company of the greatest minds that have ever lived- however that is not to say they didn't have ideas about the nature of it. Newton claimed time to be absolute, to which Einstein retorted, "relativity", Weinberg suspects that it, among other things, exists below reality as a rule, bubbling up through the quantum, into the macro, and Wheeler, considered that it seems imposed upon us "from above", though not able to say what this above would constitute. What is time? Better yet- is time? Is it discrete or continuous? Does it result from the awareness of the changing external world, or perceived changes in internal states? How did time begin? How will it end? What would answers to any of these questions mean for humanity? So, I again, would like to invite you on an exploration of the weirdness, the strangeness, and wonder, of this thing we call time." - Salon Host, Lorenzo Evans

#### Selected (optional) Pre-Readings
- [Haunted by His Brother, He Revolutionized Physics](http://nautil.us/issue/9/time/haunted-by-his-brother-he-revolutionized-physics)
- [A history of time: Classical time](https://mathshistory.st-andrews.ac.uk/HistTopics/Time_1)
- [A history of time: 20th century time](https://mathshistory.st-andrews.ac.uk/HistTopics/Time_2/)
- [Does Time Really Flow? New Clues Come From a Century-Old Approach to Math](https://www.quantamagazine.org/does-time-really-flow-new-clues-come-from-a-century-old-approach-to-math-20200407/)
[Is time quantized?](https://www.scientificamerican.com/article/is-time-quantized-in-othe/)
[Stanford Encyclopedia of Philosophy: Time](https://plato.stanford.edu/entries/time/)


I think one of the key issues with solving the mystery of time, is that we don't have very much going for us in the way of classifying it as a phenomenon: we talk about time relative to other things, in the same way that we only visualize 2D space, *as embedded in 3D space*- not the thing itself, but a reconstruction -however it is nonetheless the starting point that we have, and we've done wonderful things with it as a species, so it merits some observation I think, for what it has done, regardless of what it hasn't.

**So what *does* Physics have to say?**

Starting at Classical Mechanics: we index time to the Natural numbers, if we need to treat time as something discrete, or the Real numbers if we need to treat time as something continuous (generally using the latter as it more accurately represents our intuitions about time). Beyond that, there's not a large amount of development of the concept of time, as it is mostly a guidepost, for the path of objects and processes through space. Time is not where the action is, and thus it's a bit of a background player: time limits, stalls, progresses, or reverses the action.

For example, if we had some particle $P$, we could say $P$ is a **vector** (meaning it has magnitude, and direction), and we would talk about this particle via these components, and its location, according to the three spatial dimensions, and the one temporal dimension. 


In short, we can can say $P = (x, y, z, t)$, and that $(x, y, z, t)$ constitute a __reference frame__, or a moment in space & time, if you will.

Given the values of $x, y, z$ and $t$, as well as the magnitude (length), and direction (the measure of the angle between the particle and the positive side of the x-axis, usually marked by the lowercase Greek letter theta (/theta)), we can then comfortably analyze the evolution of $P$ as $t$ changes.

We can inquire about $t + 1$, $t + 100000$, $t +t^{t / 2}$, **and**, $t - 3$, $t - 30000$, effectively, we have access to $t \pm n$, with the caveat that $0 < t < \infty $. 

If we're treating time as something __discrete__, we index $t$ to the Natural numbers, which *begin* at $0$, and technically have an end at $\infty$, but this of course is also never reached (which is partially why singularities, i.e black holes, present a bit of a problem, with the problem being the physical theory allows for the manifestation of something that contains a mathematical/numerical impossibility as its premier property).

If we're treating time as something __continuous__, and we index $t$ to the Real numbers, then we are forced apply the concept of limits, from calculus, to the value of time, meaning it will get arbitrarily close to, but never quite reach the lower bound of $0$, or the upper bound of $\infty$.
    
I should also note that the uppercase Greek symbol delta, $\Delta$, is usually what is used here, in that delta denotes a change in some variable, in this case $t$, written $\Delta t$, but it's technically the difference in the value of $t$, given two different reference frames. 

If we take some function of time, $f(t)$, in our case the location of a particle which we know is $(x,y,z)$, the change in location over some interval is given by $\Delta f = f(t + \Delta t) - f(t)$, and the changes in the values of the spatial coordinates, are given by, $x(t + \Delta t), y(t + \Delta t), z(t + \Delta t)$. 

From here, if we zoom in on Classical Mechanics a bit, we will inevitably encounter General Relativity, Einstein's theory that gravity, is the result of mass causing space to curve. A side effect, of this is that gravity and time become linked, due to the fact that the curvature of space increases the distance that light must travel between any two points. The result of this is that __the amount of space that light can travel over any span of time becomes smaller__ as the curvature of space increases, which is why light can't escape Black Holes, and an observer watching some object fall into one, will never actually see the object "finish falling".

**In short, as a result of General Relativity, within Classical Mechanics, we understand that time, is non-absolute, malleable, and of course __relative__- but none of this cancels out the __deterministic__ and __reversible__ properties of time. For all intents and purposes, this would be fine, as General Relativity is one of the two most robust descriptions of the fundamental nature of the reality we inhabit- the issue is that the __other__ most robust description of the fundamental nature of reality, disagrees intensely with this.**

**That description, of course, is Quantum Mechanics**.

At the quantum level, there are events that *distinguish* the past from the future, such as the collapse of the wave function, which makes the past and future around a measurement asymmetrical, and thus represent an irreversible change (or rather, a change that removes the reversibility of the system being observed).

Also, because QM is probabilistic, there are natural side effects that seem to make time operate, or behave at least somewhat __probabilistically__, as opposed to the deterministic nature of time in classical systems: If we have a particle that is in a number of states simultaneously, we can't exactly speak about the temporal nature of any of these states relative to a particle, because we can't say __when__ any given state is inhabited by the particle, or vice versa: __when__ the particle is in any of these states.

What this does is set up conflict, between the perspectives on time given by our two most effective descriptions of reality:
**Classical Mechanics requires that things be deterministic, and reversible:**
- By deterministic, what we mean is that there are a set of logical rules that allow you to derive the state of the future, given its current state.
- By reversible, we mean that given the state of the system at some point in the future we should be able to derive the state of the system at some point in the past.

 **Quantum Mechanics requires that things be probabilistic, and irreversible:**
            
The collapse of the wave function is an event that sharply distinguishes the future from the past, due to the marked difference in the state of the system on either side of the event.

This is not deterministic, because prior to the collapse of the wave function, we can't say where the particle is, and it's not reversible, because, given a particle with a definite location, we can't say where it was prior to the measurement.
As of yet, this problem is intractable- to solve it would require us to do intense theoretical surgery on one or both of these tools, to make them play nicely, or an entirely new theory, that provides a set of rules from which both "mechanical theories" can be derived, as well as their behaviors and the appearance of incompatibility that results from them.
            
This isn't meant to imply that time does not exist in the realm of the quantum, just that time cannot be treated the same way __there__, as it can in the realm of the classical: it is evoked as an external concept, sometimes referred to as __quasi-classical time__, and assumed to govern all motion, as with classical mechanics, and the path of a particle through __time__, will be associated with the __world line__ of the particle- it's path through 4D space-time.

Of course, while there's certainly more to be said about time in Physics, via light-cones, thermodynamics, entropy, and world lines, I think the intro we've done so far meets our requirements. In short, Physics, while having fought valiantly to generate understanding of, uses for, and applications of time, in its theories and tools, for itself and society, does not quite know what to do with/about the mystery of time.

**Yet**.
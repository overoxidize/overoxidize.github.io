+++
title = "Thread & Thrum"
tags = ["Rust", "C"]
+++

\toc

## I. Introduction

### Unwrapping Threads:
    
Threads are rudimentary elements of both programs, and CPU's (Central Processing Units),  in that they are harnessed *by CPU's*, via the *needs of programs*, to handle work that can be completed more efficiently if executed on the multiple cores that are available on modern computational devices. Computers *technically* only do one thing at a time, i.e  in a single threaded manner, but due to the speed at which they complete and switch tasks, the illusion of true multi-tasking has been almost un-abatedly present. That being said, as the looming limits of hardware, particularly that of computer chips, interweave with the increasing demands of software, multi-threaded, concurrent programming has become ever more prevalent, allowing for multi-tasking to become something much more substantial than an illusion.

- Typically, threads are comprised of a program counter, a stack, a set of registers, and a thread ID, and can be considered a virtual representation of a core, that allows for the efficient and timely management and completion of tasks. Threads are created in response to the requests of users, or services, and are usually sub-elements of processes, which, broadly speaking, represent any program that is being executed on a given computer.

### Weaving Threads In Code:

As stated before, computers typically execute tasks in a sequential manner, attempting to complete one task at a time, and moving on to the next available task upon completion: this limitation however, is circumnavigated by the advent of multi-core processing. A thread can be used to virtually imitate a portion of the capabilities of a core, however there is still only one core available, to do the work, which is managed by the threads (which are in turn managed by a scheduler, which executes threads according to order, priority, state, and potentially a number of other factors such as OS/device type). Multi-threading, builds upon the advantage of virtually portioning the CPU core, due to having more cores available.


### Rust On A Wire

Rust, while starting out as a systems programming language, has evolved, or rather, grown, into a general purpose programming language, largely due to both, the desire of programmers to have the advantages of the language present in other types of software, and the fact that these advantages lend themselves well to some of the challenges faced in other programming contexts.
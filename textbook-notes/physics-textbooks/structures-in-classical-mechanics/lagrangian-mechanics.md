+++
title = "Lagrangian Mechanics"
tags = ["physics", "classical mechanics"]
+++

**1. Lagrangian Mechanics**
Classical Mechanics describes the motion of systems under the influence of forces. Complex physical objects can be expressed as an arrangement of particles, with the static spatial relationships between them being due to stiff interaction forces.
There are a large number of ways a system could move, which never occur, or are not realizable, So the question becomes: __Can we create a mathematical function that will help us make the distinction between realizable motions and conceivable ones?__

The description of the motion of some system, can be built by giving the position of every component of the system, at each point in time.
This is called a configuration path, which is a function of time.
The function we desire consumes a configuration path, and generates some output, and this output should have some specific characteristics, **__if the input configuration path is in fact, realizable__**.

Another option, is that we can look for a function that distinguishes one class of path from the other, with a minimum value for all realizable paths, one where the value for nonrealizable paths is much higher.
This is the variational mechanical technique, which generates a path distinguishing function for some physical system, by producing a stationary point for al realizable paths.

The variational formulation describes successfully all of the Newtonian mechanics of a large number of systems.

The **stationary point** of some function is the point where the value of the function does not vary as the input does.
Newtonian Mechanics presents the motion of systems as comprised of the positions, velocities, and accelerations, of each component of the system.

The variational perspective describes the system in terms of **aggregate** properties of the system, such as the total energy.
The Newtonian perspective allows for forces to be described as derivatives of the energy potentials of the system.

The variational perspective presents the equations of motion (the dynamical laws governing the evolution of some physical system), in terms of the difference in kinetic and potential energy.
The potential energy is a number representing the arrangement of components of a system, whereas the kinetic energy represents the __velocities__ of said components.

Within the variational perspective, the equations of motion are independent parameters derived from a given [coordinate system](Cartesian Coordinate System).
Within this method, we aren't required to consider the forces maintaining the positional constraints because they can be baked into the coordinate system.

**1.1 The Principle of Stationary Action**

For a path distinguishing function, which is stationary on all realizable paths, we can deduce some necessary properties of the function, based on classical intuition.

Day to day experience indicates that configuration paths describing physical motion are smooth/continuous, as well as that a physical systems motion may not be dependent on the entire history of the systems.

It also suggests that the Motion of physical systems are deterministic, meaning that a small number of parameters contain the importance parts of the history of the system, such that you can predict the future of the system.

**Realizable Paths**

If the configuration path describing the motion of some system is realizable, then every segment of the path must __itself__ be realizable. 

Furthermore, the realizability of a segment is dependent upon the realizability of each point in the segment. **__The realizability of a given path segment is a local property__**.
**This means a function capable of distinguishing paths must aggregate a local property of the system, measured at each moment (__point in time__) along the segment.**

For a given segment, the combination of its contributions must **__preserve the independence of contributions from non-adjacent segments__**. Put simply, this requires a function that distinguishes paths to be an integral function over the path segment of some local property of the path.

The path distinguishing function aggregates local properties of the system measured at each moment along the related path segment

We can build this integral path function of a local property to assume extreme values on realizable paths. **By convention, this type of function is referred to as the action for the system**.

By pursuing the variational mechanical method, we can create action functions which are stationary on realizable trajectories of the motion of systems.
Considering actions as integrals of local properties of configuration paths at each moment, we present $\gamma,$ as the configuration path function, and $\gamma(t)$ as the configuration at some point in time.

The action of the path segment of path $\gamma$ in the interval between $t_1\; and\; t_2$ is:
- $\Large S[\gamma](t_1, t_2) = \int_{t_1}^{t_2} F[\gamma]$.
$\Large F[\gamma]$ is a function of time, measuring some local property of the path, and may be dependent on $\Large \gamma$'s value, as well as the value of the derivatives. The path can be locally represented in terms of configuration, rate of change of configuration, and higher derivatives of the configuration at some point in time.

Given this information, reconstruction of the path at some time interval becomes possible. The function $F$ measures some local aspect of the path $\gamma$.
We can decompose $F$ into two parts: One part handles measuring the property of a local description, and the other part extracts a local description of the path from the associated function. The function that measures the local property of a system depends on the system, but the method for constructing a local description of a path is invariant across physical systems.

$F[\gamma] = \mathcal{L} \circ \mathcal{T}[\gamma] $.

The function $\mathcal{T}$ consumes the path and yields a function of time, with its value being an ordered tuple comprised of the time interval, the configuration of the system at that interval, the rate of change of configuration, and the values of higher derivatives of the path at that interval:

$\mathcal{T}[\gamma] (t)= (t, \gamma(t), \mathcal{D}\gamma)(t) \ldots)$, referred to as the __local tuple__.

The derivative of $\gamma$, $\mathcal{D}\gamma$, can be defined in terms of ordinary derivatives, by outlining how it behaves on smooth, real valued functions.
The function $\mathcal{L}$ is dependent upon the specific details of the physical system, but isn't dependent on a particular configuration path, and computes a real valued local property of the path, with a finite number of of elements, which indicates that it measures a local property.

The advantage of this is that the local description of the path is generated by a uniform process, from the configuration path, without regard to the system being analyzed.

The function $\mathcal{L}$ contains all of the system specific information, and is called a __Lagrangian__ for the system, and the resulting action, is called the __Lagrangian action__:
$\mathcal{S}[\gamma]\big(t_1,t_2\big) = \int_{t_1}^{t_2}\mathcal{L} \circ \mathcal{T}[\gamma]$.

The Lagrangian is key in Dirac and Feynman's path-integral formulation of Quantum Mechanics, where the classical action can be used to derive the relative probability amplitude for a path.

Additionally, an initial segment of a local tuple is enough to determine the future evolution of a system.

For a large number of systems, Lagrangians exist as the difference between the potential and kinetic energy of a system.

A realizable path for a system is distinguished from others by the stationary point, however, there will be realizable paths near the desired one.
This means when considering whether or not the Lagrangian action of some system is stationary, with regards to the varying of path realizability, and the associated paths, we must restrict the set of realizable paths somehow.

For Lagrangians that depend solely upon configuration and its rate of change, we can restrict the set of paths to those that begin and end with the same configuration.
The stationary action principle tells us that for a given dynamical system, a Lagrangian can be built such that a realizable path connection configurations at two times is distinguished by $\mathcal{S}[\gamma]\big(t_1,t_2\big)$ being stationary.

**1.2 Configuration Spaces**

We consider mechanical systems, that can be visualized as being comprised of point particles, with no internal structure.
Bodies with extension can be considered as composed of a number of these point particles, with specific spatial relationships. It is the outlining of the position of these particles that constitutes a configuration.
The presence of constraints between parts of a system, such as those which define the shape of a body, means constituent components of the system cannot assume all positions.

This relates to the concept of a Physical Object, in that the parts of a system which define the shape of a body can be considered to also be defining the boundary of the body, the matter within which is __constrained__ to moving as one object, and because that matter is constrained, there are __positions it cannot assume__.

The set of all acceptable configurations of a system are its configuration space. A configuration space has a dimension equal to the smallest number of parameters needed to specify a configuration, and the dimension also refers to the number of degrees of freedom within the system.

For a single particle, three parameters are needed to define a configuration, so if there are $k$ particles, then we need $3k$ parameters.
Constraints among components tend to lower the dimensionality of the configuration space.
Technically, a configuration spaces dimensionality and degrees of freedom are not the same: the degrees of freedom are the __locally accessible__ dimensions of the configuration space.

Systems containing non-integrable constraints, the dimension of the configuration space may be larger than the number of degrees of freedom, however, if all of the constraints are integrable, the system is [holonomic](Holonomic Systems).
As a system evolves over time, the components of the system evolve according to the constraints. Each particle is defined by the changing configuration, meaning the systems motion can be represented as traversing a path in configuration space.

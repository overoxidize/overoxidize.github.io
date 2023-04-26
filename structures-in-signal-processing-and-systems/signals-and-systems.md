+++
title = "Signals And Systems"
tags = ["dsp"]
+++

# Signals and Systems

## Signals convey information. Systems transform signals.

Understanding of these will be developed by exploring their structure (__syntax__), and their interpretation (__semantics__).
The relationship between the input and output is a declarative description of the system, while the process for transforming signals into outputs is an imperative description of the system.
We'll model signals and systems mathematically, as functions.
A signal maps a domain, such as time, or space, or light intensity, onto a __range__.
A system works similarly, mapping signals from its domain onto output signals.
The domain and range are both sets of signals, or **__signal spaces__**.

## Signals.
Signals often carry information, as temporal or spatial patterns, which can be embodied in many different types of media.

## Audio signals.
Sound can be represented as a function, $Sound:Time\; -> Pressure$, where $Pressure$ is the set of all possible air pressures, and $Time$ is a set expressing the duration of the signal.

One second of a voice signal, can be described $Voice:[0,1]\; -> Pressure$, and is often visualized as a waveform, which can be plotted as a function. 
Because computers cannot handle the full range of numbers implied by $[0,1]$, or the seemingly continuous nature of a waveform, what happens instead is that, roughly 8000 numbers (perhaps members of $Bin*$), per second are sampled into what is known as a discrete time signal, as they are defined only at discrete points in time.

A discrete, one second computer signal, can be thought of as a function that maps discrete time to 16bit integers: $ComputerVoice:DiscreteTime -> Ints16$.
- Their continuous counterparts work as you'd expect.

Hardware handles the task of turning the $ComputerVoice$ function into a $Sound$ function:

$HW: ((CompVoice:DiscTime -> Ints16) -> (Voice:[0,1] -> P))$.

The sound of an ideal 440Hz tone over an infinite $Real$ valued time-interval, can be modeled as $PureTone: Reals -> Reals$, where the function for converting time to pressure is $\forall t \in\; Reals,\; PureTone(t) = Psin(2 \pi \times 440t)$.

## Images.

Grayscale images are represented by the function:

$Image: [0, 11] -> [0, B_{max}]$.

More generally:

$Image: VerticalSpace \times HorizontalSpace -> Intensity$, where $Intensity$ $ = [black, white]$, is the intensity range measured in some scale.

Color pictures, are sometimes measured in terms of RGB values, and so a color picture is represented by the function:

$ColorImage: VerticalSpace \times HorizontalSpace -> Intensity$, with the values assigned by the function at any point 
$(x,y)$ is given by the triple $(r, g, b) \in Intensity$: $(r, g,b ) = ColorImage(x, y)$.
Depending on the image, the spatial domain may be different, and different ranges of intensity, and the way color is assigned to points in the domain. For instance, a computer represents color images using colormap tables:

$Display: ColorMapIndexes -> Intensity$: $(r, g, b) = Display(x, y)$.

Since computers are finite, storing images requires discretizing domains and ranges, so that your computer may operate like so:

$ComputerImage: DiscreteVSpace \times DiscreteHSpace -> Ints8$, where:
    $DiscreteVSpace = \{1, 2, \ldots, 300\}$.
    $DiscreteHSpace = \{1, 2, \ldots, 300\}$.
    $Ints8 = \{0, 1, \ldots, 255\}$.

$ComputerImage$ can be said to store $200 \times 300$ pixels, with a pixel being a picture element, the value of which is $ComputerImage(row, column) \in Ints8$, where $row \in DiscreteVerticalSpace,\;and \;column\; \in DiscreteHorizontalSpace$.

A way that computers store images, represented by a function, is:

$ColorComputerImage: DiscreteVSpace \times DiscreteHSpace -> Ints8$


## Video Signals

A video, is a sequence of images, with a display rate, typically frames per second, is a signal, the domain of which is discrete time, and can be represented as $FrameTimes = \{0, 1/30, 2/30, \ldots \}$, and the range of which is an $ImageSet$.

$Video: FrameTimes -> ImageSet$.

For analog videos:

$VideoFrame: DiscreteVSpace \times DiscreteHSpace -> Intensity$.

For any time $t \in FrameTimes$, the image $Video(t) \in ImageSet$, or, alternatively, we can say: 

$AltVideo: FrameTimes \times DiscreteVSpace \times DiscreteHSpace -> Intensity$

- $(r,g,b) = AltVideo(t,x,y)$

If these videos represent the same video, then $\forall t \in FrameTimes$, and also $\forall (x, y) \in DiscreteVSpace \times DiscreteHSpace$:

$(Video(t))(x,y) = AltVideo(t,x,y)$.


## Signals Representing Physical Attributes

Changes in the attributes of physical objects are represented as functions of time and or space:

The position of an airplane: $Position: Time -> Reals^{3}$, where $\forall t \in Time$, where $PositionVelocity(t) = (x(t), y(t), z(t),v_x(t), v_y(t), v_z(t))$ gives the position and velocity at $t \in Time$.

On the other hand, a pendulum is represented by:

$\theta : Time \rightarrow [-\pi, \pi]$, where $\theta (t)$ is the angle at time $t$.

Or perhaps, a robot:

$(\theta_u, \theta_l) : Time \rightarrow [-\pi, \pi]^2$, where $\theta_u (t), \theta_l (t)$ are the angles made with the upper and lower arm at time $t$.


## Sequences

Temporal or spatial information can be represented by functions of time or space variables, and as well, can be represented by sequences of symbols, occurring as a representation of data, or an event stream.

#### Binary Files

An N-bit file $b_1, b_2, \ldots, B_n$, where each $b_i \in Bin = \{0,1\}$, can be regarded as a funciton $File: \{1,2,\ldots, N\} -> Bin$, where the assignment $File(n) = b_n$ for every $n \in \{1, \ldots, N\; \}$. We can also take the range to be $EnglishWords$, with an N-word long English text being a function

$EnglishText: \{1,2,\ldots, N\} -> EnglishWords$.

Typically, data sequences are functions of the form $Data: Indices -> Symbols$, where $Indices \subset Nats$. An advantage of this is Data can be a discrete-time signal, however $Indices$ do not represent uniformly spaced instances of time. However, we can say that if $m,n \in Indices$, with $m < n$, then the $m^{th}$ symbol $Data(m)$ occurs before $Data(n)$, but just not the amount of time elapsed between them.

The other representation, event streams or traces, are formed from a log of significant events, and are functions of the form $EventStream: Indices -> EventSet$.

## Discrete Signals And Sampling

Continuous time signals are considered so, because $Time$ is a continous domain of the form $[\alpha, \beta] \subset Reals$, and as well, $Image$ is a continuous 2-dimensional shape of the form $[a,b] \times [c,d] \subset Reals^2$
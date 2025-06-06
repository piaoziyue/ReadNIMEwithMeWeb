---
layout: post
title: "Mismatch perception in kinesthetic awareness"
tags: embodied
categories: reading
---
# inner subject perception and execution

## a model for motor control 
Wolpert, D. M., Ghahramani, Z., & Jordan, M. I. (1995). "An internal model for sensorimotor integration." Science, 269(5232), 1880-1882.

**internal model**: a system that mimics the behavior of a natural process
* **forward models**, which mimic the causal flow of a process by predicting its next state (for example, position and velocity) given the current state and the motor command;
  * Forward Models: Predicting the Future
    
    A forward model takes the current state of your body (e.g., the position and speed of your arm) and the motor command (e.g., "contract this muscle"), and predicts what will happen next. It mimics the causal flow—the sequence of events from action to outcome.

  * **How It Works**:
    Input: Current state (where your arm is now, how fast it’s moving) + motor command (what your brain tells your muscles to do).
    
    Output: Prediction of the next state (where your arm will be, how fast it will be moving).
    
    Purpose: It lets your brain anticipate the result of a movement before it happens.
* **inverse models**, which invert the causal flow by estimating the motor command that caused a particular state transition. 
  * It takes a desired outcome (e.g., "I want my arm to end up there") and figures out the motor command needed to make it happen. It inverts the causal flow, going from effect back to cause.

  * **How It Works**:
    Input: Desired state (where you want your arm to go).

    Output: Motor command (what muscles to activate and how much).

    Purpose: It tells your brain how to achieve a goal.

* **how to obtain an estimate of the current state**
Through **the position and velocity** of the hand. The system can make use of **sensory inflow** (the information available from proprioception), it can make use of **integrated motor outflow** (the motor commands sent to the arm), or it can **combine these two sources of information** by use of a forward model.

## 

Kawato, M. (1999). "Internal models for motor control and trajectory planning." Current Opinion in Neurobiology, 9(6), 718-727.


## knowledge
8James Fentress and Chris Wickham claim that this is a habit of “Western” thought that tends to “divide knowledge into three broad categories: propositional knowledge, or knowledge about things; sensory and experiential knowledge, or knowledge directly of things; and skill knowledge, or knowledge how to do physical things,” with knowledge “about” privileged as complete knowledge (1992:3)

## difficulty of kinesthetic experience

Samudra, J.K., 2008. Memory in our body: Thick participation and the translation of kinesthetic experience. American ethnologist, 35(4), pp.665-681.

> The cultural knowledge of people with specialized body techniques, including spirit mediums who trigger trance states through repetitive movement, musicians, dancers, soldiers, and martial artists and other athletes, is deeply embodied and often not transmuted into semiotic code.

> Those involved in kinesthetic practices discover, instead, that one can be a fully conscious actor in the body without necessarily encoding the meaning of one's actions in words.5

> People can be expected to flounder in the attempt to verbalize kinesthetic practices that cannot be performed smoothly if filtered first through language.

> An anthropologist intent on understanding the meanings of kinesthetic actions faces the peculiar difficulty of rendering into discourse exactly those practices his or her consultants consider verbally inexpressible.6 The usual methods of collecting data through linguistic and visual media may not suffice; even participation alone is no guarantee of success, for the researcher is still left with the problem of how to analyze newly acquired physical skills as a shared social experience

# 
Proske, U. and Gandevia, S.C., 2012. The proprioceptive senses: their roles in signaling body shape, body position and movement, and muscle force. Physiological reviews.


# Principles of sensorimotor learning
Wolpert, D.M., Diedrichsen, J. and Flanagan, J.R., 2011. Principles of sensorimotor learning. Nature reviews neuroscience, 12(12), pp.739-751.

> Sensory streams are temporally delayed and tend to be corrupted by appreciable amounts of noise. 
> Given the stream of sensory input, there are at least three computations that can improve the accuracy of the sensory information and that can be understood within the framework of Bayesian inference. 
> * First, **multiple streams of sensory information, within and across modalities (for example, visual and tactile inputs), can be optimally combined to achieve estimates that reduce the effects of noise** (for a review see Ref. 14). Interestingly, this integration process can take into account the properties of external objects, such as tools, so that the **visuo–haptic integration** is optimal even when the tactile input comes through a hand-held tool15. 
> * Second, by learning the statistical distribution of possible states of the world — that is, different possible configurations or scenarios, termed the prior within Bayesian inference — the estimate can be further refined (for a review see Ref. 16). 
> * Lastly, by combining these processes with internal models of the body that map the motor commands (as signalled through the efference copy) into the expected sensory inputs, Bayesian inference can be used to estimate the evolving state of our body and the world (for example, Ref. 17). **Such an estimator is termed a Kalman filter and aims to optimally estimate the state, given sensory feedback, efference copy and knowledge of the dynamics and properties of sensory and motor noise**.
---
layout: post
title: "Music Tech Basic: Sound"
tags: SoundSynthesis
categories: foundation
---

# 4.3 - Sound Synthesis and Audio Processing
## Book: "Computer Music_ Synthesis, Composition, and Performance (1997)"
Author: Charles Dodge, Thomas A. Jerse
【2023 Dec8-Dec13】 

chapters plan: 2-7 8/9

## Chapter 2:

### Sound: [Vibration source](https://www.youtube.com/watch?v=aPswnDcteS4). 
* Vibration disturb the air molecules adjacent
* Synchronism with the vibration
* alternately pulling apart(air pressure lower than average - rarefactions) and pushing together the molecules (air pressure higher than average compressions)

[Schlieren flow visualization](https://www.youtube.com/watch?v=px3oVGXr4mo) visualizing the sound

### Waveform
* The pattern of pressure variations in time

* \+ Compression 
\- rarefactions

![](../images/SRL_4.3SSAP/../../../images/SRL_4.3SSAP_1_1.png)
smallest unit: cycle

### Amplitude
* displacement of particles in a medium from their equilibrium position as a sound wave passes through it
* indicative of the amount of acoustic energy
* Newtons per square meter ($N/m^2$)

### Intensity
* the amount of energy carried by a sound wave per unit of time and unit of area
* the power in a sound actually contact a surface, usually the eardrum
* Watt per square meter ($W/m^2$)
* human can perceive 1 - $10^{12} W/m^2$

### Two modes of auditory perception
#### linear mode:
* physical properties of a sound wave and the perceived sensation
* directly to changes in loudness
* ❌ align with human perceive sound
  
#### Logarithmic mode: 
* A/B=C/D, => a change from A to B would be perceived as the same amount of increase from C to D
* better reflect how human perceive changes in sound
* Compare the intensity of two signals: ![](../images/../../images/SRL_4.3SSAP_1_2.png)
* Compare the amplitude of two signals: the amplitudes needed to be measured in the same set of conditions ![](../images/../../images/SRL_4.3SSAP_1_3.png)
* Unit: decibel (dB)

### Sound pressure level: 
implicit a measurement as the threshold of audibility

### Sinusoid
#### Phase
* relative position of two waveforms
* e.g.: here take A as the reference, here B is $-30^o$
  ![](../images/../../images/SRL_4.3SSAP_1_4.png)

### pitch
#### just noticeable difference (JND) / frequency (Ernst Weber)
it is the minimum amount of change in a stimulus that can be perceived by an observer. In auditory perception, the stimulus is on the **basilar membrane**

* pitch perception and frequency almost exavtly proportional (nonlinear relationship)
* listeners compare tones based on ratio not differences
* ![](../../images/SRL_4.3SSAP_1_5.png)


### Fundamental and partial frequencies

* F0 / fundamental frequency / first harmonic
* Harmonic / harmonic partials 
  
### beating
[Demo](https://youtu.be/V8W4Djz6jnY?si=ZBqOSBAVKRdJGzZ5)
*  beating occurs at a rate corresponding to the difference between the frequency of the tone near the octaveand the frequency exactly an octave above the lower tone. 
*  This "beating of mistuned consonances" disappears above around 1500 Hz.s
*  two tones occurs at or near the interval of the pure fifth (3:2 in frequency ratio) or the pure fourth (4:3 in frequency ratio)

### Pioneers

Max Mathews: [Computer synthesis of sound intro](https://www.youtube.com/watch?v=6ZO8SePPvL0)

### words can be used in class

Most computer-music synthesis systems offer the musician complete freedom of choice with respect to tuning. -> experiments

Equal temperament with 12 semitonal divisions of the octaveis by far the most com­ mon system of musical intonation used today in Western music for keyboard instru-


p12 ramp time


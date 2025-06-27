---
layout: post
title: "ML related papers related to sensing"
tags: piano
categories: reading
---

# IMUSE: IMU-based Facial Expression Capture


## Basic info of the paper
**Goal**: Use IMUs for facial expression capture

**Existing tech and its problems**: visual based techniques (RGB or RGBD), need camera, so have high requirements for lightning and sight

**IMU's advantages**: 
* sparser spatial signals than visual data 
* lower signal-to-noise ratios
* occlusions for video: for example eating apples

**what we did in this research**:
* developed IMUSE to detect facial expression
* created a IMU dataset (IMU-ARKit) that consists of IMU, visual signals and ARKit parameters
* trained a Transformer Diffusion-based neural network [41] to reliably infer Blendshape parameters directly from the IMU signals

## Methodology

**IMU sensor**: nine-axis sensing sub-units, which include the [QMC5883P](https://www.qstcorp.com/en_comp_prod/QMC5883P)

**calibration**: from the IMU’s local coordinate system to the world coordinate system

**Blendshape facial animation**

**model training**: 
* collect data from IMU and ARKit from 20 different participants with a set of 11 IMU detectors
  1) Before the formal data collection process began, participants were given time to adapt to the sensation of wearing IMUs, ensuring captured facial movements were natural and unrestricted. 
  2) Participants were instructed to tap the IMU located on mentalis at the start of each recording, as reference frames for synchronizing the IMU signals with the visual signals. The data was divided into three parts by intentionally designed content that disentangles facial expressions into plain facial movements and emotions. In the first part, participants read aloud the provided content in a calm tone, with a split between native language and English. This was done to capture the natural facial movements associated with the language. In the second part, participants were asked to sequentially make a series of facial expressions that were based on specific classifications, ensuring a full range of emotions and movements. 
  3) Finally, participants were asked to perform lines of one specific emotion from a set of emotions, joining plain facial movements with emotions.

## Some good sentences can be cited

* We demarcated **distinct facial zones**, referencing key anatomical landmarks including: the zygomaticus area, crucial for expressing emotions like joy or sorrow; the buccinator and mentalis area, fundamental for movements pertinent to speech; the orbicularis oculi area, important for a spectrum of expressions such as smiling and frowning; and the frontalis area, integral for conveying sentiments such as dissatisfaction or melancholy. **In every designated region, we meticulously placed at least one IMU; in regions characterized by dense muscle presence or complex movements, we opted for dual IMU placement**

## cue for using IMUs from this paper

* attach IMUs to distinct regions to accurately capture the movement

# SparseIMU: Computational Design of Sparse IMU Layouts for Sensing Fine-grained Finger Microgestures
> TOCHI 2023

## Abstract: 
Gestural interaction with freehands and while grasping an everyday object enables always-available input. To sense such gestures, minimal instrumentation of the user’s hand is desirable. However, the choice of an effective but minimal IMU layout remains challenging, due to the complexity of the multi-factorial space that comprises diverse finger gestures, objects, and grasps. We present SparseIMU, a rapid method for selecting minimal inertial sensor-based layouts for effective gesture recognition. Furthermore, we contribute a computational tool to guide designers with optimal sensor placement. Our approach builds on an extensive microgestures dataset that we collected with a dense network of 17 inertial measurement units (IMUs). We performed a series of analyses, including an evaluation of the entire combinatorial space for freehand and grasping microgestures (393 K layouts), and quantified the performance across different layout choices, revealing new gesture detection opportunities with IMUs. Finally, we demonstrate the versatility of our method with four scenarios.

## Contributions
* SparseIMU: a rapid method for selecting minimal inertial sensor-based layouts for effective gesture recognition
* a computational tool to guide designers with optimal sensor placement


## Basic info of the paper
**Existing tech for detecting microgestures and its problems**: its hard to build system that can recognize microgesture in both free-hand and busy-hand conditions. IMUs layout is crutial but is currently chosen manually from trial-and-error. 
  * **data gloves**: impede the dexterity of fingers. **Pros**: capture high-fidelity information; **cons**: bulky and impede the dexterity of fingers
  
  * **optical sensing**: CyclopsRing [13] proposed a finger-worn fisheye camera device to detect on-finger and in-air pinch and slide gestures, as well as palm-writing, FingerInput [85] demonstrated the detection of thumb-to-finger gestures using a head-mounted or shoulder-mounted depth sensor. Sugiura et al. [87] have shown recognition of discrete fingerbased gestures using an array of photo-reflective sensors placed on the back of hand. A variety of other sensing approaches include ultrasonic [41, 63, 64], infrared [27, 44, 63, 108], pressure [16, 21, 98], magnetic [3, 37, 69], and capacitive techniques [7, 91]. Due to the advances in deep learning, researchers have also demonstrated the detection of fine finger movements using radar sensing [96]. These systems show some remarkable success in enabling gesture recognition in freehand conditions. **con**: (a) However, due to the inherent property of such sensing technologies, these approaches can fail under occlusion caused by holding an object. (b) scalability issue
  
  * **wrist band (EMG, smartwatch..)**: the "Always-availabe input" paper, **cons**: selected grasp variations and the number of gestures are limited due to the lower resolution of the technique.

  * IMU on hands: [55], [6]

**Our approach**: A web-based design tool provides designers with the possibility to specify high-level requirements (e.g., desired set of gestures and grasps) and designer-specified constraints (e.g., locations on the hand and fingers that shall remain un-instrumented, and the total number of IMUs to be deployed). It then automatically selects an optimal sparse IMU layout matching the given preferences as shown in Figure 1(b). In addition, the tool predicts the expected performance of gesture classification, including a confusion matrix. 
  * enable a generic and scalable solution
  
  * We use a dense network of 17 IMUs to capture high-dimensional sensor data with nearly full degrees of freedom (DOFs) of the hand/finger space.

**microgesture dataset**: in a total of 360 gestures: 6 (gestures) × 5 (fingers) × 12 (objects), with the following kinds of gestures. Overall, our dataset contains a total of 13,860 trials (1,155 trials × 12 participants) with 18 different gesture and three non-gesture states performed on 12 Grasp variations and with Freehand.

  * Grasping status (objects) ![](/assets/2025-06-03-SparseIMU-handgesture.png)
  * Finger movement (gestures) ![](/assets/2025-06-03-fingergestures.png)

  * **Raw Variables**: 17 IMUs × 9 axes = 153 real-valued signals per frame, sampled at 100 Hz.
  * **Feature Variables**: From each axis, extract six time-domain statistics, yielding 918 features per trial (for the full 17-IMU setup).
  * **Labels**: 19 classes (18 finger-gesture classes + 1 static hold) for each model.
  * **Usage in Training**: Each candidate layout (subset of IMUs) produces a feature subset (e.g., 162 features if 3 IMUs). A Random Forest is trained on these features (80:20 split or LOPO) to predict the correct gesture/non-gesture label.
  * **Goal**: Identify which sparse set of IMUs (as few as 3–6) can achieve ≥ 90 % macro-F1, enabling minimal instrumentation for real-time microgesture recognition. 

**Advantages of our method**: address the challenges of hand occlusion includes extensive hand instrumentation, which is time consuming

**Key insights**:
1. F1 Score Improves with More IMUs, But Plateaus Early
   * Freehand gestures: 
     * From 1 IMU (best F1 = 0.62) → 3 IMUs (F1 = 0.90) → 4 IMUs (F1 = 0.93)
     * Max F1 = 0.97 with 8 IMUs — only 4% improvement over 3-IMU setup
     * Surprisingly, F1 drops to 0.89 when using all 17 IMUs (due to overfitting, noise, or redundancy)

   * Grasping gestures (harder due to object interference):
     * 1 IMU (F1 = 0.54) → 3 IMUs (F1 = 0.88) → 4 IMUs (F1 = 0.90)
     * Max F1 = 0.93 at 6 IMUs — again, plateau around 4–6 sensors
   * Combined (Freehand + Grasping):
     * Follows similar trend
     * Max F1 = 0.92 at 8 IMUs
     * F1 = 0.91 already at 5 IMUs → only 1% gain beyond this
2. Sensor Placement Matters More Than Quantity
   * The specific location of IMUs heavily influences performance. 
   * Best locations often include:
     * Thumb (T-midd, T-dist)
     * Index (I-prox, I-dist)
     * Middle (M-midd, M-dist, M-prox)
   * Worst location: **Forearm — consistently gives lowest F1 (as low as 0.17–0.2)**!!!!!!!
3. !!!!!Possible to achieve gesture recognition via IMU on non-gesturing finger: Our findings from placing IMUs on a non-gesturing finger in Section 4.4 opens up a new avenue for microgesture detection in HCI by leveraging movement patterns caused by complex hand bio-mechanics in **non-instrumented fingers**.


## Some things can be cited
* **always-available input**: 
* **Microgestures** (or Micro-interactions) refer to the subtle finger movements that are fast, easy to perform, and may not interrupt the other ongoing tasks [5]
* **Leave-one-person-out (LOPO) evaluation**: how to understand the interpersonal difference

# Deep Inertial Poser: Learning to Reconstruct Human Pose from Sparse Inertial Measurements in Real Time

## problem solving
* multiple pose parameters produce the same IMU orientations.
* capturing IMU data in conjunction with ground-truth poses is expensive and difficult to do in many target application scenarios
* modeling temporal dependencies through non-linear optimization has proven effective in prior work but makes real-time prediction infeasible

## related technology
* **commercial motion capture**: 
  * cons: require expensive infrastructure and markers placed on the user
* **Marker-less multi-camera approaches**: 
  * pros: sometimes provide dense surface reconstructions 
  * cons: require controlled camera setups and can be computationally very expensive.
* **single RGB or RGB-D camera**
  * cons: require camera and less accurate


# Transfer Learning in Sensor-Based Human Activity Recognition: A Survey
> ACM Computing Survey 2025
This survey covers two main concepts: human activity recognition and transfer learning.

## Human Activity Recognition (HAR)
A typical HAR setup consists of a set of sensors S = {S1, S2, . . . , Sn } deployed for data collection, where each sensor Si collects sensor readings {Sti1, Si  t1+1, . . . , Sti2 } in the time intervalT from timestamps t1 to t2.

* Fixed-size windows: simpler and fewer computation requirements
* Time-based windows [112] 
* segmentation based on detecting change points [179]

## Transfer Learning 
A **supervised classification** problem learns a predictive function f : X → Y , where X = {X1, X2, . . . , Xm } are data points and Y = {Y1, Y2, . . . , Yk } are class labels

A domain 𝐷 consists of two parts:
* a feature space 𝑋, which is the set of all possible input vectors X = {X1, X2, . . . , Xm }
* a marginal probability distribution 𝑃(𝑋) over those features.

A task 𝑇 (here e.g. supervised classification) consists of:
* a label space 𝑌, which is the set of all possible class labels Y = {Y1, Y2, . . . , Yk }
* a predictive function 𝑓 : 𝜒 → 𝑌 that maps feature vectors to labels.
(if 𝑌 or 𝑓 are different in T1 and T2, then they are different tasks)

Transfer learning is the process of transferring knowledge from one domain 𝐷1 and task 𝑇1 to another domain 𝐷2 and task 𝑇2, where 𝐷1 != 𝐷2 or 𝑇1 != 𝑇2.

### Two important concepts in transfer learning:
*(1)* the problem setting (similarities or differences in domains and tasks) 

*(2)* the interpretation of the term knowledge.

### the possible problems we summarized in this survey: 
* domain adaptation
* sample selection bias/covariate shift
* multi-task
* self-taught learning

## HAR main challanged with transfer learning
* Lack of Labeled Data
* Noise
* Learning Generalizable Features: 
  > An empirical study testing the role of features indicated that no set of features is optimal across different HAR problems [76]. This makes generalizable feature learning a unique challenge to sensor-based HAR
* Sensor Heterogeneity: e.g. Different Numbers of Sensors, Different Types of Sensors, Different Hardware and Sampling Rates, Different Coverage and Placement

## Heterogeneous transfer learning
the source and target feature spaces differ, i.e., χs χt . Heterogeneity in feature space can be induced by (1) a change in sensor modalities across domains or (2) a change in other aspects (e.g., sensor layout, cardinality, location, frequency).

> Sensors often belong to a functional group, where they are attached to specific objects (e.g., entrance doors) and capture information specific to them (opening and closing)
  
### Approaches

*(1)* **a mapping function** between the source and the target feature spaces is learned
  * e.g. sensor profiling
*(2)* **a transformation** is applied (learned) on both source and target feature spaces to arrive at a common space, where models can be shared

## Heterogeneous Transfer in Wearables

*(1)* m-heterogeneity (a change in sensor modality),

*(2)* **p-heterogeneity (a change in sensor position)** the one we will highly possibly use in our research!!!!

*(3)* d-heterogeneity (default case: change in device aspects).

## All things related to IMU


# Deep Inertial Poser: Learning to Reconstruct Human Pose from Sparse Inertial Measurements in Real Time

## Methodology
* Stage 1: Train on purely synthetic IMU–pose pairs (from AMASS).

* Stage 2 (Fine-tuning): Use the DIP-IMU real dataset (with 17-sensor-based reference poses) to adapt the network to real-world noise and motion patterns.

### Model and Synthetic Data Generation
* They adopt the SMPL body model (72 pose parameters + 10 shape parameters) as a “ground-truth” pose space.

* By taking large existing MoCap datasets (AMASS, which itself unifies CMU, H3.6M, etc.), they place virtual IMUs on the SMPL mesh and “play back” each MoCap sequence.

* For every frame, they extract a synthetic IMU reading:
  * Orientation from forward kinematics (virtual sensor rotation).
  * Acceleration via finite differences of the sensor’s 3D position.


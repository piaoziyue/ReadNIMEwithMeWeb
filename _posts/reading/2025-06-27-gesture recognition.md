---
layout: post
title: "Gesture Recognition"
tags: piano
categories: reading
---

# General Gesture Recognition

## [UbiComp'24] Boxing Gesture Recognition in Real-Time using Earable IMUs
* **Goal**: head gesture recognition for real-time box-ing gesture recognition
* **Research questions**
  * **RQ 1**: How can classical machine learning and dynamic time warping techniques be applied to IMU data obtained through OpenEarable devices to attain real-time and effective boxing head gesture recognition? 
  * **RQ 2**: How can a boxing head gesture recognition system be integrated into the OpenEarable framework to provide real-time feedback?
  
* **Method**:
  * IMU
  * Dynamic-time-warping (DTW) : to recognize gesture across different users, Dynamic Time Warping Barycenter Averaging (DBA) (François Petitjean, Alain Ketterlin, and Pierre Gançarski. 2011. A global averaging method for dynamic time warping, with applications to clustering. Pattern Recognition 44, 3 (2011), 678–693.)
  * classical machine learning (ML) methods (RF, Decision tree, SVM), 99% accuracy in testing and 96% in real-world scenario
* **Gestures**:
  * Idle, Left Slip, Right Slip, Left Roll, Right Roll, Pullback

## [CHI'25] Datamancer: Bimanual Gesture Interaction in Multi-Display Ubiquitous Analytics Environments
* **System Usability Scale (SUS)**: John Brooke. 1996. SUS - A ’Quick and Dirty’ Usability Scale. In Usability Evaluation In Industry. CRC Press, Boca Raton, FL, USA, 189–194.

## data processing
  * data augmentation: random rotation, translation, scaling, and flipping
  * data normalization: min-max normalization
  * data splitting: 70% training, 15% validation, 15% testing
  * data balancing: oversampling the minority class
  * data smoothing: moving average filter
  * data resampling: resampling the data to a fixed frequency
  * data segmentation: segmenting the data into fixed-length windows

## [TEI'24] E-textile Sleeve with Graphene Strain Sensors for Arm Gesture Classification of Mid-Air Interactions
* **Paper structure can be refer**: sensor design, fabrication process, seamless interconnection method, and detachable hardware implementation
* **Deep learning model**: A deep learning model integrating both a convolution neural network (CNN) and LSTM (Long Short - Term Memory) was selected for the classification. The model’s architecture was originally developed for classifying time-series data for hand gesture recognition [3]. The CNN layers are used to automatically and adaptively learn spatial hierarchies of features from the time series data, and the LSTM layers are used to learn temporal dependencies from the features obtained by the CNN. The architecture initially includes a TimeDistributed wrapper that allows for CNN application at each  1University ethics approval for this study was granted by [redacted for review]  time step of the input sequences. The CNN component comprises two Conv1D layers, each accompanied by a BatchNormalization layer and a MaxPooling1D layer. Activation functions, ’tanh’ and ’relu’, are utilized for enhanced non-linearity after certain layers. A Dropout layer, set at a rate of approximately 21%, is employed to mitigate overfitting. The CNN output is flattened to feed into two LSTM layers designed to capture temporal dependencies. Each LSTM layer is complemented with a Dropout layer for overfitting prevention. Subsequent to the LSTM layers, a fully connected (FC) layer with ’tanh’ activation is employed. Model training is performed using the Adam optimizer with a learning rate of 1e-4, and a categorical cross-entropy loss function. Model performance is monitored based on validation accuracy throughout training. The model is trained for 200 - 600 epochs (depending on the convergence of training accuracy), with a batch size of 64.

* a figure for directly showing the sensor signal for each gesture, a very good example of how to show the data:
![](/assets/2025-06-27-gesture%20signals.png)

# Hand Gesture Recognition

## [CHI'24] EchoWrist: Continuous Hand Pose Tracking and Hand-Object Interaction Recognition Using Low-Power Active Acoustic Sensing On a Wristband

* **Goal**: A **wristband** for 3D hand poses and recognizes hand-object interactions using active acoustic sensing (inaudible sound waves with two microphones)

* Literature review: Hand pose tracking and gesture recognition:
  * Gloves: 
    * [John Perng, B. Fisher, Seth Hollar, and Kristofer Pister. 1999. Acceleration sensing glove (ASG). 178 – 180. https://doi.org/10.1109/ISWC.1999.806717.]
  
  * Ringers:
    * [Tap Systems Inc. 2022. Tap. Retrieved Sep 14, 2023 from https://www.tapwithus. com/product/tap- strap- 2/]
  
    * [Farshid Salemi Parizi, Eric Whitmire, and Shwetak Patel. 2020. AuraRing: Precise Electromagnetic Finger Tracking. Proc. ACM Interact. Mob. Wearable Ubiquitous Technol. 3, 4, Article 150 (sep 2020), 28 pages. https://doi.org/10.1145/3369831]
  
    * [Hsin-Ruey Tsai, Cheng-Yuan Wu, Lee-Ting Huang, and Yi-Ping Hung. 2016. ThumbRing: Private Interactions Using One-Handed Thumb Motion Input on Finger Segments. In Proceedings of the 18th International Conference on HumanComputer Interaction with Mobile Devices and Services Adjunct (Florence, Italy) (MobileHCI ’16). Association for Computing Machinery, New York, NY, USA, 791–798. https://doi.org/10.1145/2957265.2961859]
  
    * [Anandghan Waghmare, Youssef Ben Taleb, Ishan Chatterjee, Arjun Narendra, and Shwetak Patel. 2023. Z-Ring: Single-Point Bio-Impedance Sensing for Gesture, Touch, Object and User Recognition. In Proceedings of the 2023 CHI Conference on Human Factors in Computing Systems (Hamburg, Germany) (CHI ’23). Association for Computing Machinery, New York, NY, USA, Article 150, 18 pages. https: //doi.org/10.1145/3544548.3581422]
  
    * [Anandghan Waghmare, Ishan Chatterjee, and Shwetak Patel. 2023. Z-Pose: Continuous 3D Hand Pose Tracking Using Single-Point Bio-Impedance Sensing on a Ring. In Proceedings of the 2nd Workshop on Smart Wearable Systems and Applications (Madrid, Spain) (SmartWear ’23). Association for Computing Machinery, New York, NY, USA, 1–6. https://doi.org/10.1145/3615592.3616851]
  
    * [Hao Zhou, Taiting Lu, Yilin Liu, Shijia Zhang, and Mahanth Gowda. 2022. Learning on the Rings: Self-Supervised 3D Finger Motion Tracking Using Wearable Sensors. Proc. ACM Interact. Mob. Wearable Ubiquitous Technol. 6, 2, Article 90 (jul 2022), 31 pages. https://doi.org/10.1145/3534587]

> skin-contacting technologies require sensors tightly attached to the skin, potentially causing discomfort over time. Therefore, contact-free hand-tracking technologies have garnered interest due to their comfort for extended use and promising performance potential.
> In addition, many EMG-based methods usually place sensors at mid-forearm rather than a wristband, which may compromise comfort and convenience.
> wearable cameras, such as IR cameras [25, 81], thermal cameras [18] and depth cameras [9]. However, they usually have significant power requirements and spacing constraints [9, 25, 81], making them difficult to integrate into wearables such as smartwatches.
 
* **Discrete gesture recognition**:
  * **Using EMG**:
  A heavily explored direction is using electromyography (EMG), which captures electric signals from muscle movements [11, 23, 59, 60, 65, 66]. Similar sensors include electric impedance sensing [24, 86, 87] and ultrasonic imaging [45]. These technologies detect gestures through internal changes but usually require skin contact and calibration. Another approach utilizes piezoelectric sensors [1, 10, 16], surface transducer [82], or high-frequency motion sensors [31], which capture bio-acoustic signals from wrist and finger movements. Technologies based on monitoring local shape changes use less invasive modalities such as pressure/flexors [7, 38] and capacitive sensors [61, 64, 70–72], with some achieving ultra-low-power performance [72].

  * **Using IMUs**:
    * Ring: 
      * Farshid Salemi Parizi, Eric Whitmire, and Shwetak Patel. 2020. AuraRing: Precise Electromagnetic Finger Tracking. Proc. ACM Interact. Mob. Wearable Ubiquitous Technol. 3, 4, Article 150 (sep 2020), 28 pages. https://doi.org/10.1145/3369831
  
      * Hsin-Ruey Tsai, Cheng-Yuan Wu, Lee-Ting Huang, and Yi-Ping Hung. 2016. ThumbRing: Private Interactions Using One-Handed Thumb Motion Input on Finger Segments. In Proceedings of the 18th International Conference on HumanComputer Interaction with Mobile Devices and Services Adjunct (Florence, Italy) (MobileHCI ’16). Association for Computing Machinery, New York, NY, USA, 791–798. https://doi.org/10.1145/2957265.2961859

  * **Other methods**:
    > Other methods include proximity sensor arrays positioned on the wrist [15, 26] or thumb [69], as well as vision sensors like RGB [78] and IR [37, 44, 81]. Still, due to their limited precision in capturing hand-pose data, these methods usually recognize only a few gestures, preventing many potential applications.

* Continuous hand pose tracking:
  * **Using EMG**:

## [UIST'24] Gait Gestures: Examining Stride and Foot Strike Variation as an Input Method While Walking


## [CHI'25] Gesture and Audio-Haptic Guidance Techniques to Direct Conversations with Intelligent Voice Interfaces
* This paper's figures are all amazing: **A good intro figure to refer to**: 
![](/assets/2025-06-27-intro-meta.png)


## [ICORR'19] IMU-based assistance modulation in upper limb soft wearable exosuits
* We can refer it how to analyse angle difference between trials
* **IMU Calibration**:
  A calibration procedure is performed on each user before the start of the experiment to identify the transformation matrix related to each IMU sensor. These matrices relate the transformation from the sensor reference frame to the axis of rotation of the respective body part to which the sensor is attached. During the experiment calibration phase, the user is asked to perform three movements with four repetitions each: 1) rotation of the trunk in the transverse plane, 2) rotation of the trunk in the sagittal plane, 3) flexion/extension of the shoulder in the sagittal plane. A detailed explanation of the calibration procedures and algorithm for computing the joint angles can be found in the work by Ricci et al. [18].
  [L. Ricci, D. Formica, L. Sparaci, F. R. Lasorsa, F. Taffoni, E. Tamilia, and E. Guglielmelli, “A new calibration methodology for thorax and upper limbs motion capture in children using magneto and inertial sensors,” Sensors, vol. 14, no. 1, pp. 1057–1072, 2014.]

## [IMWUT'24] IMUGPT 2.0: Language-Based Cross Modality Transfer for Sensor-Based Human Activity Recognition

* Describe how GPT can help with generating virtual IMu data which will reduce the need for large-scale data collection


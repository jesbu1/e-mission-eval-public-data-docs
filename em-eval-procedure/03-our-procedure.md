Controlled Evaluation of context-sensitivity
============================================

Instruments are typically evaluated by repeatedly exposing them to controlled inputs to determine their error characteristics. In the case of complex systems such as HMSes, the evaluation needs additional controls for feedback loops, cost/accuracy trade-offs and privacy considerations. In this section, we outline em-eval — a procedure for HMS evaluation that addresses these concerns with two techniques that are novel in this domain:

1.  predefined, **artificial trips** that support spatial ground truth, preserve privacy, increase the breadth of *trip types* and support repetitions for establishing error bounds, and

2.  power and accuracy **control phones** carried at the same time as the experimental phones, that can cancel out context-sensitive variations in power and accuracy.

Artificial timeline
-------------------

The core of the experimental procedure is the predefined specification of a sequence of artificial *trips*, potentially with multiple *legs* or *sections* per trip. The trajectory and mode of travel is also predefined. The *data collector* completes the timeline trips by strictly following the specified trajectory and mode while carrying multiple phones that collect data simultaneously using different configurations.

The specified predefined trajectories provide spatial ground truth. We do not predefine temporal ground truth since it is extremely hard to control for differences in walking speeds, delays due to traffic conditions, etc. We use manual input from the data collector to collect *coarse* temporal “ground truth” of the transitions along the timeline. We do not use manual input for *fine-grained* temporal ground truth along the trajectory because:

1. human response times are too slow for fine-grained temporal ground truth during motorized transportation, and
1. distracting the data collector during active transportation can be risky.

Using an artificial timeline addresses several of the unique challenges associated with HMS evaluation.

Privacy  
Since the trips are artificial, they preserve the data collector’s privacy. Even if his adversaries would download the trips, they would not be able to learn anything about his normal travel patterns.

Spatial ground truth  
Since even high accuracy (GPS-based) data collection has errors, predefining spatial ground truth allows us to resolve discrepancies (Section [sec:relaxing-constraints]) and compute the true accuracy.

Breadth and variety of trips  
Artificial trips allow efficient exploration of the breadth of the trip space. For example, the trips could include novel modes such as e-scooters and e-bikes, or specify different contexts for conventional modes, such as express bus versus city bus.

Repetitions  
Since the trips are predefined, they can be repeated exactly. This allows us to use standard variance and outlier detection to estimate error bounds on the measured values.

Control phones
--------------

The artificial trips give us spatial ground truth, but they do not give us cost (power consumption) or temporal ground truth.

We control for the cost through the use of the use of multiple phones, carried at the same time by the data collector. The phones carried by the data collector are divided into control phones and experiment phones. The control phones represent the baseline along each of the axes in our trade-off and the experiment phones implement a custom sensing regime that is at some intermediate point. The evaluation procedure allows us to determine those points.

The power control phone captures the baseline power consumption of a phone that is not being used for tracking by a HMS. This does not mean that the phone is idle — phone OSes (e.g., iOS or android) are complex, context-sensitive systems that perform their own location tracking (e.g., “Find my iPhone”) and their own duty cycling (Figure [fig:power<sub>a</sub>ccuracy<sub>v</sub>ariations]). Using a power control allows us to identify the **additional power** consumed by the HMS, even if it is context sensitive.

The accuracy control captures the upper bound on the accuracy of a particular class of smartphones given sensor and OS limitations. While we would like to compare the experimental accuracy to ground truth,

1. all sensors have errors, so ground truth is not achievable in practice,
1. artificial trips give us spatial but not temporal ground truth, and
1. GIS-based trajectory specifications do not have an associated power trade-off.

Using an accuracy control allows us to compare the experimental data collection against the best achievable data collection, in addition to the ground truth.

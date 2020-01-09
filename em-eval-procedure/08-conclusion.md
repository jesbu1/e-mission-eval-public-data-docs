Conclusion
==========

Human Mobility Systems (HMSes) are complex software systems that run on equally complex smartphone operating systems (OSes). This complexity implies that there is rarely a simple linear relationship between their inputs and outputs, which complicates their evaluation.

We outline a procedure, based on repeated travel over predefined artificial *timelines* carrying experiment and control phones, to control this complexity. We show that it can control for outliers, and also reveal meaningful signals about the behavior of smartphone virtual sensors that are relevant to instrumenting human travel data.

The procedure is privacy-preserving, so it does not need human subjects approval. It focuses on *trip* diversity, not *demographic* diversity, so it can be undertaken by a small research group, or even a single researcher, as a pre-pilot before recruiting study participants. It uses predetermined trips and modes, so it can efficiently explore complex or newly emerging travel patterns and modes, such as e-scooters. The procedure, and the associated reference implementation can simplify the testing required before a study is launched.

The next stage is evaluation, which adopts this procedure to evaluate the sensing accuracy for various settings. In addition to assessing the architecture usage, we also gauge the ability of the analysis algorithms (Chapter [chap:pipeline<sub>i</sub>mpl<sub>d</sub>etails]) to boost the sensed accuracy.

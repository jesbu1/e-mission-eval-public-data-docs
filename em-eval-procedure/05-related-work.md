Related work
============

Human Mobility Systems (HMSes) are complex to evaluate (Section [sec:relaxing-constraints]). Other researchers have identified similar challenges as part of survey papers (e.g., phone context, privacy, learning, scaling , varying metrics and time scales across research areas ). However, to the best of our knowledge, there is no proposed solution that addresses all of them.

Papers related to instrumenting travel behavior fall into three main categories; we list some work from each as an example. A comprehensive classification of papers into categories is beyond the scope of this paper.

Context sensitive sensing algorithms: power without accuracy
------------------------------------------------------------

This research area focuses on context sensitive, adaptive power management of sensors. Papers such as ACE  and Jigsaw  compare their power requirements to naive sensing techniques. However, their accuracy evaluations focus on the localization error (Jigsaw), or comparison to naive inferred results[1] (ACE).

Travel diary systems: compare to manual surveys
-----------------------------------------------

There is a vast variety of one-off travel diary systems that combine smartphone based sensing with cloud-based processing to generate travel diaries. Systems such as such as Data Mobile , Future Mobility Study (FMS)  and rMove  aim to replace the paper and telephone based Household Travel Surveys with smartphone and cloud based systems. So they evaluate the accuracy of their systems against the traditional methods, not against ground truth. This can show that smartphone based methods are significantly better than traditional methods, but not provide a quantitative estimate of the accuracy of their system. Similarly, they do not include quantitative power evaluations - preferring statements like “Among the three types of discrepancies, the second type, data gap due to battery drainage, was most frequently observed.”  or “The battery consumption test was simply whether, under regular usage, the phone could make it through the day without having to be charged.” . So they do not rigorously evaluate either the power or the accuracy side of the trade-off.

Mode inference: accuracy without power, non-uniform data
--------------------------------------------------------

Mode inference of travel mode based on sensor data is an extremely popular subject in the literature[2]. Researchers have used decision trees , Hidden Markov Models , and neural networks  to distinguish between various subsets of travel modes. However, although the inference algorithms are different, most such papers use similar methods for evaluating their accuracy. They typically recruit a small sample of their friends (e.g., 16 users over one day , 4 users over two weeks ) to collect naturalistic data along with annotations of the ground truth. The data collection focuses on the sensors used for analysis and omits the battery. This kind of evaluation does not meet the any of the requirements outlined above, except privacy, which is addressed by not publishing the dataset.

[1] e.g., based on speed

[2] Probably because it is hard, and nobody has really solved it well yet for modes other than walking

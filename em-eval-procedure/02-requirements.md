Requirements for evaluating Human Mobility Systems (HMSes)
==========================================================

Human Mobility Systems (HMSes) need a methodology for rigorous evaluation that allows users of the data to understand their limitations and their accuracy in various settings. Before establishing such a method, we need to understand the evaluation requirements, and the challenges associated with meeting each requirement. Establishing a clear set of requirements also allows us to understand the limitations of the proposed method and provides a roadmap for future improvements.

Holistic evaluation: power vs. overall accuracy
-----------------------------------------------

Using smartphones for collecting background sensed location data leads to higher battery drain. Travelers are very sensitive to battery life  , and there is a clear power/accuracy trade-off for smartphone sensing. Naïve high accuracy sensing drains the battery for almost all users (Section [sec:modeling]), but techniques to lower battery drain also lower the accuracy (Section [sec:api<sub>o</sub>verview]) So it is critical that the evaluation consider both power and accuracy together. For example, if an HMS can get 95% accuracy, but runs out of battery in 2 hours, the deployer needs to adjust the incentives offered (e.g., money, utility, …) accordingly.

Privacy preserving
------------------

The data collected by HMSes includes location traces, which are inherently privacy sensitive. While a common privacy technique is to *de-link* datasets by replacing Personally Identifiable Information (PII) with a code , location traces allow re-identification from the raw data alone . Intuitively, from the location traces, we can find the *places* where people spend most of their time, which allows us to discover their home and work locations and uniquely identify them. This implies that the evaluation methodology must address privacy concerns.

Ground truthed
--------------

In order to fully evaluate the data collected, we need ground truth for not just the mode, but also the trip start and end times, section start and end times and the travel trajectory. Labeling trips through prompted recall is a low effort technique to collect mode ground truth, but it depends on accurate trip and section segmentation. Segmentation ground truth requires recalling the start and end *times* at the end of the day, which is likely to be unreliable . Similarly, for evaluating trajectories, travelers can potentially draw out spatial ground truth but spatiotemporal ground truth is almost impossible to obtain after the fact.

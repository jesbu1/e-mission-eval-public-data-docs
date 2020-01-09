Inspired by the popularity of smartphone-based personal fitness tracking, the transportation community aims to build Human Mobility Systems (HMSes) that can automatically track and classify multi-modal travel patterns. Such systems can replace expensive and infrequent travel surveys with long-term, largely passive data collection augmented with intermittent surveys focused on perceptual data.

While there has been much work on building HMSes, both in academia and in industry, the procedure to *evaluate* them has largely been an afterthought. Careful evaluations are critical as we move from the personal to the societal domain. Users who make decisions based on self-tracking have an intuition of its accuracy based on their experienced ground truth. The decisions are low-stakes lifestyle changes, which may be personally meaningful, but are not societally contentious. However, a Metropolitan Transportation Agency picking projects and allocating millions of dollars in funding needs to know the accuracy of the data before making its decisions .

Computational Mobility (CM) can frame approaches to evaluate accuracy. Consistent with interdisciplinary research principles, we can apply computational concepts to shift the focus from ad hoc techniques to more rigorous concepts for evaluating software systems and algorithms. These concepts include:
1. *artificial workloads*, from Operating Systems,
1. *standard datasets*, from Machine Learning, and
1. *handling transient effects*, from Networking.

The rest of this chapter is structured as follows. We start with an intuitive description of the challenges and the solution in Section [sec:procedure<sub>i</sub>ntuition]. Next, we outline the evaluation requirements in Section [sec:eval<sub>r</sub>equirements] and outline an experiment procedure that meets them in Section [sec:our-procedure]. We discuss some alternative approaches in Section [sec:relaxing-constraints] and describe the reference implementation in Section [sec:system-experiment-design], concluding with Section [sec:eval<sub>c</sub>onclusion].

Intuition for challenges and solution
=====================================

The typical HMS evaluation procedure (e.g., Quantified Traveler, prior versions of our work) is ad hoc and also functions as a pilot — a small (\(\approx\) 3-12) set of the author’s friends and family are recruited to install the app component of the HMS on their phones, and go about their daily life for a few days or weeks while annotating the trips with “ground truth”. The ground truth annotation can either directly happen on the app, or through a recap at the end of the day. Conscientious researchers may ensure that the set of evaluators are demographically diverse, in an attempt to evaluate against a richer set of travel patterns.

While this procedure imposes little additional researcher burden, it conflates the *experimental* procedure (understanding human travel behavior in the wild) with the *evaluation* procedure (evaluating the instrument that will measure the human travel behavior). The first is trying to understand *behavior*, so it needs human diversity. The second is trying to understand *sensing* parameters, so it needs diversity of *trip types*. The human functions as a phone transportation mechanism during evaluation and could be profitably replaced with a self-navigating robot if one was available.

An analogy with classic physical measurements may be useful. Consider the situation in which a researcher wants to collect data on the weight distribution of the population in a particular region. Since there are currently no certifying bodies for travel diaries, let us pretend that she cannot purchase a pre-certified scale. How would she evaluate the available scales before starting her experiment?

The analog to ad hoc evaluation procedure would involve recruiting several of her friends and family to weigh themselves on the scales and compare the reported weight with their true weight. This analogy clearly reveals some limitations of the ad hoc procedure:
1. How does she trust that the self-reported weights are “true”?
1. If all her friends are adults weighing 55 kg – 75 kg, how does she know how the scales perform outside that range?

She can overcome the range limitations by recruiting a broader set of testers, e.g., through an intercept survey. However, that modification makes the ground truth limitation worse, since it is less likely that strangers will reveal their true weight. A further modification might pay contributors to improve the self-reported accuracy, but at this point, she is essentially running the experiment.

A more robust evaluation procedure would involve choosing known weights across a broad range (e.g., 0 kg to 300 kg in 10 kg increments) and comparing them to the reported weights. Since no instrument is perfect, there is likely to be some variation in the values reported. She would likely repeat the experiments multiple times in order to establish error bounds.

HMS evaluation procedures need to be more sophisticated than simple physical measurements since:
1. their operation is based on prior behavior (e.g., HMS duty cycling, android doze mode) and the potential for feedback loops makes it important to control the *sequence* of evaluation operations,
1. unlike a physical scale, which has a fixed one-time cost, they have an ongoing, variable cost in terms of battery drain, so the evaluation must assess the power/accuracy trade-off, and
1. unlike scalar weight data, HMSes generate strongly correlated timeseries data, which is extremely hard to anonymize.

Therefore, the main contributions in this chapter are:

1.  We propose an **evaluation procedure** for HMSes based on predefined, ground truthed, artificial trips and outline how it addresses the above challenges,
1.  We describe the design of a cross-platform **evaluation system** that can be used to perform such evaluations reproducibly and publish the results.
1.  We highlight some lessons learned during this process that future groups might want to take into account while designing their experiments.



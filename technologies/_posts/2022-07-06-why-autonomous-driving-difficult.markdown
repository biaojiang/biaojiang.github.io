---
layout: post
title:  "Why autonomous driving still a long way to go!"
date:   2022-07-06 19:21:00 +0200
categories: technologies
tag: autonomous driving
#comments: false
math: false
---

What are autonomous driving, autopilot, or self-driving car, you name a few, is not described here, there're a lot of articles hot about this topic.

I think [CBS News on "What's the status of self-driving cars?"](https://www.cbsnews.com/news/self-driving-cars-status-progress-technology-safety/) was a good discussion in earlier 2022. Recently, Elon Mask claimed to cut 200 employees in autopilot division. Of course, autopilot is not as simple as what production managers thought, it is an extremely costly and complicated engineering project covering mathematical model, wireless communication, sensor technologies, navigation, computing infrastructure, government regulations, transportation infrastructure, etc. Year 2050 is still too optimistic for a fully auto-driving car that you can ask it to go anywhere just simply sitting and being relax in the car.

Auto-driving car relies on the sensor technologies, Edge computing power and offline machine learning/AI model training. The following are some **technical bottlenecks**:

## Sensors and signal processing
Most people are not serious about the sensor limitations, how the sensor could reliably detect the surrounding objects depends on the signal-to-noise ratio (SNR), especially under bad weathers such as heavy snowing winter，extreme high/low temperature, etc.

Signal processing should have the ability to detect sudden events, such as a reckless driver suddenly changes the lane. Multiple-object discrimination and tracking are also important issues. [TI ADAS](https://www.ti.com/applications/automotive/adas/overview.html) has sensor data fusion hardware solution which could be possible to solve the data integration and processing latency problem.


### Machine learning and AI

When looking at most of the mainstream ML packages, i.e. Scikit-learn, TensorFlow, it can be noticed that most of the models just play probabilistic or statistical tricks, model mismatching is the main obstacle for ML models. Many people are spending much long time training the models with biased training data or less cleaned data. For auto-driving, outliers are important information for which it is difficult to collect all the outliers in driving scenarios.

Edge computer mounted inside the car cannot perform predictions merely based on the trained model in the Cloud, it should have online learning abilities otherwise it cannot deal with sudden events. 

Now many people from both academia and industry are talking about the most fashionable word of **AI** in the current age. However, hyping AI is the main objective to obtain funding, not many people how and whether AI could help their business or research. In **Github**, some people used the vibration sensor for predictive maintenance with **LSTM** model, but the features were not correctly calculated, and it is not necessary to apply LSTM at all, for which the false alarm rate is too high, even from the beginning with newly changed equipment/component, there are false alarms. The reason is that there is a tradeoff between data and domain knowledge, and sometimes the latter is more important.

> The current AI technologies are not truly AI, the machine can only learn what you teach them based on existing data. For reaction time and safety critical scenarios, the accuracy what the current AI models could achieve is still much lower than could be accepted. The autonomous driving won't come to reality until the machine is capable of thinking and making crucial decisions by itself.

---
layout: post
title:  "Ultrasound elastic image registration for arterial plaque motion stabilization!"
date:   2018-01-13 16:00:00 +0100
categories: projects
math: false
---

## Background

Atherosclerosis is a disease that causes stiffening and buildup of plaques in the arteries. The plaques can rupture and this may result in stroke (brain) or myocardial infarct (heart).

The plaques can be either stable or unstable (vulnerable) depending on their composition, meaning that just having a plaque is not necessarily hazardous.
Medically, if a patient has a large plaque, it is often surgically removed. However, since the plaques may not be vulnerable, there is a need for a screening/imaging method to assess the plaque’s vulnerability. Using non-invasive ultrasound, analyzing texture features (risk markers) of the imaged plaques has proven to be useful in detecting vulnerable plaques. However, due to the cyclic nature of the cardiac pacing, the blood pressure changes cyclically in the arteries causing complex movement and deformation of the plaque tissues. Previous studies have shown that the risk-markers change cyclicly with the cardiac cycle. In order to facilitate the calculation of risk-markers, and study the intra-plaque components, there is a need for a method to stabilize the plaque in the image sequence (remove the motion).

## Goal

* Implemented and evaluated methods for elastic registration.
* Recommendations on method optimizations.

## Applications

* New risk-marker for arterial plaque vulnerability

## Methods

1. Block-matching

1. Optical flow

1. Demons image registration

## Results

The pioneering results were produced by @biajiase, and based on which, 4 undergraduate students (supervisors: @biajiase and [Christer Grönlund](https://www.umu.se/en/staff/christer-gronlund/)) implemented in MATLAB, providing `.m` files and **GUI**, with presentation talked on 11th Jan, 2018. 

![Integrated medical ultrasound processing](/images/UCM.png)

If you have questions, you can send me email or check the following link for further information:

[Arterial plaque motion stabilization using optical flow][Ytube-optiFlow]

[Ytube-optiFlow]: https://www.youtube.com/watch?v=tQbdh-GNFic

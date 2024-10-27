---
title: Micro-imaging Segmentation at Nanolive
description: ML-based analysis to model the effects of a SARS-CoV-2 infection
slug: nanolive-optuna
date: 2024-10-26 00:00:00+0000
image: cells.png
categories:
    - research
    - mldl-engineering
tags:
    - Optimization
    - Nanolive
weight: 100 # You can add weight to some posts to override the default sorting (date descending)
toc: true
---

Between 2022 and 2023 I spend just over half a year at the startup [Nanolive](https://www.nanolive.ch). This startup offers a unique take on cell biology. Where traditionally, microscopy imaging is independent of any subsequent analysis, Nanolive offers a 2-for-1 package. Advanced image analysis with (pre)trained ML/DL models often suffer if the image acquisition procedure is systemically different from that seen in the training data. As such, digital analytical solutions often have to work on a wide range of noise signatures, optical aberrations, resolution differences, and much more. This is where the genius of offering a 2-for-1 package comes in. By standardizing the microscope, an analysis platform can be offered which is tailored to the imaging solution.

I had the pleasure to be part of the Deep Quantitative Biology team. This is their core R&D team, with exclusive access to their own wet lab. The team utilizes a combination of fluorescent labeling and manual labeling / label correction on an ih-house labelling platform to train cutting-edge segmentation models. One of my core responsiblity was to develop and manage an optimization platform. This platform was to take in previously existing models and data, explore samples, settings, and hyperparameter space, and automatically generate reports on the process. This allowed us to identify potential weaknesses of our models, but also to spend labelling efforts where they would be most impactful.


 
> Header image adapted from [here](https://commons.wikimedia.org/wiki/File:Human_mesenchymal_stem_cells.gif)
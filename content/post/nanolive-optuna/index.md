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

## Me and Nanolive

Between 2022 and 2023 I spend just over half a year at the startup [Nanolive](https://www.nanolive.ch), a startup bringing a unique approach to cell biology. Traditional microscopy typically separates acquisition and analysis as two separate steps, but Nanolive combines them into a unified, AI-powered solution. Advanced image analysis with (pre)trained ML/DL models often suffer if the image acquisition procedure is systemically different from that seen in the training data. Digital image analysis solutions often have to work on a wide range of noise signatures, optical aberrations, resolution differences, and much more. Nanolive's 2-for-1 package addresses this by standardizing the microscopy process, creating a robust platform for the included downstream analysis.

As part of the Deep Quantitative Biology team, Nanolive's core R&D team, one of my core responsiblities was to develop an optimization platform. The team has exclusive access to their own wet lab and utilizes a combination of fluorescent labeling and manual labeling / label correction on an ih-house labelling platform to train cutting-edge segmentation models. The optimization platform was to take in previously existing models and data, and to then explore subsamples, settings, and hyperparameter space, to optimize our models and automatically generate performance reports. This allowed us to identify potential weaknesses of our models, but also to spend labelling efforts only where they would be most impactful.

## Their Publication

Needless to say, I was thrilled to see my old team's latest publication: [Dynamic label-free analysis of SARS-CoV-2 infection reveals virus-induced subcellular remodeling](https://www.nature.com/articles/s41467-024-49260-7). Their unique position in the field allowed them to reach findings few other labs could: using Nanolive's label-free methodology, high quantities of live cells can be analyzed over a much longer period of time than competing technologies. Let's summarize who contributed, what their findings are and why this is valuable:

## Summary

### WHO
[Pasteur Institute](https://www.pasteur.fr/en)'s Virus & Immunity Unit and [Nanolive](https://www.nanolive.ch/about/company/)'s Deep Quantitative Biology team. Together, they bring strong virology expertise and a high-throughput, label-free methodology.

### WHAT
The authors analyze how SARS-CoV-2 impacts subcellular structures and internal cell dynamics, showing how the virus modifies cells to boost its own production and delay the host’s immune response. They further demonstrate the robustness of their ML segmentation despite the numerous challenges with establishing a ground truth in this space. This is then used to compare the organelle dynamics over two days for infected samples and non-infected control cells. Anyone familiar with the field will be aware that measuring hundreds of live cells over this large time-span while quantifying sub-cellular dynamics is a feat on its own! The authors further identify time-windows of the numerous effects of SARS-CoV-2 on the infected host, resolving conflicts in the existing literature. Finally, Bayesian networks for infected cells compared to control classes, show that SARS-CoV-2 strongly affects the process through which lipid droplets are produced. 

### HOW
Standard microscopy either lacks resolution or damages live cells, but Nanolive’s holotomography (HT) creates a 3D refractive index tomogram. This process, conceptually similar to a CT scan, yields high resolution output without damaging the cell. Nanolive is the first company to make microscopy solutions based on the HT principle commercialy available. Normally, staining or other markers would have to be added to label cells. Unfortunately, this damages the cell and can influence the inner cell dynamics. Manual labelling effort would be required to avoid using damaging agents, but this human involvement typically limits the amount of cells that can be quantified and analyzed. By using ML-based segmentation, hundreds of living cells and subcellular dynamics can be tracked over hours and even days.

### WHY
Understanding the subcellular changes during SARS-CoV-2 infection sheds light on its lifecycle and clarifies previously conflicting data by showing it varies over time. This paper is a big step forward in high-throughput, high-resolution analysis of cellular dynamics and demonstrates the potential of Nanolive’s innovative approach.

## Conclusion
Working alongside my former colleagues at Nanolive was truly a privilege. They’re some of the most dedicated, talented, and genuinely pleasant people I’ve had the opportunity to meet. Their commitment to pushing the boundaries of cell biology at Nanolive shines through in this latest publication. It’s rewarding to see even a small part of my work contribute to such impactful findings. I’m confident that with their skills and vision, there’s a bright future ahead for the team and the field of high-resolution, high-throughput cell analysis.

> Header image adapted from [here](https://commons.wikimedia.org/wiki/File:Human_mesenchymal_stem_cells.gif)
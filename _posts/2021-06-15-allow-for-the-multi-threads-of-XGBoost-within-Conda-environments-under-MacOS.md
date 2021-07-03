---
layout: post
title: Allow for the Multi-threads of XGBoost within Conda environments under MacOS
subtitle: Sharing the tricks to allow for Multi-threads within Conda environments under MacOS
gh-repo: AlfredSAM/alfredsam.github.io
gh-badge: [star, fork, follow]
tags: [Xgboost, Conda, R, Macos, Openmp, Medium]
comments: true
---

In general, the popular packages compiled in Linux system should be highly optimized to use multi-threads, but the subtle issues usually occur for compilation under MacOS. Here is my exploration about how to modify the make file to facilitae the compilation such that XGBoost in MacOS can utilize multi-threads. Please check [Allow for the Multi-threads of XGBoost within Conda environments under MacOS](https://medium.com/geekculture/allow-for-the-multi-threads-of-xgboost-within-conda-environments-under-macos-8959babb4599) and [Fail to install xgboost R package from source inside conda environment under MacOS (big sur)](https://github.com/dmlc/xgboost/issues/7017).

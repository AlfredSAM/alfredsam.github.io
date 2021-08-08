---
layout: post
title: Introduction to Computing Environments for Data Science  
subtitle: The First Course for Students to Study Data Science
gh-repo: AlfredSAM/alfredsam.github.io
gh-badge: [star, fork, follow]
cover-img:
tags: [Conda, Python, R, Environments, Jupyter Lab, Rstudio]
comments: true
---

(This post is dedicated to part of the bridging courses for the oriented students pursuing data science related master degrees in the Economics department of Hong Kong Baptist University. Interested audience can also refer to this post as the very beginning for the journey to the data science. Let's get started!)

Hello, everyone! Thanks so much for your application for the data science related master in the Economics department of Hong Kong Baptist University. First of all, your enthusiasm and interest on data science are highly appreciated, since this is one of the most exciting areas to create great welfare for the human beings. In most of the applications of data science, programming is the usual way (probably the only way) to implement various algorithms and models on distinct types of data, structured or unstructured, textual or numeric. Among multiple popular programming languages, [**Python**](https://www.python.org/about/) and [**R**](https://www.r-project.org/about.html) are undoubtedly the most common choices.

This post mainly introduces the basic setups of **Python** and **R** in the viewpoint of the **environments**. Following this post, a series of notes about the foundations of **Python** and **R** for data science are discussed. At the end of the bridging courses, you are expected to construct the appropriate computing **environments** for the targeting _projects_ and _tasks_. Furthermore, you are also expected to have basic concepts on data wrangling using related **packages** within **Python** and **R**. During the courses in the coming year, you are going to experience the applications of **Python**  and **R** for the main topics on Econometrics, Statistics, and Machine learning. Before the detailed discussion on the **environments**, several points about **Python** and **R** are also illustrated here.


Well, we have long long stories to tell about the issue of similarities and differences between **Python** and **R**, and interested audience can refer to [R wiki](https://en.wikipedia.org/wiki/R_(programming_language)) and [Python wiki](https://en.wikipedia.org/wiki/Python_(programming_language)). However, here I only give some high-level ideas. Generally speaking, **Python** and **R** are both _interpreted high-level programming languages_, relative to another bunch of _compiled low-level languages_, such as [c](https://en.wikipedia.org/wiki/C_(programming_language)), [cpp](https://en.wikipedia.org/wiki/C%2B%2B), and [Fortran](https://en.wikipedia.org/wiki/Fortran). For the _compiled low-level languages_, the codes are usually _compiled_ and _linked_ to generate the _executable_ programs before running, while _interpreted high-level programming languages_ are usually _comprehended_ and _executed_ line by line with corresponding **R** or **Python** _interpreter_. Generally speaking, **R** or **Python** are much easier to code and debug than **cpp** or **Fortran**, but _compiled low-level languages_ highly dominate _interpreted high-level programming languages_ in terms of execution time. So, why not directly learn **cpp** or **Fortran**? Please keep in mind that 

{: .box-note}
total time = development time + execution time, and human time is much more valuable than the CPU time.

For daily works, we usually stick to _interpreted high-level programming languages_ in the main source file, and then put the computational intensive parts to _compiled low-level languages_. In most of the time, we do not even touch the actual codes of **cpp** or **Fortran**, because they are _wrapped_ as the **Python** or **R** _packages_ and provide the _interfaces_ for **Python** or **R** to call. For example, [**XGBoost**](https://xgboost.readthedocs.io/en/latest/) is the state-of-the-art machine learning algorithm for supervised learning, and its most computational expensive implemmentation is written in **cpp**. However, It also provides the _interfaces_ (_packages_) for other languages, especially **Python** and **R**. Of coz, as a data scientist one usually needs to write the customized codes to adapt to the tasks, so he or she can balance the trade-offs and select which type of languages to go. In most of the time, such _two-language_ and _three-language_ problems often annoy the data scientists to code and debug, so nowadays ambitious developers try to develop smarter languages to make our lives easier. Interested audience can refer to [Julia](https://julialang.org/), which is ["_easy to write code that's nearly as fast as C_"](https://docs.julialang.org/en/v1/) 

Even **Python** and **R** are both _interpreted high-level programming languages_, but they indeed differ in many aspects of syntax. The detailed discussion will be left for your own practice. However, some historical issues related to their philosophy can be shared here. **Python** is the _general-purposed_ language, such that it is **NOT** designed for the specific direction for usage. However, developers from different areas join and contribute the communities, and with the help the the excellent packages Python is vastly applied in machine learning. On the other hand, **R** is designed for statistics and computation originally and currently it is extended to broader areas on machine learning. One simple example can illustrate this point. Suppose we generate a vector $$[1, 2, 3]$$ and then multiply each of its element by 3. In **R** interpreter, we can input

```r
c(1, 2, 3) * 3
```

then this piece of codes returns

```
[1] 3 6 9
```

However, in **Python** interpreter if we input

```python
[1, 2, 3] * 3
```

you will find that this returns

```
Out[1]: [1, 2, 3, 1, 2, 3, 1, 2, 3]
```

Strange, right? Yes, if we view this issue in terms of the element-wise vector calculation. However, as we know that **R** is dedicated to statistics and computation but **Python** is **NOT**, so it is easy to comprehend their different results. In **Python**, _list_ is the container to store the objects but **NOT** ready for computation as numeric vector. If we wanna replicate the same behavior as **R**, we can `import` the `numpy` package for help.

```python
import numpy as np
np.array([1, 2, 3]) * 3
```

then you will find the output:

```
Out[2]: array([3, 6, 9])
```

Actually, `np.array()` function just generates the one-dimensional array (numeric vector) from the given _list_ of $$[1, 2, 3]$$, which can be applied for the methods of numerical computation. With more and more examples, you will find that the _base_ **R** has involved build-in functions for statistics, computation, and data wrangling, while **Python** usually needs the additional packages to conduct the corresponding tasks. However, such issue cannot tell which is the winner but just the different philosophies. Nowadays, more and more data scientists are both the **Python** users and **R** users at the same time, and one can also find that the popular algorithms usually have both **Python** and **R** packages for use. If one still wanna check their pros and cons in data science, then I indeed can share my own experience. In terms of data wrangling, **Python** package `pandas` is more powerful than _base_ **R**, but **R** package `tidyverse` is as powerful as `pandas` and convenient to program (e.g. less lines of codes). In terms of the model training pipelines for machine learning, **R** package `tidymodels` can highly reflect the thoughts of statictical learning (e.g. [general workflows instead of narrow concept of models](https://www.tmwr.org/workflows.html)) and also inherit the convenient coding from `tidyverse`, but it is under development. However, **Python** package `scikit-learn` is relatively mature and powerful, but the application of this package requires careful organization of the training steps and is also more complex to code. In terms of deep learning, **Python** seems to be the winner mainly because the well-developed communities of `Tensorflow` and `PyTorch`. In terms of statistics and econometrics, **R** packages and **Python** packages nowadays can usually provide the similar functions, while **R** usually provides simpler syntax. Before diving into the happiness of the functions of brilliant **Python** and **R** packages, please also keep in mind that


{: .box-note}
Concept is the **base**, and programming is the **tool**


Once the concept is clear for the algorithms, one can code it in any language. Therefore, the first suggestion is that _please ask yourself what you are going to do before googling the key words_. Another suggestion is that just learn both **Python** and **R** and you will not lose.



## Projects and Environments




![managing envs for projects 1](https://raw.githubusercontent.com/AlfredSAM/medium_blogs/main/bridging_python_r/img/env1.png)

_Source: https://miro.medium.com/max/1263/1*RJXS5hapodrGXvmIBhUEEw.png_



![managing envs for projects 1](https://github.com/AlfredSAM/medium_blogs/blob/main/bridging_python_r/img/env2.png?raw=true)

*Source: https://nbisweden.github.io/excelerate-scRNAseq/logos/conda_illustration.png*






## Managing Conda Environments (Python)




### Python Scientific Libraries for Data Science





### Jupyter Lab








## Managing Conda Environments (R)



### R Packages Management



### Jupyter Lab Again



### Rstudio





## Summary




## References

* [A Quick and Easy Guide to Managing Conda Environments](https://towardsdatascience.com/a-quick-and-easy-guide-to-managing-conda-environments-87bfe7bab065)













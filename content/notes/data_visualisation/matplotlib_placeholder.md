---
title: "Matplotlib Placeholder"
subtitle: "A placeholder note for matplotlib chart basics."
author: "Cam"
date: 2021-01-06
description: "A placeholder note for matplotlib chart basics."
summary: "A placeholder note for matplotlib chart basics."
type: note
categories: ["Python", "Data Visualisation"]
tags: ["charts", "matplotlib"]
draft: false
---

{{< toc >}}

## Installation

To install `pip install matplotlib`

## Sample Chart

Here's a sample chart from the matplotlib gallery.


```python
# https://matplotlib.org/3.3.3/gallery/shapes_and_collections/scatter.html#sphx-glr-gallery-shapes-and-collections-scatter-py
%matplotlib inline
import numpy as np
import matplotlib.pyplot as plt

# Fixing random state for reproducibility
np.random.seed(19680801)


N = 50
x = np.random.rand(N)
y = np.random.rand(N)
colors = np.random.rand(N)
area = (30 * np.random.rand(N))**2  # 0 to 15 point radii

plt.scatter(x, y, s=area, c=colors, alpha=0.5)
plt.show()

```


![png](matplotlib_placeholder_3_0.png)


## References

- [venv Docs](https://docs.python.org/3/library/venv.html)
- [IPython Docs](https://ipython.readthedocs.io/en/stable/install/kernel_install.html)


```python
#Versions used in this notebook
import sys
print("OS:", sys.platform)

!python --version

from importlib.metadata import version
for library in ["jupyterlab", "matplotlib", "numpy"]:
    print(library, version(library))   
```

    OS: win32
    Python 3.9.1
    jupyterlab 2.2.0
    matplotlib 3.3.3
    numpy 1.19.5
    

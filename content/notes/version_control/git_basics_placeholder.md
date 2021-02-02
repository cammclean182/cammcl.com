---
title: "Git Basics Placeholder"
subtitle: "A placeholder note for git basics."
author: "Cam"
date: 2021-01-05
description: "A placeholder note for git basics."
summary: "A placeholder note for git basics."
type: note
categories: ["Python", "git"]
tags: ["data science", "git"]
draft: false
---

{{< toc >}}

## Installation

To install `pip install pandas`

## Sample Dataframe

Here's a sample chart from the matplotlib gallery.

Note need to make table border one in custom css? remove scroll bars? then looks good... increase spacing?


```python
import numpy as np
import pandas as pd
df = pd.DataFrame(np.random.randint(0,100,size=(100, 4)), columns=list('ABCD'))
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>57</td>
      <td>11</td>
      <td>19</td>
      <td>16</td>
    </tr>
    <tr>
      <th>1</th>
      <td>90</td>
      <td>64</td>
      <td>2</td>
      <td>76</td>
    </tr>
    <tr>
      <th>2</th>
      <td>97</td>
      <td>42</td>
      <td>88</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>72</td>
      <td>12</td>
      <td>79</td>
      <td>56</td>
    </tr>
    <tr>
      <th>4</th>
      <td>87</td>
      <td>49</td>
      <td>77</td>
      <td>65</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>95</th>
      <td>65</td>
      <td>62</td>
      <td>24</td>
      <td>77</td>
    </tr>
    <tr>
      <th>96</th>
      <td>45</td>
      <td>77</td>
      <td>23</td>
      <td>31</td>
    </tr>
    <tr>
      <th>97</th>
      <td>37</td>
      <td>65</td>
      <td>27</td>
      <td>28</td>
    </tr>
    <tr>
      <th>98</th>
      <td>41</td>
      <td>89</td>
      <td>72</td>
      <td>45</td>
    </tr>
    <tr>
      <th>99</th>
      <td>65</td>
      <td>0</td>
      <td>39</td>
      <td>22</td>
    </tr>
  </tbody>
</table>
<p>100 rows × 4 columns</p>
</div>




```python
display(df)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>57</td>
      <td>11</td>
      <td>19</td>
      <td>16</td>
    </tr>
    <tr>
      <th>1</th>
      <td>90</td>
      <td>64</td>
      <td>2</td>
      <td>76</td>
    </tr>
    <tr>
      <th>2</th>
      <td>97</td>
      <td>42</td>
      <td>88</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>72</td>
      <td>12</td>
      <td>79</td>
      <td>56</td>
    </tr>
    <tr>
      <th>4</th>
      <td>87</td>
      <td>49</td>
      <td>77</td>
      <td>65</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>95</th>
      <td>65</td>
      <td>62</td>
      <td>24</td>
      <td>77</td>
    </tr>
    <tr>
      <th>96</th>
      <td>45</td>
      <td>77</td>
      <td>23</td>
      <td>31</td>
    </tr>
    <tr>
      <th>97</th>
      <td>37</td>
      <td>65</td>
      <td>27</td>
      <td>28</td>
    </tr>
    <tr>
      <th>98</th>
      <td>41</td>
      <td>89</td>
      <td>72</td>
      <td>45</td>
    </tr>
    <tr>
      <th>99</th>
      <td>65</td>
      <td>0</td>
      <td>39</td>
      <td>22</td>
    </tr>
  </tbody>
</table>
<p>100 rows × 4 columns</p>
</div>



```python
print(df.to_markdown())
```

    |    |   A |   B |   C |   D |
    |---:|----:|----:|----:|----:|
    |  0 |  57 |  11 |  19 |  16 |
    |  1 |  90 |  64 |   2 |  76 |
    |  2 |  97 |  42 |  88 |   9 |
    |  3 |  72 |  12 |  79 |  56 |
    |  4 |  87 |  49 |  77 |  65 |
    |  5 |  44 |  25 |  84 |  71 |
    |  6 |  14 |   8 |  12 |  21 |
    |  7 |  56 |  82 |  82 |  74 |
    |  8 |  25 |   7 |  43 |  28 |
    |  9 |  37 |  88 |  61 |  10 |
    | 10 |   5 |   7 |  63 |  40 |
    | 11 |  28 |  71 |  80 |  95 |
    | 12 |  31 |  29 |  63 |  77 |
    | 13 |  88 |  69 |  87 |  47 |
    | 14 |  96 |  73 |  46 |  64 |
    | 15 |  74 |  94 |  64 |  63 |
    | 16 |   4 |   4 |  20 |  60 |
    | 17 |  70 |  68 |   6 |   0 |
    | 18 |  26 |  10 |  95 |  65 |
    | 19 |   8 |  80 |  94 |   2 |
    | 20 |  94 |  13 |  60 |  97 |
    | 21 |  26 |  41 |  29 |  69 |
    | 22 |  73 |  13 |  21 |  93 |
    | 23 |  41 |  46 |   7 |  86 |
    | 24 |  82 |  44 |  50 |  76 |
    | 25 |  29 |  13 |  66 |  16 |
    | 26 |  31 |  35 |  36 |  22 |
    | 27 |   1 |  12 |  12 |  42 |
    | 28 |  26 |  69 |  19 |  89 |
    | 29 |  35 |  29 |  16 |   4 |
    | 30 |  60 |  98 |  11 |  10 |
    | 31 |  79 |  96 |  35 |  45 |
    | 32 |  75 |  44 |  27 |  54 |
    | 33 |  73 |  13 |  62 |  70 |
    | 34 |  70 |  39 |  37 |  19 |
    | 35 |  77 |  32 |  35 |  44 |
    | 36 |  14 |  96 |  51 |  17 |
    | 37 |  82 |  68 |   6 |  62 |
    | 38 |  84 |  65 |  15 |   9 |
    | 39 |   0 |  48 |  99 |  33 |
    | 40 |  45 |  86 |   7 |  61 |
    | 41 |  45 |  25 |  44 |  25 |
    | 42 |  70 |  76 |  60 |  79 |
    | 43 |  40 |  48 |  24 |  54 |
    | 44 |  79 |  99 |  45 |  78 |
    | 45 |   5 |  52 |   9 |  48 |
    | 46 |  82 |  79 |  62 |  16 |
    | 47 |  20 |   0 |  42 |  51 |
    | 48 |  27 |  69 |   4 |  94 |
    | 49 |  76 |  65 |  10 |   9 |
    | 50 |  17 |  61 |  68 |  62 |
    | 51 |  51 |  42 |   4 |  58 |
    | 52 |  77 |  61 |  28 |  49 |
    | 53 |  16 |  33 |  25 |  46 |
    | 54 |  19 |  98 |  49 |  79 |
    | 55 |  63 |   1 |  70 |  25 |
    | 56 |  78 |  72 |  68 |  68 |
    | 57 |  14 |  76 |  81 |  11 |
    | 58 |   5 |  11 |  88 |  73 |
    | 59 |  73 |  76 |  50 |  64 |
    | 60 |  35 |  88 |  64 |  81 |
    | 61 |  74 |  16 |  17 |  50 |
    | 62 |  79 |  14 |  54 |  47 |
    | 63 |  17 |   1 |  29 |   6 |
    | 64 |  93 |  57 |  43 |  77 |
    | 65 |   5 |  39 |   8 |  37 |
    | 66 |  88 |  25 |  80 |  44 |
    | 67 |  44 |  74 |  55 |  85 |
    | 68 |  85 |  81 |  10 |  11 |
    | 69 |   7 |  74 |  83 |  42 |
    | 70 |  40 |  81 |  37 |  45 |
    | 71 |  49 |   1 |  71 |  35 |
    | 72 |   4 |  41 |  89 |  41 |
    | 73 |  31 |  13 |  55 |  72 |
    | 74 |  49 |  95 |  72 |  10 |
    | 75 |  63 |  69 |  91 |  42 |
    | 76 |  79 |  28 |  65 |  34 |
    | 77 |  34 |  81 |  45 |  92 |
    | 78 |   1 |  44 |  40 |  40 |
    | 79 |  90 |  26 |  37 |  57 |
    | 80 |   1 |  95 |   5 |  18 |
    | 81 |  67 |  50 |  45 |  16 |
    | 82 |   2 |  41 |  42 |  79 |
    | 83 |  75 |   5 |  15 |  82 |
    | 84 |  29 |  78 |  43 |   8 |
    | 85 |  91 |   8 |  97 |  39 |
    | 86 |  77 |  48 |  93 |  18 |
    | 87 |  91 |  15 |  31 |  80 |
    | 88 |  49 |  59 |  68 |  60 |
    | 89 |  31 |  55 |  55 |  90 |
    | 90 |  59 |   4 |   6 |  89 |
    | 91 |   2 |   6 |  90 |   0 |
    | 92 |  49 |  16 |  77 |  64 |
    | 93 |   3 |  17 |  70 |  65 |
    | 94 |  28 |  83 |   8 |  75 |
    | 95 |  65 |  62 |  24 |  77 |
    | 96 |  45 |  77 |  23 |  31 |
    | 97 |  37 |  65 |  27 |  28 |
    | 98 |  41 |  89 |  72 |  45 |
    | 99 |  65 |   0 |  39 |  22 |
    

## References

- [venv Docs](https://docs.python.org/3/library/venv.html)
- [IPython Docs](https://ipython.readthedocs.io/en/stable/install/kernel_install.html)


```python
#Versions used in this notebook
import sys
print("OS:", sys.platform)

!python --version

from importlib.metadata import version
for library in ["jupyterlab", "pandas", "numpy"]:
    print(library, version(library))   
```

    OS: win32
    Python 3.9.1
    jupyterlab 2.2.0
    pandas 1.2.0
    numpy 1.19.5
    


```python

```

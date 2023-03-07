---
jupyter:
  colab:
  kernelspec:
    display_name: Python 3
    name: python3
  language_info:
    name: python
  nbformat: 4
  nbformat_minor: 0
---

<div class="cell markdown" id="sOdE1_E3zURz">

CUHK-STAT1013: Practical Assignment Part 1: Sharing Your Idea and Data

</div>

<div class="cell markdown" id="9Fy05KAkyJI0">

## Golf Ball dataset background

**Description**:

Dataset describing the driving distances of current and new golf
balls.The testing was performed with a mechanical hitting machine so
that any difference between the mean distances for the two models could
be attributed to a difference in the design.

**Source**:
<https://www.kaggle.com/datasets/ipravin/golf-ball-testing-data-set-from-par-inc?resource=download>

**Sample size**: 40

**Feature documentation**:

| Feature | Class  | Dtype |
|:--------|:-------|:------|
| Current | Tensor | int64 |
| New     | Tensor | int64 |

</div>

<div class="cell markdown" id="k85zO7zxys4H">

## Hypothesis

-   Tell us what your idea is and why you have chosen to pursue this
    idea.
    -   We are interested in "*Does the new coating golf ball more
        durable than the current one?*"
-   What two groups you are comparing:
    -   **G1**: driving distance of current golf ball; **G2**: driving
        distance of new golf ball
-   What you will be measuring (i.e., what your response variable will
    be)
    -   `driving distance`
-   Is your response variable quantitative rather than categorical?
    -   `driving distance` is quantitative data, since it is seperated
        to `current` and `new` , which both are int64 type.
-   Make a prediction about what kind of difference you expect to see
    between your samples and WHY.
    -   We'd expect that **G2** \> **G1** since we would expect the
        coating for the new ball is effective and hence making the new
        ball more durable.
-   Talk about how you will gather your data
    -   From kaggle link:
        <https://www.kaggle.com/datasets/ipravin/golf-ball-testing-data-set-from-par-inc?resource=download>
-   If you had unlimited resources (time, money, staff, etc.) how would
    you collect your data?
    -   \(i\) perform the test more times by running the mechanical
        hitting machine ; (ii) investigate if anyother factors would
        affect the result eg.weather , quality of glass.

</div>

<div class="cell markdown" id="3GOdPWT03PQB">

## Prepare your dataset

</div>

<div class="cell code" execution_count="27"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:206}"
id="BZrIsqQrAzq4" outputId="ad559d38-774d-4ffc-a966-f827e57ac30b">

``` python
# load dataset from csv file
# upload the csv file to colab first
# install packages we need

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
df = pd.read_csv("/content/Golf.csv")
df.head(5)
```

<div class="output execute_result" execution_count="27">

       Current  New
    0      264  277
    1      261  269
    2      267  263
    3      272  266
    4      258  262

</div>

</div>

<div class="cell code" execution_count="22"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="agx2k1jeE-c9" outputId="604adb0f-b38b-4e1c-d138-6945649192fc">

``` python
# first 5 records of G1
df['Current'].head(5)
```

<div class="output execute_result" execution_count="22">

    0    264
    1    261
    2    267
    3    272
    4    258
    Name: Current, dtype: int64

</div>

</div>

<div class="cell code" execution_count="23"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="vbxsKb9cFM4X" outputId="a2f75008-259d-4d55-c22d-570955517eb6">

``` python
# first 5 records of G2
df['New'].head(5)
```

<div class="output execute_result" execution_count="23">

    0    277
    1    269
    2    263
    3    266
    4    262
    Name: New, dtype: int64

</div>

</div>

<div class="cell code" execution_count="25"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:300}"
id="cW0SjlgIFUJ2" outputId="84978139-14bb-403b-d1c7-edd9d34501b8">

``` python
#basic stat of G1 and G2
df.describe()
```

<div class="output execute_result" execution_count="25">

              Current         New
    count   40.000000   40.000000
    mean   270.275000  267.500000
    std      8.752985    9.896904
    min    255.000000  250.000000
    25%    263.000000  262.000000
    50%    270.000000  265.000000
    75%    275.250000  274.500000
    max    289.000000  289.000000

</div>

</div>

<div class="cell code" execution_count="39"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:279}"
id="_3EWoURHF9M1" outputId="58f44795-15a5-48e6-b596-4fdf7de0799e">

``` python
#visualization of G1
sns.violinplot(data=df, x='Current', bins='auto')
plt.xlabel("Driving distance of current ball")
plt.show()
```

<div class="output display_data">

![](a831934c4b3a17ebba04c15bbd98e9c69f375624.png)

</div>

</div>

<div class="cell code" execution_count="40"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:279}"
id="6JShOPwXITkY" outputId="e3b691b2-39f3-4271-a737-fdd6d91102b1">

``` python
#visualization of G2
sns.violinplot(data=df, x='New', bins='auto')
plt.xlabel("Driving distance of New ball")
plt.show()
```

<div class="output display_data">

![](7a31ee6202abbc9de79f8172f71c81de1b5b5cdc.png)

</div>

</div>

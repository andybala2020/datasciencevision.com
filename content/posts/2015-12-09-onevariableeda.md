---
title: 'Pseudo Facebook Data - Plots in Python'
slug: 'onevariableeda'
date: 2015-12-09
tags:
  - 'MachineLearning'
  - 'EDA'
  - 'Python'
  - 'DataScience'
categories:
  - 'Data Science'
template: post
thumbnail: '../thumbnails/notebook.png'
jupyter: true
---

In this post, we will learn about EDA of single variables using simple plots like [histograms], [frequency plots] and [box plots].

[histograms]: https://en.wikipedia.org/wiki/Histogram
[frequency plots]: https://www.khanacademy.org/math/pre-algebra/pre-algebra-math-reasoning/pre-algebra-frequency-dot-plot/v/frequency-tables-and-dot-plots
[box plots]: https://en.wikipedia.org/wiki/Box_plot

Data sets used below are part of a project from the UD651 course on [udacity](https://www.udacity.com/) by Facebook.
The data from the project corresponds to a typical data set at [Facebook](https://facebook.com). You can load the data through the following command. Notice that this is a `<TAB>` delimited _csv_ file. This data set consists of 99000 rows of data. We will see the details of different columns using the command below.

<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>

<span class="c1">#Read csv file</span>
<span class="n">pf</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;https://s3.amazonaws.com/udacity-hosted-downloads/ud651/pseudo_facebook.tsv&quot;</span><span class="p">,</span> <span class="n">sep</span> <span class="o">=</span> <span class="s1">&#39;</span><span class="se">\t</span><span class="s1">&#39;</span><span class="p">)</span>

<span class="c1">#summarize data</span>
<span class="n">pf</span><span class="o">.</span><span class="n">describe</span><span class="p">(</span><span class="n">include</span><span class="o">=</span><span class="s1">&#39;all&#39;</span><span class="p">,</span> <span class="n">percentiles</span><span class="o">=</span><span class="p">[])</span><span class="o">.</span><span class="n">T</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span><span class="s1">&#39; &#39;</span><span class="p">,</span> <span class="n">regex</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt"></div>

<div class="output_subarea output_stream output_stderr output_text">
<pre>/p/ret/rettools/AnacondaPython/Python35/lib/python3.5/site-packages/numpy/lib/function_base.py:3403: RuntimeWarning: Invalid value encountered in median
  RuntimeWarning)
</pre>
</div>
</div>

<div class="output_area">
<div class="prompt output_prompt">Out[1]:</div>

<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>count</th>
      <th>unique</th>
      <th>top</th>
      <th>freq</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>50%</th>
      <th>max</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>userid</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>1.59705e+06</td>
      <td>344059</td>
      <td>1.00001e+06</td>
      <td>1.59615e+06</td>
      <td>2.19354e+06</td>
    </tr>
    <tr>
      <th>age</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>37.2802</td>
      <td>22.5897</td>
      <td>13</td>
      <td>28</td>
      <td>113</td>
    </tr>
    <tr>
      <th>dob_day</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>14.5304</td>
      <td>9.01561</td>
      <td>1</td>
      <td>14</td>
      <td>31</td>
    </tr>
    <tr>
      <th>dob_year</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>1975.72</td>
      <td>22.5897</td>
      <td>1900</td>
      <td>1985</td>
      <td>2000</td>
    </tr>
    <tr>
      <th>dob_month</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>6.28337</td>
      <td>3.52967</td>
      <td>1</td>
      <td>6</td>
      <td>12</td>
    </tr>
    <tr>
      <th>gender</th>
      <td>98828.0</td>
      <td>2</td>
      <td>male</td>
      <td>58574</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th>tenure</th>
      <td>99001.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>537.887</td>
      <td>457.65</td>
      <td>0</td>
      <td></td>
      <td>3139</td>
    </tr>
    <tr>
      <th>friend_count</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>196.351</td>
      <td>387.304</td>
      <td>0</td>
      <td>82</td>
      <td>4923</td>
    </tr>
    <tr>
      <th>friendships_initiated</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>107.452</td>
      <td>188.787</td>
      <td>0</td>
      <td>46</td>
      <td>4144</td>
    </tr>
    <tr>
      <th>likes</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>156.079</td>
      <td>572.281</td>
      <td>0</td>
      <td>11</td>
      <td>25111</td>
    </tr>
    <tr>
      <th>likes_received</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>142.689</td>
      <td>1387.92</td>
      <td>0</td>
      <td>8</td>
      <td>261197</td>
    </tr>
    <tr>
      <th>mobile_likes</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>106.116</td>
      <td>445.253</td>
      <td>0</td>
      <td>4</td>
      <td>25111</td>
    </tr>
    <tr>
      <th>mobile_likes_received</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>84.1205</td>
      <td>839.889</td>
      <td>0</td>
      <td>4</td>
      <td>138561</td>
    </tr>
    <tr>
      <th>www_likes</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>49.9624</td>
      <td>285.56</td>
      <td>0</td>
      <td>0</td>
      <td>14865</td>
    </tr>
    <tr>
      <th>www_likes_received</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>58.5688</td>
      <td>601.416</td>
      <td>0</td>
      <td>2</td>
      <td>129953</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We need convert some of the variables from numeric to category.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">cats</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;userid&#39;</span><span class="p">,</span> <span class="s1">&#39;dob_day&#39;</span><span class="p">,</span> <span class="s1">&#39;dob_year&#39;</span><span class="p">,</span> <span class="s1">&#39;dob_month&#39;</span><span class="p">]</span>
<span class="k">for</span> <span class="n">col</span> <span class="ow">in</span> <span class="n">pf</span><span class="o">.</span><span class="n">columns</span><span class="p">:</span>
    <span class="k">if</span> <span class="n">col</span> <span class="ow">in</span> <span class="n">cats</span><span class="p">:</span>
        <span class="n">pf</span><span class="p">[</span><span class="n">col</span><span class="p">]</span> <span class="o">=</span> <span class="n">pf</span><span class="p">[</span><span class="n">col</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s1">&#39;category&#39;</span><span class="p">)</span>

<span class="c1">#summarize data</span>
<span class="n">pf</span><span class="o">.</span><span class="n">describe</span><span class="p">(</span><span class="n">include</span><span class="o">=</span><span class="s1">&#39;all&#39;</span><span class="p">,</span> <span class="n">percentiles</span><span class="o">=</span><span class="p">[])</span><span class="o">.</span><span class="n">T</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span><span class="s1">&#39; &#39;</span><span class="p">,</span> <span class="n">regex</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt"></div>

<div class="output_subarea output_stream output_stderr output_text">
<pre>/p/ret/rettools/AnacondaPython/Python35/lib/python3.5/site-packages/numpy/lib/function_base.py:3403: RuntimeWarning: Invalid value encountered in median
  RuntimeWarning)
</pre>
</div>
</div>

<div class="output_area">
<div class="prompt output_prompt">Out[2]:</div>

<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>count</th>
      <th>unique</th>
      <th>top</th>
      <th>freq</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>50%</th>
      <th>max</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>userid</th>
      <td>99003.0</td>
      <td>99003</td>
      <td>2.19354e+06</td>
      <td>1</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th>age</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>37.2802</td>
      <td>22.5897</td>
      <td>13</td>
      <td>28</td>
      <td>113</td>
    </tr>
    <tr>
      <th>dob_day</th>
      <td>99003.0</td>
      <td>31</td>
      <td>1</td>
      <td>7900</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th>dob_year</th>
      <td>99003.0</td>
      <td>101</td>
      <td>1995</td>
      <td>5196</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th>dob_month</th>
      <td>99003.0</td>
      <td>12</td>
      <td>1</td>
      <td>11772</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th>gender</th>
      <td>98828.0</td>
      <td>2</td>
      <td>male</td>
      <td>58574</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th>tenure</th>
      <td>99001.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>537.887</td>
      <td>457.65</td>
      <td>0</td>
      <td></td>
      <td>3139</td>
    </tr>
    <tr>
      <th>friend_count</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>196.351</td>
      <td>387.304</td>
      <td>0</td>
      <td>82</td>
      <td>4923</td>
    </tr>
    <tr>
      <th>friendships_initiated</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>107.452</td>
      <td>188.787</td>
      <td>0</td>
      <td>46</td>
      <td>4144</td>
    </tr>
    <tr>
      <th>likes</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>156.079</td>
      <td>572.281</td>
      <td>0</td>
      <td>11</td>
      <td>25111</td>
    </tr>
    <tr>
      <th>likes_received</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>142.689</td>
      <td>1387.92</td>
      <td>0</td>
      <td>8</td>
      <td>261197</td>
    </tr>
    <tr>
      <th>mobile_likes</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>106.116</td>
      <td>445.253</td>
      <td>0</td>
      <td>4</td>
      <td>25111</td>
    </tr>
    <tr>
      <th>mobile_likes_received</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>84.1205</td>
      <td>839.889</td>
      <td>0</td>
      <td>4</td>
      <td>138561</td>
    </tr>
    <tr>
      <th>www_likes</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>49.9624</td>
      <td>285.56</td>
      <td>0</td>
      <td>0</td>
      <td>14865</td>
    </tr>
    <tr>
      <th>www_likes_received</th>
      <td>99003.0</td>
      <td></td>
      <td></td>
      <td></td>
      <td>58.5688</td>
      <td>601.416</td>
      <td>0</td>
      <td>2</td>
      <td>129953</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The goal of this analysis is to understand user behavior and their demographics. We want to understand what they are doing on the Facebook and what they use. Please note this is not a real Facebook dataset.</p>
<p>Our goal is to do some basic EDA (Exploratory Data Analysis) to understand any underlying patterns in the data.
We will first look at a histogram of User's Birthdays.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[3]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>
<span class="n">sns</span><span class="o">.</span><span class="n">set</span><span class="p">(</span><span class="n">style</span><span class="o">=</span><span class="s2">&quot;darkgrid&quot;</span><span class="p">)</span>
<span class="o">%</span><span class="k">matplotlib</span> inline

<span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">countplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;dob_day&quot;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">pf</span><span class="p">)</span>

</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt"></div>

<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
Q0REov1/0v42Du8/k9YAAAAASUVORK5CYII=
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We see some peculiar behavior of the data on the 1st of the month. Let us plot this data in more detail, in per month basis.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">g</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">factorplot</span><span class="p">(</span><span class="s2">&quot;dob_day&quot;</span><span class="p">,</span> <span class="n">col</span><span class="o">=</span><span class="s2">&quot;dob_month&quot;</span><span class="p">,</span> <span class="n">col_wrap</span><span class="o">=</span><span class="mi">4</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">pf</span><span class="p">,</span> <span class="n">kind</span><span class="o">=</span><span class="s1">&#39;count&#39;</span><span class="p">,</span> <span class="n">size</span><span class="o">=</span><span class="mf">2.5</span><span class="p">,</span> <span class="n">aspect</span><span class="o">=.</span><span class="mi">8</span><span class="p">)</span>
<span class="n">g</span><span class="o">.</span><span class="n">set</span><span class="p">(</span><span class="n">xticklabels</span><span class="o">=</span><span class="p">[])</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt output_prompt">Out[4]:</div>

<div class="output_text output_subarea output_execute_result">
<pre>&lt;seaborn.axisgrid.FacetGrid at 0x7fffcd441208&gt;</pre>
</div>

</div>

<div class="output_area">
<div class="prompt"></div>

<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>This explains the above plot. Because of the default settings, or users privacy concerns, numerous people have 1/1 as their birthdays!</p>
<p>Now, let us explore the distribution of friend counts in this data.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[5]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">pf</span><span class="p">[</span><span class="s2">&quot;friend_count&quot;</span><span class="p">],</span> <span class="n">kde</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">bins</span><span class="o">=</span><span class="mi">100</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlim</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">1000</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt output_prompt">Out[5]:</div>

<div class="output_text output_subarea output_execute_result">
<pre>(0, 1000)</pre>
</div>

</div>

<div class="output_area">
<div class="prompt"></div>

<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We see the data has some outliers near 5000. This is an example of a long tail data. We want our analysis to be focused on the bunch of Facebook users, so we need to limit the axes of these plots. Additionally, we also want to look at these data as a function of gender. However, We also want to remove any data where gender is NA.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[6]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span> <span class="o">=</span> <span class="n">pf</span><span class="p">[</span><span class="n">pf</span><span class="o">.</span><span class="n">gender</span><span class="o">.</span><span class="n">notnull</span><span class="p">()]</span>
<span class="n">g</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">FacetGrid</span><span class="p">(</span><span class="n">df</span><span class="p">,</span> <span class="n">col</span><span class="o">=</span><span class="s2">&quot;gender&quot;</span><span class="p">)</span>
<span class="n">g</span> <span class="o">=</span> <span class="n">g</span><span class="o">.</span><span class="n">map</span><span class="p">(</span><span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">,</span> <span class="s2">&quot;friend_count&quot;</span><span class="p">,</span> <span class="n">bins</span><span class="o">=</span><span class="mi">100</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="s2">&quot;b&quot;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlim</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">1000</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt output_prompt">Out[6]:</div>

<div class="output_text output_subarea output_execute_result">
<pre>(0, 1000)</pre>
</div>

</div>

<div class="output_area">
<div class="prompt"></div>

<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
SUVORK5CYII=
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>If we want to know, mean statistics of our data, we can use the 'value_counts' command.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[164]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pf</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="s1">&#39;gender&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">friend_count</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt output_prompt">Out[164]:</div>

<div class="output_text output_subarea output_execute_result">
<pre>gender
female  count    40254.000000
        mean       241.969941
        std        476.039706
        min          0.000000
        25%         37.000000
        50%         96.000000
        75%        244.000000
        max       4923.000000
male    count    58574.000000
        mean       165.035459
        std        308.466702
        min          0.000000
        25%         27.000000
        50%         74.000000
        75%        182.000000
        max       4917.000000
Name: friend_count, dtype: float64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let us know look at the tenure of usage (measured in Years) of Facebook.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[8]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span> <span class="o">=</span> <span class="n">pf</span><span class="p">[</span><span class="n">pf</span><span class="o">.</span><span class="n">tenure</span><span class="o">.</span><span class="n">notnull</span><span class="p">()]</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s2">&quot;tenure&quot;</span><span class="p">]</span><span class="o">/</span><span class="mi">365</span><span class="p">,</span> <span class="n">kde</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">bins</span><span class="o">=</span><span class="mi">36</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlim</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">7</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Number of years using Facebook&#39;</span><span class="p">,</span> <span class="n">fontsize</span><span class="o">=</span><span class="mi">12</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of users in sample&#39;</span><span class="p">,</span> <span class="n">fontsize</span><span class="o">=</span><span class="mi">12</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt output_prompt">Out[8]:</div>

<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.text.Text at 0x7fffc9590ef0&gt;</pre>
</div>

</div>

<div class="output_area">
<div class="prompt"></div>

<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We will now look at any pattern in the ages of Facebook users in this dataset.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[9]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">pf</span><span class="p">[</span><span class="s2">&quot;age&quot;</span><span class="p">],</span> <span class="n">kde</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">bins</span><span class="o">=</span><span class="mi">100</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlim</span><span class="p">(</span><span class="mi">13</span><span class="p">,</span><span class="mi">113</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">&#39;Age of Users in Years&#39;</span><span class="p">,</span> <span class="n">fontsize</span><span class="o">=</span><span class="mi">12</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;Number of users in sample&#39;</span><span class="p">,</span> <span class="n">fontsize</span><span class="o">=</span><span class="mi">12</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt output_prompt">Out[9]:</div>

<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.text.Text at 0x7fffc94f7780&gt;</pre>
</div>

</div>

<div class="output_area">
<div class="prompt"></div>

<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
AABJRU5ErkJggg==
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>One general theme of observation here is that most of the data have a long tail. In these circumstances, it is better to look at such data after certain types of transformation. Let us do such an analysis of “friend_count”.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[35]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">pf</span><span class="p">[</span><span class="s2">&quot;friend_count&quot;</span><span class="p">],</span> <span class="n">kde</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">hist_kws</span><span class="o">=</span><span class="p">{</span><span class="s2">&quot;alpha&quot;</span><span class="p">:</span> <span class="mf">0.9</span><span class="p">})</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt"></div>

<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[49]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">pf</span><span class="p">[</span><span class="s2">&quot;friend_count&quot;</span><span class="p">],</span> <span class="n">kde</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">bins</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">logspace</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">4</span><span class="p">),</span> <span class="n">hist_kws</span><span class="o">=</span><span class="p">{</span><span class="s2">&quot;alpha&quot;</span><span class="p">:</span> <span class="mf">0.9</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xscale</span><span class="p">(</span><span class="s1">&#39;log&#39;</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt"></div>

<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
AAAAAElFTkSuQmCC
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Let us try to compare distribution of male vs female friend counts.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[175]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">plotDensity</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="kc">None</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="kc">None</span><span class="p">,</span> <span class="n">bins</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">linspace</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">1000</span><span class="p">,</span><span class="mi">200</span><span class="p">),</span> <span class="o">**</span><span class="n">kws</span><span class="p">):</span>

<div>
    <span class="n">w</span> <span class="o">=</span> <span class="mi">100</span><span class="o">*</span><span class="n">np</span><span class="o">.</span><span class="n">ones_like</span><span class="p">(</span><span class="n">x</span><span class="p">)</span><span class="o">/</span><span class="n">x</span><span class="o">.</span><span class="n">size</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">bins</span><span class="o">=</span><span class="n">bins</span><span class="p">,</span> <span class="n">alpha</span><span class="o">=</span><span class="mf">0.4</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;step&#39;</span><span class="p">,</span> <span class="n">linewidth</span><span class="o">=</span><span class="mi">2</span><span class="p">,</span> <span class="n">label</span><span class="o">=</span><span class="n">label</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">color</span><span class="p">,</span> <span class="n">weights</span><span class="o">=</span><span class="n">w</span><span class="p">,</span> <span class="o">**</span><span class="n">kws</span><span class="p">)</span>
    <span class="k">return</span>
</div>

<span class="n">g</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">FacetGrid</span><span class="p">(</span><span class="n">df</span><span class="p">,</span> <span class="n">col</span><span class="o">=</span><span class="kc">None</span><span class="p">,</span> <span class="n">hue</span><span class="o">=</span><span class="s1">&#39;gender&#39;</span><span class="p">,</span> <span class="n">size</span><span class="o">=</span><span class="mf">6.0</span><span class="p">,</span> <span class="n">xlim</span><span class="o">=</span><span class="p">(</span><span class="mi">6</span><span class="p">,</span><span class="mi">600</span><span class="p">),</span> <span class="n">ylim</span><span class="o">=</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">5</span><span class="p">),</span> <span class="n">legend_out</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">g</span> <span class="o">=</span> <span class="p">(</span><span class="n">g</span><span class="o">.</span><span class="n">map</span><span class="p">(</span><span class="n">plotDensity</span><span class="p">,</span> <span class="s1">&#39;friend_count&#39;</span><span class="p">))</span><span class="o">.</span><span class="n">add_legend</span><span class="p">()</span>
<span class="n">g</span> <span class="o">=</span> <span class="n">g</span><span class="o">.</span><span class="n">set_axis_labels</span><span class="p">(</span><span class="s1">&#39;Friend Count&#39;</span><span class="p">,</span> <span class="s1">&#39;</span><span class="si">% o</span><span class="s1">f users&#39;</span><span class="p">)</span>

</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt"></div>

<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAgAAAAGoCAYAAAAw313kAAAABHNCSVQICAgIfAhkiAAAAAlwSFlz
AAALEgAACxIB0t1+/AAAIABJREFUeJzt3XeYLOdB5/tvdU6Tz5yZk4PCK1mykm0J24Btgok2S7hc
coYHHu/F964X7mKC4WG5C0sy7AIXGzCwD1zsNbsEL7B4DTZ4vbZlyZIlWXp1pJPD5JmezqGq7h/V
0z19Jupoenpm6vd5Hj3qqq6uevuVzqlfv/UGx/d9REREJFwi/S6AiIiI7D4FABERkRBSABAREQkh
BQAREZEQUgAQEREJIQUAERGREIr1+gLGmItAHvCAhrX24V5fU0RERDbX8wBAcON/o7V2cReuJSIi
ItuwG48AnF26joiIiGzTbtyYfeDDxphHjTE/uAvXExERkS3sRgB4vbX2IeCrgbcZY75wF64pIiIi
m3B2cy0AY8y7gIK19tc2OqbZdP1YLLprZRIRkX3P6XcB9qOedgI0xmSAiLW2aIzJAm8Gfm6zzywu
lntZpD1tfHyA2dlCv4uxJ6guOlQXHaqLDtVFx/j4QL+LsC/1ehTABPBfjTF+61p/Yq39+x5fU0RE
RLbQ0wBgrb0APNDLa4iIiMhLp+F5IiIiIaQAICIiEkIKACIiIiGkACAiIhJCCgAiIiIhpAAgIiIS
QgoAIiIiIaQAICIiEkIKACIiIiGkACAiIhJCCgAiIiIhpAAgIiISQgoAIiIiIaQAICIiEkIKACIi
IiGkACAiIhJCCgAiIiIhpAAgIiISQgoAIiIiIaQAICIiEkIKACIiIiGkACAiIhJCCgAiIiIhpAAg
IiISQgoAIiIiIaQAICIiEkIKACIiIiGkACAiIhJCCgAiIiIhpAAgIiISQgoAIiIiIaQAICIiEkIK
ACIiIiGkACAiIhJCCgAiIiIhpAAgIiISQgoAIiIiIaQAICIiEkIKACIiIiGkACAiIhJCCgAiIiIh
pAAgIiISQgoAIiIiIaQAICIiEkIKACIiIiGkACAiIhJCCgAiIiIhpAAgIiISQgoAIiIiIaQAICIi
EkIKACIiIiGkACAiIhJCCgAiIiIhpAAgIiISQgoAIiIiIaQAICIiEkIKACIiIiGkACAiIhJCCgAi
IiIhpAAgIiISQgoAIiIiIaQAICIiEkKxfhfgZr7vt187jtPHkoiIiBxcey4AfOzJ6+3XrzwzxthQ
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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Similarly, we can compare distributions of <em>www</em> likes.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[179]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">g</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">FacetGrid</span><span class="p">(</span><span class="n">df</span><span class="p">,</span> <span class="n">col</span><span class="o">=</span><span class="kc">None</span><span class="p">,</span> <span class="n">hue</span><span class="o">=</span><span class="s1">&#39;gender&#39;</span><span class="p">,</span> <span class="n">size</span><span class="o">=</span><span class="mf">6.0</span><span class="p">,</span> <span class="n">xlim</span><span class="o">=</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">15000</span><span class="p">))</span>
<span class="n">g</span> <span class="o">=</span> <span class="p">(</span><span class="n">g</span><span class="o">.</span><span class="n">map</span><span class="p">(</span><span class="n">plotDensity</span><span class="p">,</span> <span class="s1">&#39;www_likes&#39;</span><span class="p">,</span> <span class="n">bins</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">logspace</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">5</span><span class="p">,</span><span class="mi">50</span><span class="p">)))</span><span class="o">.</span><span class="n">add_legend</span><span class="p">()</span>
<span class="n">g</span> <span class="o">=</span> <span class="n">g</span><span class="o">.</span><span class="n">set_axis_labels</span><span class="p">(</span><span class="s1">&#39;www Likes Count&#39;</span><span class="p">,</span> <span class="s1">&#39;</span><span class="si">% o</span><span class="s1">f users&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xscale</span><span class="p">(</span><span class="s1">&#39;log&#39;</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt"></div>

<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
AElFTkSuQmCC
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We cal also look at the total number of likes numerically per gender, as follows:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[173]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pf</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="s1">&#39;gender&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">www_likes</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt output_prompt">Out[173]:</div>

<div class="output_text output_subarea output_execute_result">
<pre>gender
female    3507665
male      1430175
Name: www_likes, dtype: int64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can also compare two distributions graphically using “box plots”. We can also look at the actual value using the by command. Here, we are trying to understand which gender initiated more friendships.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[185]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">boxplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s1">&#39;gender&#39;</span><span class="p">,</span> <span class="n">y</span><span class="o">=</span><span class="s1">&#39;friendships_initiated&#39;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylim</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">200</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt output_prompt">Out[185]:</div>

<div class="output_text output_subarea output_execute_result">
<pre>(0, 200)</pre>
</div>

</div>

<div class="output_area">
<div class="prompt"></div>

<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
FVEAAAAASUVORK5CYII=
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[186]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pf</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="s1">&#39;gender&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">friendships_initiated</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt output_prompt">Out[186]:</div>

<div class="output_text output_subarea output_execute_result">
<pre>gender
female  count    40254.000000
        mean       113.899091
        std        195.139308
        min          0.000000
        25%         19.000000
        50%         49.000000
        75%        124.750000
        max       3654.000000
male    count    58574.000000
        mean       103.066600
        std        184.292570
        min          0.000000
        25%         15.000000
        50%         44.000000
        75%        111.000000
        max       4144.000000
Name: friendships_initiated, dtype: float64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Next, we want to understand if users have used certain features of Facebook or not. If we look at the summary of mobile_likes variable, median is close to 0, indicating a lot many users with 0 values for this variable. We can look also look at the logical value if value of this quantity is non-zero. We can additionally create a new variable called mobile_check_in that takes a value 1 if mobile_likes is non-zero.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[187]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pf</span><span class="o">.</span><span class="n">mobile_likes</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt output_prompt">Out[187]:</div>

<div class="output_text output_subarea output_execute_result">
<pre>count    99003.000000
mean       106.116300
std        445.252985
min          0.000000
25%          0.000000
50%          4.000000
75%         46.000000
max      25111.000000
Name: mobile_likes, dtype: float64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[201]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="p">(</span><span class="n">pf</span><span class="o">.</span><span class="n">mobile_likes</span> <span class="o">&gt;</span> <span class="mi">0</span><span class="p">)</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt output_prompt">Out[201]:</div>

<div class="output_text output_subarea output_execute_result">
<pre>True     63947
False    35056
Name: mobile_likes, dtype: int64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[200]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pf</span><span class="p">[</span><span class="s1">&#39;mobile_check_in&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">where</span><span class="p">(</span><span class="n">pf</span><span class="p">[</span><span class="s1">&#39;mobile_likes&#39;</span><span class="p">]</span> <span class="o">&gt;</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">0</span><span class="p">))</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s1">&#39;category&#39;</span><span class="p">)</span>
<span class="n">pf</span><span class="o">.</span><span class="n">mobile_check_in</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt output_prompt">Out[200]:</div>

<div class="output_text output_subarea output_execute_result">
<pre>1    63947
0    35056
Name: mobile_check_in, dtype: int64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can find percentage of people who have done mobile check in.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[203]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">frac</span> <span class="o">=</span> <span class="p">(</span><span class="n">pf</span><span class="o">.</span><span class="n">mobile_check_in</span> <span class="o">==</span> <span class="mi">1</span><span class="p">)</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span><span class="o">/</span><span class="n">pf</span><span class="o">.</span><span class="n">mobile_check_in</span><span class="o">.</span><span class="n">size</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Fraction of Mobile Check-ins = &quot;</span><span class="p">,</span> <span class="n">frac</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt"></div>

<div class="output_subarea output_stream output_stdout output_text">
<pre>Fraction of Mobile Check-ins =  0.645909719907
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We find that about 65% of people have used mobile devices for check in and hence it would be a good decision to continue development of such products.</p>
<p>In summary, here we have learned to make inferences about single variable data using a combination of plots - histograms, box plots and frequency plots; along with various numerical data.</p>

</div>
</div>
</div>

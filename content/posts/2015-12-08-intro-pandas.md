---
title: 'Reddit Survey: Introduction to Pandas'
slug: 'intro-pandas'
date: 2015-12-08
tags:
  - 'EDA'
  - 'Python'
  - 'DataScience'
categories:
  - 'Data Science'
template: post
thumbnail: '../thumbnails/notebook.png'
jupyter: true
---

The data set used here is part of a project from [UD651](https://www.udacity.com/course/data-analysis-with-r--ud651) course on [udacity](https://www.udacity.com/) by [Facebook](https://www.facebook.com).

The data from the project corresponds to a survey from [reddit.com](https://reddit.com). You can load the data through the following command. We will first look at the different attributes of this data using the `summary()` and `describe()` [pandas](https://pandas.pydata.org) methods.

<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[45]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>

<span class="c1">#Read csv file</span>
<span class="n">reddit</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;https://s3.amazonaws.com/udacity-hosted-downloads/ud651/reddit.csv&quot;</span><span class="p">)</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="nb">object</span><span class="p">)</span>
<span class="c1">#summarize data</span>
<span class="n">reddit</span><span class="o">.</span><span class="n">describe</span><span class="p">(</span><span class="n">include</span><span class="o">=</span><span class="s1">&#39;all&#39;</span><span class="p">,</span> <span class="n">percentiles</span><span class="o">=</span><span class="p">[])</span><span class="o">.</span><span class="n">T</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">nan</span><span class="p">,</span><span class="s1">&#39; &#39;</span><span class="p">,</span> <span class="n">regex</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt output_prompt">Out[45]:</div>

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
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>id</th>
      <td>32754.0</td>
      <td>32754.0</td>
      <td>32756</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>gender</th>
      <td>32553.0</td>
      <td>2.0</td>
      <td>0</td>
      <td>26418.0</td>
    </tr>
    <tr>
      <th>age.range</th>
      <td>32666.0</td>
      <td>7.0</td>
      <td>18-24</td>
      <td>15802.0</td>
    </tr>
    <tr>
      <th>marital.status</th>
      <td>32749.0</td>
      <td>6.0</td>
      <td>Single</td>
      <td>10428.0</td>
    </tr>
    <tr>
      <th>employment.status</th>
      <td>32603.0</td>
      <td>6.0</td>
      <td>Employed full time</td>
      <td>14814.0</td>
    </tr>
    <tr>
      <th>military.service</th>
      <td>32749.0</td>
      <td>2.0</td>
      <td>No</td>
      <td>30526.0</td>
    </tr>
    <tr>
      <th>children</th>
      <td>32535.0</td>
      <td>2.0</td>
      <td>No</td>
      <td>27488.0</td>
    </tr>
    <tr>
      <th>education</th>
      <td>32610.0</td>
      <td>7.0</td>
      <td>Bachelor's degree</td>
      <td>11046.0</td>
    </tr>
    <tr>
      <th>country</th>
      <td>32577.0</td>
      <td>439.0</td>
      <td>United States</td>
      <td>20967.0</td>
    </tr>
    <tr>
      <th>state</th>
      <td>20846.0</td>
      <td>52.0</td>
      <td>California</td>
      <td>3401.0</td>
    </tr>
    <tr>
      <th>income.range</th>
      <td>31139.0</td>
      <td>8.0</td>
      <td>Under $20,000</td>
      <td>7892.0</td>
    </tr>
    <tr>
      <th>fav.reddit</th>
      <td>28393.0</td>
      <td>1833.0</td>
      <td>askreddit</td>
      <td>2123.0</td>
    </tr>
    <tr>
      <th>dog.cat</th>
      <td>32749.0</td>
      <td>3.0</td>
      <td>I like dogs.</td>
      <td>17151.0</td>
    </tr>
    <tr>
      <th>cheese</th>
      <td>32749.0</td>
      <td>11.0</td>
      <td>Other</td>
      <td>6563.0</td>
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
<p>The describe() method helped us get an overview of all the data available to us. We also ensured that all the data read was a categorical data.</p>
<p>Let us look at the age.range variable in more detail. We can look at the different levels of this variables using the cat.categories property of a Pandas Series.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[46]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">reddit</span><span class="p">[</span><span class="s2">&quot;age.range&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s1">&#39;category&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">cat</span><span class="o">.</span><span class="n">categories</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">
<div class="prompt output_prompt">Out[46]:</div>

<div class="output_text output_subarea output_execute_result">
<pre>Index([&#39;18-24&#39;, &#39;25-34&#39;, &#39;35-44&#39;, &#39;45-54&#39;, &#39;55-64&#39;, &#39;65 or Above&#39;, &#39;Under 18&#39;], dtype=&#39;object&#39;)</pre>
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
<p>This shows there are 7 possible values of this variable and some where no data is available (NA).</p>
<p>A more pictorial view of this can be seen using a histogram plot of this.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[57]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>
<span class="n">sns</span><span class="o">.</span><span class="n">set</span><span class="p">(</span><span class="n">style</span><span class="o">=</span><span class="s2">&quot;darkgrid&quot;</span><span class="p">)</span>
<span class="o">%</span><span class="k">matplotlib</span> inline

<span class="n">newOrder</span> <span class="o">=</span> <span class="p">[</span><span class="s2">&quot;Under 18&quot;</span><span class="p">,</span> <span class="s2">&quot;18-24&quot;</span><span class="p">,</span> <span class="s2">&quot;25-34&quot;</span><span class="p">,</span> <span class="s2">&quot;35-44&quot;</span><span class="p">,</span> <span class="s2">&quot;45-54&quot;</span><span class="p">,</span> <span class="s2">&quot;55-64&quot;</span><span class="p">,</span> <span class="s2">&quot;65 or Above&quot;</span><span class="p">]</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">countplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;age.range&quot;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">reddit</span><span class="p">,</span> <span class="n">order</span><span class="o">=</span><span class="n">newOrder</span><span class="p">)</span>

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
<p>Similarly, we can also plot a distribution of income range.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[51]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">countplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;income.range&quot;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">reddit</span><span class="p">)</span>
<span class="n">locs</span><span class="p">,</span> <span class="n">labels</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">()</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">plt</span><span class="o">.</span><span class="n">setp</span><span class="p">(</span><span class="n">labels</span><span class="p">,</span> <span class="n">rotation</span><span class="o">=</span><span class="mi">90</span><span class="p">)</span>
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
XP8fdQsga2ibF5cAAAAASUVORK5CYII=
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
<p>One problem with the above plots is that the different levels are not ordered. This can be fixed using ordered Factors, instead of regular factor type variables. Additionally, We need to use a more reasonable x-label for plotting income.range.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[52]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">newLevels</span> <span class="o">=</span> <span class="p">[</span><span class="s2">&quot;100K&quot;</span><span class="p">,</span> <span class="s2">&quot;&gt;150K&quot;</span><span class="p">,</span> <span class="s2">&quot;20K&quot;</span><span class="p">,</span><span class="s2">&quot;30K&quot;</span><span class="p">,</span> <span class="s2">&quot;40K&quot;</span><span class="p">,</span> <span class="s2">&quot;50K&quot;</span><span class="p">,</span> <span class="s2">&quot;70K&quot;</span><span class="p">,</span> <span class="s2">&quot;&lt;20K&quot;</span><span class="p">]</span>
<span class="n">reddit</span><span class="p">[</span><span class="s2">&quot;income.range&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="n">reddit</span><span class="p">[</span><span class="s2">&quot;income.range&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">astype</span><span class="p">(</span><span class="s1">&#39;category&#39;</span><span class="p">)</span>
<span class="n">reddit</span><span class="p">[</span><span class="s2">&quot;income.range&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="n">reddit</span><span class="p">[</span><span class="s2">&quot;income.range&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">cat</span><span class="o">.</span><span class="n">rename_categories</span><span class="p">(</span><span class="n">newLevels</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[55]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">newOrder</span> <span class="o">=</span> <span class="p">[</span><span class="s2">&quot;&lt;20K&quot;</span><span class="p">,</span> <span class="s2">&quot;20K&quot;</span><span class="p">,</span><span class="s2">&quot;30K&quot;</span><span class="p">,</span> <span class="s2">&quot;40K&quot;</span><span class="p">,</span> <span class="s2">&quot;50K&quot;</span><span class="p">,</span> <span class="s2">&quot;70K&quot;</span><span class="p">,</span> <span class="s2">&quot;100K&quot;</span><span class="p">,</span> <span class="s2">&quot;&gt;150K&quot;</span><span class="p">]</span>
<span class="n">ax</span> <span class="o">=</span> <span class="n">sns</span><span class="o">.</span><span class="n">countplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;income.range&quot;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">reddit</span><span class="p">,</span> <span class="n">order</span><span class="o">=</span><span class="n">newOrder</span><span class="p">)</span>
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
rkJggg==
"
>
</div>

</div>

</div>
</div>

</div>

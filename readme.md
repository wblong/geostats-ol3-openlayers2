geostats 地统计
========================


[geostats](http://www.intermezzo-coop.eu/mapping/geostats/) is a tiny standalone JS library for classification released by [Simon Georget](http://www.intermezzo-coop.eu/)  under MIT license. 

Other contributors : [Doug Curl](http://kgs.uky.edu/kgsmap/ukengage/) (Jenks algorithm), [Casey Thomas](http://cpt.ph/), [Dreamind](https://github.com/dreamind), [cricri](https://github.com/cricri)


It currently supports
--------------

- equal intervals  等间隔
- quantiles 分位数
- standard deviation 标准差
- arithmetic progression 等差数级
- geometric progression 等比数级
- jenks (natural breaks) 最佳自然断裂法
- uniques values 唯一值
- user defined classification 用户定义分类

and **few statistical methods**

To use it, just download the geostats package and include the following line into your html page :

```html
   <script type="text/javascript" src="path/to/lib/geostats.min.js"></script>
```

**Please see the samples page to understand how it works!**

API
========================

Attributes : 属性
--------------

- *serie* : contains the statistic population. Default : empty. 统计对象集合
- *separator* : used to separate ranges values, by default : ' - ' 分隔符（Legend图例中的分隔符）
- *legendSeparator* : by default, equals to *separator* value
- *method* : give information regarding the classification method used. Default : empty. 分级方法（见上）
- *bounds* : classification bounds 分级边界数组 [0, 67827, 1067285, 5416945, 18642586, 1312978855]
- *ranges* : classification ranges 分级数组 ["0 - 67827", "67827 - 1067285", "1067285 - 5416945", "5416945 - 18642586", "18642586 - 1312978855"]
- *colors* : classification colors 分级颜色数组 ["#333399", "#333399", "#333399", "#333399", "#333399"]
- *debug* : default value `false`. When set to `true` , provide useful debug message regarding objects and properties. 打开调试
- *silent* :  default value `false`. If silent, do no trigger alert() message when inputs are incorrects but display console.log() messages  打开警告消息提示


Methods : 方法
---------


**Statistics :**

- *min()* : return the min value 最小值
- *max()* : return the max value 最大值
- *sum()* : return the sum of the population 求和
- *pop()* : return the number of individuals 总个数
- *mean()* : return the mean 平均值
- *median()* : return the median 中位数
- *variance()* : return the variance 方差
- *stddev()* : return the standard deviation 标准差
- *cov()* : return the coefficient of variation 变异系数，离散系数 stddev/mean


**Classification :**

- *getClassEqInterval(nbClass)* : Perform an equal interval classification and return bounds into an array. Alias : *getEqInterval(nbClass)*  执行等间隔分级
- *getClassStdDeviation(nbClass)* : Perform a standard deviation classification and return bounds into an array. Alias : *getStdDeviation(nbClass)* 执行标准差分级 （正太分布）
- *getClassArithmeticProgression(nbClass)* : Perform an arithmetic progression classification and return bounds into an array. Alias : *getArithmeticProgression(nbClass)* 等差分级
- *getClassGeometricProgression(nbClass)* : Perform a geometric progression classification and return bounds into an array. Alias : *getGeometricProgression(nbClass)* 等比分级
- *getClassQuantile(nbClass)* : Perform a quantile classification and return bounds into an array. Alias : *getQuantile(nbClass)*  按分位数分级
- *getClassJenks(nbClass)* : Perform a Jenks classification and return bounds into an array. Alias : *getJenks(nbClass)* 最佳自然分级
- *getClassUniqueValues()* : Perform a unique values classification and return bounds (values) into an array. Alias : *getUniqueValues()* 唯一值分级
- *setClassManually()* : Set a user defined classification based on passed array (Same array is returned). Useful to automatically set bounds/ranges and generate legend. 自定义分级



**Constructor methods :** 

- *setSerie()* : fill up the *serie* attribute 设置统计对象
- *setColors()* : fill up the *colors* attribute 设置颜色数组
- *setPrecision()* : set precision on serie - only useful for float series. Can take no value (for automatic precision), or an integer between 0-20. By default, the precision will be computed automatically by *geostats*. 设置精度


**Getters methods :**

- *getRanges(array)* : return an array of classes range (*ranges* value) 获取分级
- *getRangeNum()* : return the number/index of this.ranges that value falls into 获取分级数
- *getHtmlLegend(colors, legend, callback, mode, order)* : return a legend in html format. Please refer [to code comment](https://github.com/simogeo/geostats/blob/master/lib/geostats.js#L735) to know how about option.  获取HTML图例
- *getSortedlist()* : return the sorted serie in text format 获取分级排序后的数据
- *getClass()* : return a given value class 获取指定分级


**Internals methods :** 私有方法

- *_nodata()* : check if *serie* attribute if not empty 
- *_hasNegativeValue()* : check if the serie contains any negative values
- *_hasZeroValue()* : check if the serie contains zero values
- *sorted()* : return the sorted (asc) serie
- *info()* : return information about the population in text format 
- *setRanges()* : fill up the *ranges* attribute (array of classes range)
- *doCount()* : perform count feature by classes, used to display count feature in legend 


*Note : If you are looking for a nice JS library to format numbers for displaying, just rely on [numeraljs](http://numeraljs.com/).*

 
MIT LICENSE
========================
 
 Copyright (c) 2011 Simon Georget

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

 

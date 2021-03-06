# Tools for Implementation
## Introduction
There are many ways to implement a chart for a web application. This document will attempt to review some of the tool out there and thier pros and cons. The main requirment of this project is for this application to be delivered over the web, because of this we will largly look at the 2 main ways of generating content on the web, server side vs browser side rendering and their respective tool, pros and cons.

## Overview of Server Side Rendering vs Browser Side Rendering
When it comes to the web this distinction of how content will be delivered and rendered has a very strong influence of what any web application can do. As such I will spend some time reviewing their differences. 

Server side rendering is how all the web operated for a very long time. When the web was born the only thing browsers understood was HTML, a static markup language. When a user would visit a site like www.somesite.com somewhere a web server is waiting, the user is making a "request." The server on the other end is responsible for serving up the request. That means that there is some code that figures out what the request is asking for, then generates all the HTML *WITH* the relevent data the user requested and sends it the whole package to the user. Every time a user makes a new request the whole page, all the html is generated by the server and then sent to the user's browser to be fully re-redered.

Browser side rendering came about basically with the inclusion of javascrip in browsers becuase there browsers now had a programming languge with logic they could interpurt. This allowed for things to become dynamic and change without reloading the whole page. 

Let's use an addition calculator to as an example to highlight some of their differences. Imagine a page with 2 number inputs and a submit button that returns the sum of the 2 numbers.
```
 ----------     -----------
|          | + |            | = *get result button*
 ----------     -----------

SUM!
```
For a SSR page for the SUM value to change the server needs to recive a sum request with the 2 input values then calculate the sum and then regenerate the HTML of the page with the new summed value.

For a BSR page this calculation can be done by the browser and the value on the page can be updated virtually instantlly. This has saved round trip to the server is huge.


## Overview with project in mind
I'd like to look at the two main ways of generating content in the context of this project since there are uses for both.

SSR gives you more control over the data. Less of the raw data has to be sent to the user's browser, ie the user only see's a server rendered image of a chart vs a data object that gets rendered by the browser. User rights and managment, ie who can see what and when is simpified if all the data on the page is rendered and controlled by the server. Finally expensive database quereies or computations can be handled by the server.

BSR gives you fluid and dynamic UI's and UX's. You can make thing interactive. For example make use of ajax requests to render additional data or transform charts based on an action by user. 

## SSR languages and tools
We will moslty look at the tooling and ecosystem (libraries and packages) available and relevent to this project of creating charts. Tooling are things like package managers, ide support, build/testing management. 

As I am most familiar with PHP and it's ecosystem I will focus mainly on it. There are many other good programming languages that are designed for the web such as Python, ruby, C# + .net, java, and recently Go lang but I will only breifly highlight them. In my view with the exception of Go lang they are equally good in the most genral sense. The reason I exclude Go lang is that it's relativly new and it's ecosystem and tooling is still quite lacking. 


### PHP
Is a mature programming language that is super simple to get up and running. Has a whole host of rich IDE' like phpStorm or netBeans support and a package manager [composer](https://getcomposer.org/
) to help manage dependencies.

Ecosystem
* [Charts](https://github.com/ConsoleTVs/Charts)
    - A wrapper for generating charts using any of the main charting libraries
    - Common api if you decide to change charting libraries
    - good documentation
    - CON: need to learn another api
    - CON: might be more difficult to customize or do something outside the scope of the package.
* [JPGraphs](http://jpgraph.net/doc/)
    - PHP driven static charts
    - pretty good documentation
    - CON: default styling looks old
* [ObHighchartsBundle](https://github.com/marcaube/ObHighchartsBundle)
    - Highcharts wrapper
* [snappy](https://github.com/KnpLabs/snappy)
    - HTML to PDF Generator


### Python
Also mature langue with lots of good tooling like pip for packages, and pycharm as an ide. Great tools for scientific use like charting and analysis. 

Ecosystem
* [Jupyter](https://ipython.org/)
    - An interactive shell
* [rpy2](http://rpy2.readthedocs.io/en/version_2.8.x/)
    - An interface between python and r
    - good documentation
    - CON: need to know r as well
* [plotly](https://plot.ly/python/)
    - Looks very powerful
    - Generates online graphs
    - might be paid
* many more

### Others
Java and C# probably both have their libraries and tools but I don't have any familiarity with them.

## BSR tools and language
When it comes to the browser there's only javascrip the tooling is quite robust with many IDE's and several package mangers (npm and grunt). 

Ecosystem
Since there are so many charting libraries out there for javascrip I am including a [chart](https://en.wikipedia.org/wiki/Comparison_of_JavaScript_charting_frameworks) that compares them
    * Chartsjs
    - Focus only on charting making it easier to use
    * D3
    - a full visulization tool that does much more than just generate charts

Javascript frameworks
Depending on how much interactivity is required a framework might help keeping the code orginized and keep from having to revent the "wheel."
* [React](https://facebook.github.io/react/)
* [vuejs](https://vuejs.org/)
    - Have used quite extensivally
    - great framework that doesn't need to be an all or nothing deal unlike the others
* [angularjs](https://angularjs.org/)

## Conclusion
With the present project requirments in mind using either python and a ipython notebook or vuejs wrapping some charting library would make the most sense. For either of these solutions to work we are making the assumption that the data whole data set will be available to the user (indirectly). 
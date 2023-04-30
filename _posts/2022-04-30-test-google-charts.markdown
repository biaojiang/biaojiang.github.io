---
layout: post
title:  "Test Google charts in Jekyll markdown post!"
date:   2023-04-30 09:14:00 +0200
categories: data-science
math: false 
---

## Google Charts
[Google Charts](https://developers.google.com/chart) creates impressive interactive charts for browsers and mobile devices. We can also deploy it as a Cloud micro-service, e.g., web app, Cloud Run, etc.

Some common use cases for Google Charts include:

1. Creating charts and visualizations for websites or web applications: Google Charts can be easily integrated into web pages or applications to provide data visualizations that are dynamic and interactive.

1. Creating reports and dashboards: Google Charts can be used to create standalone reports or embedded within larger dashboards or reporting environments.

1. Exploring data in Jupyter Notebooks: Google Charts can be used within Jupyter Notebooks to explore and analyze data interactively.

1. Creating custom visualizations for specific use cases: Google Charts offers a wide range of customization options, allowing users to create custom visualizations that meet specific needs.

### Google Charts vs. Matplotlib
As for using Matplotlib instead of Google Charts, it really depends on the specific use case and requirements. Matplotlib is a popular Python library for creating static and dynamic charts and visualizations and can be a good choice for more specialized or complex visualization needs. However, it may not be as easy to use or integrate with web-based applications as Google Charts.

## Examples
### Pie chart
We can embed a Google Chart in the markdown file by using an HTML <iframe> tag:

<iframe width="600" height="400" src="https://chart.googleapis.com/chart?cht=p3&chd=t:60,40&chs=250x100&chl=Hello|World"></iframe>

This will display a simple pie chart with the labels "Hello" and "World".
* "cht=p3": specifies the chart type as a 3D pie chart
* "chd=t:60,40": specifies the data values for the chart, in this case two values of 60 and 40
* "chs=250x100": specifies the size of the chart as 250 pixels wide and 100 pixels tall
* "chl=Hello|World": specifies the labels for each value in the chart, in this case "Hello" and "World"
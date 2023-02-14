---
layout: post
title:  "Data plotlib in Golang!"
date:   2022-12-27 17:30:00 +0100
categories: data-science
math: true
---

## Motivative
[The Go Programming Language](https://go.dev) is much faster than Python, and the syntax is in a modern design. I got familiar with Go by implementing the acoustic array beamforming modules. Initially, the results were exported to plot in Python, but it was not convenient. Therefore, finding a way to directly plot the high-quality figures in Go could improve the development efficiency later. 

## Plot in Go

The plotlib is developed on the top of [gonum/plot](https://pkg.go.dev/gonum.org/v1/plot). The `marker` defined in other plotting libraries, e.g., matplotlib, is named `points` in gonum. To implement a function similar to `imshow,` we need to use `heatmap.`


### Interface between the plotlib and the main function

* Line plotting struct
{% highlight go %}
// Line structure
type Line struct {
	P         *plot.Plot
	XYs       []plotter.XYs // XY data
	Width     float64
	Height    float64
	Color     []string
	Xlabel    string
	Ylabel    string
	Title     string
	Figname   string
	GridOn    bool
	PointsOn  []bool // add points/markers
	LineWidth []float64
	Ticks     []float64
	Legend    []string
	LegendPos struct{ Left, Top bool } // legned position
}
{% endhighlight %}

* Plotting
{% highlight go %}
var plt plotlib.Plt = &line
plt.AddDataXY(&x_data, &y_data)
plt.Plot()
{% endhighlight %}

* Save figure
{% highlight go %}
plt.SaveFig()
{% endhighlight %}


### Result
1. Line and point/marker plotting

Narrowband beamforming of a 16-element array was simulated, and the resulting beampatterns for two different windowing functions are compared as follows:

{:center-img: style="text-align: center;"}
![narrowband beamforming](/images/narrowbeam_win_cmp.svg){: height="480px" width="640px" title="narrowband beamforming comparing two windows"}
{:center-img}

2. Scatter plotting
[Iris flower data set](!https://en.wikipedia.org/wiki/Iris_flower_data_set) was used to test the Golang machine learning performance. The data feature distribution was visualized with scatter plotting:

{:center-img: style="text-align: center;"}
![iris sepal length vs. width](/images/iris_scatter_sepal.svg){: height="480px" width="640px" title="iris sepal length vs. width"}
{:center-img}

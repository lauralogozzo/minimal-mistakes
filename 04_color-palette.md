---
layout: single
title: Color Palette
permalink: /Color-Palette/
header:
  overlay_image: "/assets/images/myCols-All.svg"

---
A set of functions to display the available color palettes (see plotCols) and to load a color
palette into your global environment (see getCols).

<h3> Load Functions into Global Environment </h3>
<pre>
  <code>
source("https://lauralogozzo.github.io/assets/myCols.R.txt")
  </code>
</pre>	

<h3> Documentation </h3>

Function to display the available color palettes, and their names:
<pre>
  <code>
plotCols(
  group = ""
)
  </code>
</pre>

<html>
<head>
<style>
table, th, td {
}

th, td {
  padding: 20px;
}
</style>
</head>
<body>

<table style="width:700px" padding = "3px">
  <tr>
    <td><b><font size = 2 style="font-family: Menlo">
    group
    </font></b></td>
    
    <td><font size = 2 style="font-family: Menlo">
    "categorical" or "ramp" specifies the available color palettes in that type to display.
    Defaults to "", which displays both types of color palettes.
    </font></td>
  </tr>
</table>

<br>

Function to pull the desired color palette by name:
<pre>
  <code>
getCols(
  x = NULL
  num = length(eval(parse(text=x)))
)
  </code>
</pre>

<html>
<head>
<style>
table, th, td {
}

th, td {
  padding: 20px;
}
</style>
</head>
<body>

<table style="width:700px" padding = "3px">
  <tr>
    <td><b><font size = 2 style="font-family: Menlo">
    x
    </font></b></td>
    
    <td><font size = 2 style="font-family: Menlo">
    The color palette name to pull. See plotCols() for available palettes.
    </font></td>
  </tr>
  
  <tr>
    <td><b><font size = 2 style="font-family: Menlo">
    num 
    </font></b></td>
    
    <td><font size = 2 style="font-family: Menlo">
    The number of colors to pull from the desired palette. Defaults to the entire palette.
    </font></td>
  </tr>
</table>

<h3> Examples </h3>
An example of a palette for categorical data in <em>ggplot</em>:
<pre>
  <code>
# Load ggplot
library('ggplot2')

# Creates a global environment object named 'myCols' that contains the chosen palette
myCols <- getCols("nausicaa")

# Get iris data
data(iris)

# Ggplot example
ggplot(data=iris, aes(Petal.Length,Sepal.Length, color = Species)) +
  geom_point(size = 2)+
  scale_color_manual(values = myCols) +
  theme_classic()

  </code>
</pre>

An example of a gradient palette for continuous data in <em>ggplot</em>:
<pre>
  <code>
# Load ggplot
library('ggplot2')

# Get color palette
myCols <- getCols("sunset")

# Plot continuous scale
ggplot(data=iris, aes(Petal.Length,Sepal.Length, color = Petal.Width)) +
  geom_point(size = 2) +
  scale_color_gradientn(colors = rev(myCols)) +
  theme_classic()

  </code>
</pre>


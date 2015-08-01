---
layout: post
title: Microwave Circuit Design
category: Software
tags: KLayout Python
---

## CPW Design

I've developed a collection of KLayout macros to help with CPW design. 

### Make CPW from Path

**Files**

* [Make CPW.py](https://github.com/calebjordan/klayout-macros/pymacros/Make CPW.py)

Draw a traces as paths, select them, and run this. A 10um wide CPW will be drawn in layer 1/0, and a 4um keepout will be drawn in layer 1/6. These polygons will have rounded ends, so you'll have to trim them with some other boolean operations. I'll probably make macros for that as well. 

### Calculate Frequency of CPW

**Files**

* [cpw_design.py](https://github.com/calebjordan/klayout-macros/pymacros/cpw_design.py)

### Make Ground Straps

**Files**

* [Make Ground Straps.py](https://github.com/calebjordan/klayout-macros/pymacros/Make Ground Straps.py)

Select the path along which you would like to place ground straps and run. It should place regularly spaced paths for grounding straps. Soon 

## FastHenry Tools

Some tools to help with the impressively difficult to use FastHenry. You'll need fasthenry3.0 available on your path. 

### Run Shapes in FastHenry

**Files**

* [fasthenry.py](https://github.com/calebjordan/klayout-macros/pymacros/fasthenry.py)
* [Run in FastHenry.py](https://github.com/calebjordan/klayout-macros/pymacros/Run in FastHenry.py)

This will create an input file based on selected paths, will call FastHenry on the file, and display the results (the output text) in a dialog box. A eventually have a better way to display the data. 

**Important** You need to give your paths names, so they can be appropriately labeled in the input file, and you know how to interpret the results. 

* Select the path
* Press 'q'
* Click the 'User Properties' button
* Add a new Property
	- Key: '1' **with quotes**. GDS standard only allows numeric property keys. Pretty dumb.
	- Value: 'Name' **without quotes, alphanumeric**. FastHenry requires alphanumeric labels.

The nodes names will contain the path name, so you can tell which row of the output matrix corresponds to which path.
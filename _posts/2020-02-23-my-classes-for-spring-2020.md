---
layout: post
title: My Classes for Spring 2020
date: 2020-02-23
description: what classes I took for my 4th (and final) semester of grad school
permalink: /blog/my-classes-for-spring-2020
toc:
  sidebar: left
thumbnail: assets/img/header_fall2018classes.jpg
categories: MSLIS
---

This is it - the last semester of my MS/LIS degree. As I am currently job searching, I decided to take a slightly lighter class load for this final semester: 2 regular classes, 1 short class, and an independent study. Here they are:

- IS532: Theory & Practice of Data Cleaning
- IS590PZ: Data Structures & Algorithms - Puzzles & Games
- IS590SC: Introduction to Command Line Tools
- IS592: Independent Study

Note that the course descriptions & learning outcomes are pulled from the syllabi for each respective course.

## IS532: Theory & Practice of Data Cleaning

While I have encountered a lot of the topics covered in this class in previous classes (e.g. Regular Expressions, the Relational Model), this is still a must-take class at the iSchool. I have actually been meaning to take this class for a while, but because it is reliably offered every semester, I kept putting it of to take other classes. This class teaches several concepts important to data curation (e.g. data provenance, reproducibility), and includes some new topics that are quite exciting to me - like logic programming (Datalog) and workflow automation.

### Course Description

> Data cleaning (also: cleansing) is the process of assessing and improving data quality for later analysis and use, and is a crucial part of data curation and analysis. This course identifies data quality issues throughout the data lifecycle, and reviews specific techniques and approaches for checking and improving data quality. Techniques are drawn primarily from the database community, using schema-level and instance-level information, and from different scientific communities, which are developing practical tools for data pre-processing and cleaning.

### Learning Objectives

- Understand how to detect and flag data quality problems.
- Understand principles of data and information modeling.
- Understand techniques that support automated data curation and cleaning.

### Key Topics

- Introduction to Data Quality and Data Cleaning
- Syntactic Issues and Regular Expressions
- Hands-on Data Cleaning with OpenRefine... ​and optionally with R or Python
- Logic-Based Integrity Constraints in ​Datalog & ​SQL
- Workflow Automation and Modeling
- From Workflows to Data Provenance and Reproducibility

## IS590PZ: Data Structures & Algorithms - Puzzles & Games

This is a new class at the iSchool (this semester is the 2nd time it has been offered). The goal of the class is to teach students about data structures and algorithms in a fun and interesting way... through puzzles and games. Each week we are given a new puzzle or game that we have to represent in some kind of data structure and then solve based on a specific algorithmic approach. Many of the projects are done in groups, although some can also be completed individually. This class is challenging and fast-paced, but also highly rewarding because it pushes me to advance my python problem solving skills. Also, as a huge fan of puzzles and games, this class is just intrinsically interesting.

### Course Description

> Learn, experiment, code with, and compare performance of common data structures and algorithms in a fun, collaborative, and challenging context. In class, students will discuss and solve logic puzzles and play several types of strategy games. In small teams they will explore the deductive, strategic, and tactical decisions involved, select appropriate data structures & algorithms to develop efficient program solutions to automate playing, solving, generating, or analyzing puzzles & games. Techniques and tools used include analysis of efficiency (Big-O), recursion, minimax, Monte Carlo Tree Search, client/server network communications, deterministic vs non-deterministic algorithms.  Structures used include arrays, matrices, hash tables, stacks, various trees, network graphs, and custom structures.  For some projects, students will have competitions pitting their solutions against other teams

### Learning Objectives

Though the contextual focus of the course is on strategic games and logic puzzles, the underlying purpose is for students to learn and practice the following critical and broadly-useful skills:

- logical and analytical thinking and problem solving
- use of performance analysis techniques as one aspect of comparing similar solutions/algorithms
- understand how data structures and algorithms are interdependent and make suitable choices accordingly
- practical coding ability using data structures and concepts listed in the course description above.

## IS590SC: Introduction to Command Line Tools

This is a one-month short course offered at the end of the semester. It covers many of the vital skills often glossed over in typical programming classes - like version control, shell scripting, and computer cluster/cloud tools.

### Course Description

This class will provide an overview of the history and commonly offered command line interfaces and essential shell scripting tools. These approaches will be extended to cover common version control tools, including git and GitHub, their value, and how to appropriately organize a project within them. We will also review how to submit projects to the Illinois Campus Cluster tool, and touch on situations where it may be valuable to do so.

### Textbook

<br>
**"The Linux Command Line"** (2nd ed), by William Shotts
{: .small}

[Available online here](http://linuxcommand.org/tlcl.php){: .btn .btn--primary}

## IS592: Independent Study

I decided to do an independent study this semester because I wanted to learn how to analyze data using python packages that are typically used for data science projects. Last semester, I learned how to perform statistical analyses in R (IS542) and how to use various machine learning algorithms for data mining in WEKA (IS590DT). However, the language that I am most comfortable with - and use for data wrangling - is python, and I have yet to learn how to apply the concepts I learned in those previous classes to the python data science ecosystem. I also want to learn how to do time-series analysis - something that neither of those previous classes covered.

This independent study is also functioning as a follow up to another class I took last semester, Open Data Mashups (IS590OM). The goal of that class was to produce a new analysis-ready dataset that combined data from other open data sources. I created a country-year time-series dataset that combined data from the Correlates of War project, the UCDP/PRIO Armed Conflict dataset, the World Bank's World Development Indicators, and the Polity IV project. For my independent study, I will be analyzing this dataset in a variety of ways, implementing the statistical learning techniques I learned last semester in python.

### Resources

<br>
**"Introduction to Machine Learning with Python"** (2016), by Andreas Müller and Sarah Guido
{: .small}

[Available here](https://learning.oreilly.com/library/view/introduction-to-machine/9781449369880/){: .btn .btn--primary}

**"Python for Data Analysis"** (2017), by Wes McKinney
{: .small}

[Available here](https://learning.oreilly.com/library/view/python-for-data/9781491957653/){: .btn .btn--primary}

**"Python Data Science Handbook"** (2017), by Jake VanderPlas
{: .small}

[Available here](https://jakevdp.github.io/PythonDataScienceHandbook/){: .btn .btn--primary}

**"Machine Learning"** MOOC by Andrew Ng
{: .small}

[Available here](https://www.coursera.org/learn/machine-learning/home/info){: .btn .btn--primary}

---
layout: post
title: My Classes for Fall 2019
date: 2019-09-29
description: what classes I took for my 3rd semester of grad school
permalink: /blog/my-classes-for-fall-2019
toc:
  sidebar: left
thumbnail: assets/img/header_fall2018classes.jpg
categories: MSLIS
---

One year down, one year to go! During the first year of my MSLIS degree, I focused on the fundamentals: how to organize and process data. This year, I am shifting my focus to analysis. This semester I am taking three classes focused on different ways to analyze data, as well as one project-oriented class that will allow me to collect together the data I want to analyze.

- IS542: Data, Statistical Models, and Information
- IS590DV: Data Visualization
- IS590DT: Data Mining
- IS590OM: Open Data Mashups

Note that the course descriptions, themes, learning outcomes and such are pulled from the syllabi for each respective course.

## IS542: Data, Stats, & Info

This is an introduction to statistics for information professionals - it covers the fundamental concepts of statistical analysis and how to perform those analyses in base R using RStudio.

### Course Description

> An	introduction	to	statistical	and	probabilistic	models that	are used	to	quantify	information,	assess information quality,	and	make	decisions	in a	principled	way.	The	increasing	prevalence	of	massive	data	sets	and	falling computational	barriers	have	rendered	statistical	modeling	an	integral	part	of	contemporary	information	management.	With	this	in	mind,	this	class	prepares	students	to	select	and	properly	undertake	common	modeling	tasks.	The	course	reviews	relevant	results	from	probability	theory,	emphasizing	the	merits	and	limitations	of	familiar	probability	distributions	as	vehicles	for	modeling	information.	Subsequent	consideration	includes	parametric	and	non-parametric	predictive	models,	as	well	as	extensions	of	these	models	for	unsupervised	learning.	Throughout	these	discussions,	the	course	focuses	on	model	selection	and	gauging	model	quality.	Applications	of	statistical	and	probabilistic	models	to	tasks	in	information	management	(e.g.	prediction,	ranking,	and	data	reduction)	are	emphasized.

### Learning Outcomes

- Explain	the	role	of	marginal,	joint,	and	conditional	probability	in	modeling	processes	involving	information.
- Select,	parameterize,	and	compare	probability	distributions	as	vehicles	for	modeling	information.
- Specify,	estimate	and	evaluate	elementary parametric	and	non-parametric statistical	models.
- Articulate	the	responsibilities	of	a	professional	who	creates,	describe,	or	uses	models	of	data.

### Textbooks

<br>
**"An	Introduction	to	Statistical	Learning: with Applications in R"** (2013), by Gareth James, Daniela Witten, Trevor Hastie and Robert Tibshirani
{: .small}

[Author's Site](http://faculty.marshall.usc.edu/gareth-james/ISL/){: .btn .btn--primary}

**"OpenIntro Statistics"** (3rd ed)
{: .small}

[Publisher's Site, free download](https://www.openintro.org/stat/textbook.php?stat_book=os){: .btn .btn--primary}

**"An Introduction to R"** (3rd ed), Venables,	W.N.,	Smith,	D.M	and	the	R	Core	Team
{: .small}

[Full Document](http://cran.r-project.org/doc/manuals/R-intro.pdf){: .btn .btn--primary}

## IS590DV: Data Visualization

One of the most popular classes in the iSchool, this class is all about data visualization. The class mostly focuses on python libraries, and each class has both a lecture that deep-dives on one particular aspect of visualization as well as live code-alongs.

### Course Description

> Data visualization is crucial to conveying information drawn from models, observations or investigations. This course will provide an overview of historical and modern techniques for visualizing data, drawing on quantitative, statistical, and network-focused datasets. Topics will include construction of communicative visualizations, the modern software ecosystem of visualization, and techniques for aggregation and interpretation of data through visualization. Particular attention will be paid to the Python ecosystem and multi-dimensional quantitative datasets.

### Central Themes

1. What are the components of an effective visualization of quantitative data?
2. What tools and ecosystems are available for visualizing data?
3. What systems can be put in place to generate visualizations rapidly and with high-fidelity representation?

### Course Website

Lecture slides and Jupyter notebooks from the code-alongs are available on the course's GitHub website.

[IS590DV Fall 2019 Website](https://uiuc-ischool-dataviz.github.io/fall2019/){: .btn .btn--primary}

## IS590DT: Data Mining

While IS542 focuses on the more traditional methods of statistical analysis, this class focuses on modern methods of extracting information from large data. Techniques for classification, clustering, and prediction are taught using [WEKA](https://www.cs.waikato.ac.nz/ml/weka/), a free software for machine learning.

### Course Description

> Data mining refers to the process of exploring large datasets with the goal of uncovering interesting patterns. This process usually involves a number of tasks such as data collection, pre-processing, and characterization; model fitting, selection, and evaluation; classification, clustering, and prediction. Although data mining has its roots in database management, it has grown into a discipline that focuses on algorithm design (to ensure computational feasibility) and statistical modeling (to separate the signal from the noise). As such, it draws heavily upon a variety of other disciplines including statistics, machine learning, operations research, and information retrieval. This course will cover the major data mining concepts, principles, and techniques that *every information scientist should know about.* Lectures will introduce and discuss the major approaches to data mining, computer lab sessions coupled with assignments will provide hands-on experience with these approaches, and term projects offer the opportunity to use data mining in a novel way. Mathematical detail will be left to the students who are so inclined.

### Course Objectives

1. To gain a broad exposure to data mining concepts and principles through lectures and discussion.
2. To develop a working proficiency in selected data mining techniques through lab sessions, hands-on assignments, and office hours.
3. To nurture the ability to detect opportunities to apply data mining concepts, principles and techniques in new scenarios by independent exploration of resources beyond the course materials, and, optionally, through a course project.

### Textbook

<br>
**"Data Mining: Practical Machine Learning Tools and Techniques"** (4th ed), by I.H. Witten, E. Frank, M.A. Hall, and C.J. Pal
{: .small}

[Book via ScienceDirect](https://doi.org/10.1016/C2015-0-02071-8){: .btn .btn--primary}

#### Data

Data used for the course is available through the professor's website.

[Data](http://abel.lis.illinois.edu/data/){: .btn .btn--primary}

## IS590OM: Open Data Mashups

The entire point of this class is to produce a new dataset that combines multiple other open data sources. The project is the class - with some career planning and development sprinkled in along the way. The end goal is to have a project for your portfolio, and the tools to use that project when applying for jobs - think elevator pitch, cover letter, resume, presentation, etc. As an added bonus, you have an interesting dataset ready and waiting for analysis.

### Course Description

> Data sharing and modern open data standards have been creating large repositories of data that remain disconnected. Many data science and machine learning techniques are boosted by incorporating data representing a variety of domains and granularities. Topics on data curation, data cleaning, copyright, web scraping, storage, processing, and automation will be reviewed. This course seeks to explore techniques and perspectives of combining various data sources to create a dataset ready for analysis, but in a project oriented space so that each topic is synthesized with practice and experienced in context. Students will select a project area and explore the technical and conceptual requirements of that project space, eventually producing a proof of concept around it. All project domains and areas are open, with the only requirement being that they combine several data sources into a new dataset. This course is meant for students who have completed at least two semesters of coursework, are comfortable with programming in Python (the project can be completed in any language, but instruction will be in Python), and desire a space to explore and develop a capstone or independent study project. However, further work on the project is not a requirement. Guest speakers and field experts from the University Library will be invited. Students will be encouraged to share and publish their datasets at the end of the semester.

### Learning Goals

1. Identify and assess relevant data sources for a research project
2. Process, clean, and quality check datasets
3. Combine multiple datasets into one for an analysis process
4. Produce quality dataset and project documentation
5. Effectively deliver various types of project pitches
6. Write effective conference talk proposals
7. Provide constructive peer feedback and peer reviews
8. Receive and interpret peer feedback

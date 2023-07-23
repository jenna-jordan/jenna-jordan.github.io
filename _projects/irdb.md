---
layout: page
category: Grad School
importance: 1
title: "International Relations Database"
permalink: /projects/irdb
description: "These inter-related projects were completed as final projects for coursework during my MSLIS degree, and were aimed at improving the data resources for political scientists working in Peace/Conflict research."
img: /assets/img/project_irdbhome.jpg
github: https://github.com/jenna-jordan/international-relations-database-extended
---

Although I went to school for Library and Information Science, the specific domain that I am interested in applying my skills to is political science - in particular, the international relations and conflict resolution subfields. Many of the classes that I have taken during my MSLIS conclude with open-ended final projects, in which you can apply the skills you have learned to the domain of your choice. I used these final projects to improve the data resources available to political scientists and Peace/Conflict researchers.

## Fall 2018 through Spring 2019

During my first semester, I took a [class on databases](/blog/my-classes-for-fall-2018#is490db-introduction-to-databases)  and a [class on python](/blog/my-classes-for-fall-2018#is452-foundations-of-information-processing). Both classes concluded with a final project of our own devising. I merged those two final projects into one: designing and creating the database that incorporated most of the Correlates of War Project datasets and then transforming and loading the data into the database using python.

For the database half of the project, I designed a database schema (and created the EER diagram), and then wrote a SQL script to create the database that contains, connects, and describes the disparate datasets published by the [Correlates of War project](http://www.correlatesofwar.org/). However, this only covers the creation of the tables and their referential integrity. The python half of the project involved writing scripts (using the Pandas library) to transform the CSV files into SQL insert statements. The transformation process ended up revealing several data quality issues, and the process of integrating the four War datasets was much more complicated than I initially thought.

Together, both sides of the project resulted in a [Github repo](https://github.com/jenna-jordan/international-relations-database) that contains the necessary scripts to allow anyone to create and fill the database on their own machine.

## Fall 2019

During my third semester, I took a project-based class called [Open Data Mashups](/blog/my-classes-for-fall-2019#is590om-open-data-mashups). The goal of this class was to produce a new dataset that integrated open data from 3-5 distinct sources, all while learning about project management, data management & curation, data provenance, reproducible workflows, version control, copyright & attribution, project & dataset documentation, and more.

I chose to expand upon my existing work with the Correlates of War datasets by integrating in other datasets commonly used by Peace/Conflict researchers: the UCDP/PRIO Armed Conflict dataset, the Polity IV dataset, the World Bank World Development Indicators dataset, and CShapes (historical country shape-files). When possible, I wrote scripts to acquire the data via API (UCDP/PRIO Armed Conflict, World Bank WDI). When needed, I normalized (3rd normal form) the datasets so they could be more easily manipulated (Correlates of War, UCDP/PRIO Armed Conflict). Some of the datasets were already in country-year format and didn't require too much wrangling (Polity IV, World Bank WDI).

One of the main challenges for this project was the fact that all 4 datasets used different country identifier schemes. CoW used their own CoW codes, UCDP/PRIO used the Gleditsch & Ward (G&W) codes, Polity IV used a version of the CoW codes that had been expanded, and the WorldBank used codes primarily based on the ISO 3-character country code standard. In order to connect these 4 similar but distinct schemas, I used Prof. Vincent Arel-Bundock's R package "countrycode". However, upon further investigation of the country-year panel dataset, I found several errors that I would need to correct in order to best integrate the 4 datasets.

The final product of this project is a [GitHub repo](https://github.com/jenna-jordan/international-relations-database-extended) with a country-year dataset (1946-2018) that includes variables from 2 datasets that separately track war and armed conflict (CoW & UCDP/PRIO), 1 dataset that tracks how autocratic/democratic a government is (Polity IV), and 1 dataset that tracks a wide variety of development indicators. Also included are the identifiers for historical country shape-files (CShapes) to more easily enable visualization. Documentation and code are also included in the repo.

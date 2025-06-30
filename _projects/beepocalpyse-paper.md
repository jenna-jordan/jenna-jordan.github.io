---
layout: page
category: Publications
importance: 3
title: "Beepocalypse"
permalink: /projects/beepocalypse
description: "Project completed for the Cline Center on media coverage of the beepocalypse, resulting in a PNAS Perspective article."
img: /assets/img/project_beepocalypse.jpg
github: https://github.com/jenna-jordan/beepocalypse
---

"No buzz for bees: Media coverage of pollinator decline" was published on January 12, 2021, as a part of the Global Insect Decline special issue in PNAS (Proceedings of the National Academy of Sciences of the USA). You can access the article [here](https://doi.org/10.1073/pnas.2002552117).
{: .notice--info}

[![Open in Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/jenna-jordan/beepocalypse_streamlit/main/app.py)

At the beginning of the Spring 2020 semester, Dr. May Berenbaum approached the Cline Center for Advanced Social Research about a potential project. Dr. Berenbaum is an entomologist at UIUC who has long researched the issue of pollinator decline. She wanted to see if the increasing levels of concern about pollinators in academic circles was reflected in coverage by the popular press. The Cline Center's Global News Index is a fantastic data resource for studies about media coverage, and our director, Dr. Scott Althaus, has a lot of experience in analyzing media coverage. Thus, the beepocalypse project was born.

I had worked at the Cline Center as a Graduate Research Assistant since the Spring 2019 semester - and my first semester was dedicated to writing the documentation for the Global News Index and Archer, a web application for querying the Global News Index. My role in the project was to collect, wrangle, and visualize the data. I worked with Dan Shalmon, my supervisor and the External Engagement Coordinator at the Cline Center, to develop and then refine our queries. We worked out several approaches to try and determine how to best include the most documents relevant to our topic and also exclude the irrelevant documents.

One of my primary focuses throughout this process was in developing a reproducible workflow. I wanted it to be easy to tweak part of a query, and then arrive at the new visualization simply by running the scripts. I used the Python Requests library to access the Solr API and programmatically acquire the data, and then used the pandas library to wrangle the data into the format I needed. For the visualization, this was a time-series dataset with article counts per month, per publisher, per query. I used a combination of ipywidgets and the Python plotly library to create an interactive visualization that would allow Drs. Berenbaum and Althaus to see how many articles matched each query within each publisher over time. I used Voila and Binder to make this visualization publicly available through a web link. This visualization tool was extremely useful in refining our approach to the final analysis, in selecting which queries and publishers to use and what angle to pursue in the paper. For the final visualizations that would be submitted with the paper, I used the weekly time-series data to create scatterplots with lowess trend lines in R, using the ggplot2 library.

After over two months of work, we submitted a Perspective article to PNAS in March 2020. The article is titled "No buzz for bees: media coverage of pollinator decline," and was co-written by Drs. Berenbaum and Althaus. Dan Shalmon and I both received co-author credit for our contributions in designing and performing the research, collecting and analyzing the data, and creating figures. I was very excited and grateful to be given co-author credit on this paper - it meant a lot to me, and I was happy just to have the opportunity to work with such amazing academics and play with some very interesting data!

The entire data collection, wrangling, and visualization process is available on the [GitHub repo](https://github.com/jenna-jordan/beepocalypse). The [replication data](https://databank.illinois.edu/datasets/IDB-4237085) is available at the Illinois Data Bank.

The Interactive Query Visualizer was originally published through Binder. I later re-made the app using Streamlit. Links for both sites are included below.

[![Open in Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/jenna-jordan/beepocalypse_streamlit/main/app.py)

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/jenna-jordan/beepocalypse/master?urlpath=%2Fvoila%2Frender%2FNotebooks%2FVisualize_Query_Results.ipynb)

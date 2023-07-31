---
layout: post
title: My Class and Internship for Summer 2019
date: 2019-07-31
description: the class I took during the summer semester of grad school and my summer internship
permalink: /blog/my-class-and-internship-for-summer-2019
toc:
  sidebar: left
thumbnail: assets/img/header_fall2018classes.jpg
categories: MSLIS
---
{% include figure.html path="assets/img/header_fall2018classes.jpg" class="img-fluid rounded z-depth-1" %}

Today was the last day of both my class and my internship for the summer! I have been taking a class online, IS562: Metadata in Theory & Practice, as well as working as a Data Science Intern at the Program on Governance and Local Development in Gothenburg, Sweden. First I'll introduce the class, and then share a reflection on my internship experience.

## IS562: Metadata in Theory & Practice

Rather than focusing on learning a specific metadata schema (some classes focus just on using those common in libraries, like MARC and MODS), this class focused on teaching the overarching concepts and technical traits that all metadata schemas share, in order to prepare students to work with any of the wide variety of metadata schemas and standards used in the real world (libraries, companies, academia, government, archives, etc). Along the way we got practice using a wide variety of specific metadata schemas (Dublin Core, CDWALite, PREMIS, and CIDOC-CRM just to name a few). While most metadata schemas are based in XML, we also learned about schemas that use RDF and how the semantic web and linked open data are becoming more prominent in the metadata world. PREMIS is a schema that currently uses XML but is in the process of transitioning to RDF, which makes it a very interesting schema to study.

### Course Description

> Metadata plays an increasingly critical role in the creation, distribution, management and use of electronic materials. This course will combine theoretical examination of the design of metadata schema with their practical application in a variety of settings. Hands-on experience in the creation of descriptive, administrative, technical, provenance and structural metadata in XML- and RDF-based schema, along with their application in systems such as harvesting and digital repositories, will help students develop a thorough understanding of current practices in metadata and metadata schema creation.

> Combines theoretical examination of the design of metadata schema with their practical application in a variety of settings. Hands-on experience in the creation of descriptive, administrative, and structural metadata, along with their application in systems such as OAI harvesting, OpenURL resolution systems, metasearch systems and digital repositories, will help students develop a thorough understanding of current metadata standards as well as such issues as crosswalking, metadata schema, metadata's use in information retrieval and data management applications, and the role of standards bodies in metadata schema development.

### Main Topics

- Identifiers
- Descriptive Metadata - Dublin Core, CDWALite
- Administrative Metadata - PBCore
- Technical Metadata, Provenance & Preservation - PREMIS, MIX,
- Structural Metadata - METS
- XML, Oxygen (XML Editor), Designing schemas with XSDs
- RDF, the Semantic Web, Serialization, and Linked Open Data - CIDOC-CRM
- Crosswalking, Quality Control, XSLTs
- OAI-PMH, SPARQL
- Workflows and Application Profiles

## Internship

I have spent the past 10 weeks working as a Data Science Intern at the Program on Governance and Local Development (GLD). The internship was kicked off in the best way possible - attending GLD's annual conference to learn about accountability in local governance and enjoying the wonderful hospitality only a Swedish seaside spa hotel can offer. The conference was a great way to learn about the ongoing academic work in local governance and development, and I was able to meet many interesting professionals from both academia and development agencies. But after the conference, it was time to get to work. This summer GLD has been conducting a survey in Kenya, Zambia, and (later) Malawi to gather data for their Local Governance Performance Index. GLD had just hired a new Data Scientist, and it was my job to help her with monitoring the data incoming daily from the survey. In addition to learning new tools like Survey To Go and dipping my toes into R, I was able to use the Python skills I've spent the last year developing almost every day. My skillset of information processing and organization was a perfect complement to the Data Scientist's skillset in statistical analysis (she had just completed her PhD in Statistics), and we worked really well together. Data science typically has two sides - preparing the data, and analyzing the data. I happen to enjoy (and have more experience in) preparing the data, while her expertise was in analysis. Along the way, I got a few ad-hoc lessons in various statistical concepts (she loves to teach statistics, and I was a very willing audience), and I did my best to make her job easier and allow her to spend more time on analyzing the data.

The vast majority of my python work was in processing XML documents using XPath (extracting needed information and sometimes putting it into tabular form), reorganizing tabular data using Pandas (with my design choices informed by relational databases), and writing extracted data into whatever format was needed for analysis (such as WKT files for use in QGIS). Every week - sometimes every day - there was some new information puzzle to solve... and it was fun. This was messy, real-world data that would eventually be used to try and improve people's lives. While using my newly developed technical skills was a major priority for me, it was just as important that my work, my time and effort, would go toward improving the world.

This internship was also a perfect transition between my first year at the iSchool - which was focused on information organization and processing - and my second year at the iSchool - which will be more focused on data analysis. I got to use my python skills prepare data for analysis, while getting an introduction to analysis through the osmosis of office conversations. I've even started working my way through Hadley Wickham's [R For Data Science](https://r4ds.had.co.nz), in anticipation of learning R in one my classes next semester. I have learned so much over the past year... I can only hope that I will learn just as much over the next!

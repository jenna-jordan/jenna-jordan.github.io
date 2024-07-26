---
layout: post
permalink: /backlog/
title: "Blog Backlog"
description: Blog posts currently sitting in drafts (in a folder or in my head)
date: 2024-07-26
---

I'm an inconsisent writer. I don't put out a new post every week, I don't steadily chip away at new content, but rather I tend to write in sudden, intense bursts when inspiration strikes and I have the free time (and then I sit on it for a while until I'm happy with it). I also have a lot of ideas, and the ideas that I am definitely going to write about at some point get added to the backlog. These blog posts may not exist yet, but they will at some point, so stay tuned.

The reference interview... for data teams
:    Everyone with an MSLIS degree knows about the reference interview. It's a core part of being a librarian, and it is a conversation/process that has been refined for the specific purpose of connecting a patron to the information they actually need. I also know that data teams can really struggle with identifying/delivering what stakeholders actually need (vs what they think they need and therefore ask for). So I want to introduce the idea of the reference interview to data teams as a framework for communicating with stakeholders and scoping projects.

The transformation flow, part 2: data modeling design paradigms
:    Part 2 of this series will be an overview of different data modeling techniques - 3rd normal form, dimensional models, data vault, one big table, etc. The goal is to introduce these different ways to model data and provide lots of links/references for folks to dig deeper if they wish, while also comparing/contrasting the methods.

The transformation flow, part 3: pipeline it all together
:    Part 3 of this series will focus on how the data transformation flow actually gets implemented in data warehouses. This will be the post that actually talks about the role of dbt and what a well designed transformation flow may look like.

Something about data mesh & dbt mesh
:    Hopefully this gets written before Coalesce in October!

Personal project series: Correlates of War dbt project
:    Following the completion of the transformation flow series (which is very abstract), I plan on writing a follow up series that documents how I implement the practices and data modeling methods with very specific examples. This will be accompanied by a project on GitHub with the actual code. I will use data from the Correlates of War project, store it in a duckdb database, and transform it with a dbt project, demonstrating how the same data can be modeled with different techniques (3NF, dimensional, OBT, etc) and how to create a dbt project from scratch.
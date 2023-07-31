---
layout: post
title: "Carpentries Workshops"
permalink: /projects/carpentries-workshops
date: 2021-09-28
toc:
  sidebar: left
description: "An overview of the workshops I've taught, including a semester-long syllabus."
thumbnail: assets/img/project_carpentries.jpg
categories: software-carpentries
---
{% include figure.html path="assets/img/header_carpentries.jpg" class="img-fluid rounded z-depth-1" %}

My Carpentries teaching journey started out slow - I taught a couple of times that first year, and stuck to the lesson I was most comfortable with (SQL & Databases). However, at the start of the summer in 2021 my work put me in charge (or I volunteered to be in charge) of a group of undergraduate interns who wanted to learn how to use computational methods for open source intelligence analysis. So I put together a curriculum of Carpentries lessons to take my interns from zero-assumed knowledge to the ability to complete a computational analysis in Python. I'm teaching the same curriculum in the Fall (slightly expanded and refined) to another group of undergraduate interns. This allowed me to gain experience in teaching more of the core Carpentries lessons... and also inspired me to develop [my own lesson focused on interactive data visualizations](/projects/carpentries-dataviz-workshop)!

---

# A semester-long curriculum of Carpentries workshops

Each week I teach for 2 hours, and then learners can practice what they've learned and give feedback on the workshop in an assignment (delivered via Google Forms). I've included the curriculum schedule below:

## Week 0: Self Assessment

**Goals:**

- Learners assess their current skill level

**Assignment:**

- [Computational Skills Self Assessment form](https://forms.gle/QsB6fFpn9VWiVjRz9)
  

## Week 1: GitHub

**Goals:**

- Instructor & learners introduce themselves
- Overview of the curriculum
- All learners have a GitHub account and know the basics of creating and modifying a personal repository on GitHub (with GitHub Desktop).

**Assignment:**

- [Assignment 1: GitHub](https://forms.gle/SPUiKxH5gtc1q5o47)

**Resources:**

- [Getting Started with GitHub - Training by Elizabeth Wickes](https://github.com/elliewix/github-training-brain-dumps/blob/master/github_directions.md)
- [GitHub's docs on creating a new account](https://docs.github.com/en/github/getting-started-with-github/signing-up-for-github)
- [GitHub's docs on GitHub Desktop](https://docs.github.com/en/desktop/installing-and-configuring-github-desktop/overview/getting-started-with-github-desktop#introduction)
- [GitHub's docs on creating a new repo](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-on-github/creating-a-new-repository)
- [Writing a good README](https://www.makeareadme.com/)
- [GitHub's docs on cloning a repo](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository-from-github)

## Week 2: The Shell (part 1)

**Lesson Plan:**

- [Shell workshop lesson plan from Software Carpentries](http://swcarpentry.github.io/shell-novice/) (Lessons 1-5)

**Goals:**

- become comfortable navigating your computer via the command line
- learn the basic set of Bash commands (pwd, ls, man, cd, mkdir, nano, touch, mv, cp, rm, wc, cat, less, sort, head, tail, echo)
- learn how to chain commands using the pipe, redirect, and append 
- learn how to use loops

**Assignment:**

- [Assignment 2: The Shell](https://forms.gle/CqZ1zkhdAmdBju8c9)
- [Answer Key for Assignment 2](https://docs.google.com/document/d/1uvkMieUHK2JM4XPx8mAeEmqvfdNiDSAQc2mUHshrAvE/edit?usp=sharing)

**Further Resources:**

- [The Linux Command Line - web tutorials](http://linuxcommand.org/lc3_learning_the_shell.php#contents)
- [The Linux Command Line - full free textbook](https://phoenixnap.dl.sourceforge.net/project/linuxcommand/TLCL/19.01/TLCL-19.01.pdf)
- [Explain Shell](https://explainshell.com/)

## Week 3: The Shell (part 2)

**Lesson Plan:**

- [Shell workshop lesson plan from Software Carpentries](http://swcarpentry.github.io/shell-novice/) (Lessons 6 & 7)
- [Shell Extras workshop lesson plan from Software Carpentries](http://carpentries-incubator.github.io/shell-extras/) (Lesson 2)

**Goals:**

- Learn how to save a series of commands as a shell script
- Learn how to search files from the command line
	- grep, find
- Learn how to generate and use your own SSH key pair
- Learn how to access a computer remotely
	- ssh, scp

**Assignment:**

- [Assignment 3: The Shell cont](https://forms.gle/hVq8VgEBWPyVXC4S8)
- [Answer Key for Assignment 3](https://docs.google.com/document/d/1B0qwQVUyNudAQ7jGPIAIONmU32FBedkNo4wkyPEsX74/edit?usp=sharing)

**Further Resources:**

- [Setting up and using the SSH config file](https://linuxize.com/post/using-the-ssh-config-file/)

## Week 4: Git

**Lesson Plan:**

- [Git workshop lesson plan from Software Carpentries](http://swcarpentry.github.io/git-novice/)

**Goals:**

- Learn how to use git from the command line
- Set up git on the remote sandbox server
	- git config
- Learn how to create repositories
	- git init
- Learn how to track changes
	- git add, git commit, git status, git log, git diff
- Learn how to use the history
	- HEAD, git show, git checkout, git revert
- Learn how to not track things
	- .gitignore
- Set up a remote repository
	- git remote, git push, git pull
- Learn how to collaborate & resolve conflicts
	- git clone

**Assignment:**

- [Assignment 4: Git](https://forms.gle/XyEa9RmgznnRuLPx7)
- [Answer Key for Assignment 4](https://docs.google.com/document/d/1VUVdRvK9YPIEqiVrWX_3pL1DeSr9e-brajbPsx0XgeY/edit?usp=sharing)

## Week 5: Python (part 1)

**Lesson Plan:**

- [Plotting & Programming in Python workshop lesson plan from Software Carpentries](http://swcarpentry.github.io/python-novice-gapminder/)  (Lessons 1-7)

**Goals:**

- Everyone has Anaconda (and thus Python & Jupyter Lab) installed and is familiar with how to work within Jupyter Lab and use a Jupyter Notebook
- Learn about data types and type conversion in python
- Learn how to use built in functions
- Learn how to get help, read the built-in docs, and read errors
- Learn how to import and use libraries
- Learn how to read data into a dataframe and interact with the dataframe (pandas)

**Assignment:**

- [Assignment 5: Python](https://forms.gle/oJYrV2aPVtnVPHJ56)
- [Answer Key for Assignment 5](https://docs.google.com/document/d/1FGN-ZHiPPu_dW73kC7o3ks9kWwXP8VtvXcPXe--2B2E/edit?usp=sharing)

**Further Resources:**

- [Intro to Anaconda from Software Carpentries](https://carpentries-incubator.github.io/introduction-to-conda-for-data-scientists/)


## Week 6: Python (part 2)

**Lesson Plan:**

- [Plotting & Programming in Python workshop lesson plan from Software Carpentries](http://swcarpentry.github.io/python-novice-gapminder/) (Lessons 8-12)

**Goals:**

- Learn how to select data from a dataframe (pandas)
- Learn how to plot data (matplotlib.pyplot)
- Learn how to work with lists
- Learn about for loops and the accumulator pattern

**Assignment:**

- [Assignment 6: Python & pandas](https://forms.gle/XPxxRaBubMaDaptD9)
- [GitHub repo for the pandas practice](https://github.com/NCRI-io/nclabs_pandaspractice)

## Week 7: Python (part 3) + requests & REST APIs

**Lesson Plan:**

- [Plotting & Programming in Python workshop lesson plan from Software Carpentries](http://swcarpentry.github.io/python-novice-gapminder/) (Lessons 13-18)
- [Storing Information with Dictionaries from Software Carpentries](https://cac-staff.github.io/summer-school-2016-Python/11-dicts.html)

**Goals:**

- Learn about conditionals (if, else, elif)
- Looping over files (glob)
- Learn how to write functions
- Learn about the dictionary data type
- Learn how use python's requests library to query a REST API

**Assignment:**

- [Assignment 7: Python](https://forms.gle/GGDeBWAmg5Ck7WRA7)

**Further Resources:**

- [Python & APIs: A Winning Combo for Reading Public Data from Real Python](https://realpython.com/python-api/)
- [Python API Tutorial: Getting Started with APIs from DataQuest](https://www.dataquest.io/blog/python-api-tutorial/)

## Week 8: Interactive Data Visualizations

**Lesson Plan:**

- [Interactive Data Visualizations in Python workshop lesson plan](https://carpentries-incubator.github.io/python-interactive-data-visualizations/)

**Goals**

- Learn how to create a new conda environment
- Learn how to wrangle data into a tidy shape
- Learn how to create line plots with plotly
- Learn how to create and run a streamlit app
- Learn how to add widgets to the streamlit app

## Week 9: Databases & SQL (part 1)

**Lesson Plan:**

- [SQL workshop lesson plan from Software Carpentries](http://swcarpentry.github.io/sql-novice-survey/) (Lessons 1-5)

**Goals:**

- Learn how to select data from a table
- Learn how to sort results and remove duplicates
- Learn how to filter, or select subsets of data, based on boolean conditions
- Learn how to calculate new values to be returned in the results
- Learn about missing data, and incorporating NULL into queries

**Assignment:**

- [Assignment 8: SQL](https://forms.gle/wWQFYSREEXLkQQMA6)

## Week 10: Databases & SQL (part 2)

**Lesson Plan:**

- [SQL workshop lesson plan from Software Carpentries](http://swcarpentry.github.io/sql-novice-survey/) (Lessons 6-10)

**Goals:**

- Learn how to aggregate data in queries (calculate sums, averages, etc)
- Learn how to combine tables in a query
- Learn about data hygiene, and principles of database design like primary & foreign key constraints
- Learn how to create, modify, and delete data
- Learn how to use SQLite databases within a python script

**Assignment:**

- [Assignment 9: SQL](https://forms.gle/hdgDb7KsQU2DhVCw9)
- Review [Lesson 10](https://swcarpentry.github.io/sql-novice-survey/10-prog/index.html) (Programming with Databases - Python) on your own

## Week 11: Regular Expressions 

**Lesson Plan:**

- [Regular Expressions workshop lesson plan from Library Carpentries](https://librarycarpentry.org/lc-data-intro/)

**Goals:**

- Learn how to use Regular Expressions (regex)

**Assignment:**

- Practice using regular expressions by completing some [Regex Crosswords](https://regexcrossword.com/)

**Further Resources:**

- [Regular Expressions workshop videos from Software Carpentries](https://youtube.com/playlist?list=PL7C1EB31127AB8A0B)

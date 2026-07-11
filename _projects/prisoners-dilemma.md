---
layout: page
category: Grad School
importance: 2
title: "Prisoner's Dilemma"
permalink: /projects/prisoners-dilemma
description: "This was my final project for an Intermediate Python course, and is a Monte Carlo analysis of the Prisoner's Dilemma (with reactive noise)."
img: /assets/img/project_prisoners-dilemma.jpg
github: https://github.com/jenna-jordan/Prisoners-Dilemma
---

The Prisoner's Dilemma has long been a favorite for political scientists - it is a game that has many applications in international relations (the iterated prisoner's dilemma game is also known as the "Peace-War game"), and simulations of the game can be easily conducted and analyzed with computers. Every year tournaments are held with slight tweaks to the rules, and submitted strategies compete to win the most points overall. Each rule adjustment is made to bring the game closer to reality, and find the best strategy that can be applied to the real world.

The tournament that I created has its own tweak: reactive noise. Most modern tournaments contain some level of noise (the chance that the other player will misinterpret your move), however the noise level tends to remain fairly constant. The idea behind reactive noise is that in the real world, cooperating decreases noise (by increasing trust and transparency), while defecting increases noise. So in the tournament that I designed, there is an arbitrary starting level of noise, and each time a player cooperates that noise is reduced some amount, and then each time a player defects that noise is increased some amount. Randomness is based into the game at every possible opportunity (using python's 'random' library), as is suitable for a Monte Carlo simulation.

Credit for the idea of reactive noise belongs to Dan Shalmon, who mentioned the idea during a long and fascinating discussion about the prisoner's dilemma at the Cline Center office.
{: .notice--info}

The full code is available on the [GitHub repo](https://github.com/jenna-jordan/Prisoners-Dilemma), as well as a Quick Start Guide for anybody interested in running their own simulations. The parameters are completely flexible - you can either leave them at the defaults and run the analysis simply by calling the function `run_MCsim()`, or play with the parameters (detailed in the Quick Start Guide) to see how/if the resulting rankings vary.

Three classes are used to run the tournament: Strategy, Player, and Game. Each specific strategy is a Strategy subclass, with 16 common strategies included in the Strategy code. Each player uses a single Strategy, and each Game plays two Players against each other (who may or may not be using the same strategy).

On a personal note, this project is the first time I have ever written object-oriented python code, using classes to pass information between objects. It helped to deepen my understanding of many fundamental programming concepts, and advanced my capabilities in using python for data analysis. This served as my final project for IS590PR (Programming for Analytics and Data Processing) during the Spring 2019 semester.

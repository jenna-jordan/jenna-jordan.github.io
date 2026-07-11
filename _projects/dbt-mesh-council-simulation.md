---
layout: page
category: Data & Analytics Engineering
importance: 2
title: "dbt Mesh Council Simulation"
permalink: /projects/dbt-mesh-council-simulation
description: "A role-playing game to simulate a migration to dbt Mesh, created for a peer exchange at Coalesce 2024."
img: /assets/img/coalesce2024_governance-co-lab_frontpage.jpg
---

{% include figure.html path="assets/img/coalesce2024_session_stage.jpg" class="img-fluid rounded z-depth-1" %}

On Tuesday, October 8, 2024, I facilitated a [peer exchange session at Coalesce 2024](https://coalesce-widgets.getdbt.com/agenda/session/1383564):

> #### Governance co-lab: We the people, in order to govern data, do establish processes
>
> While dbt Mesh features provide options for a technical implementation of data & model governance, the people & process side of the equation is left up to organizations to figure out. Some organizations may have data governance structures already established and need to figure out how dbt fits into the picture, while other organizations may be learning that they now need to stand up data governance structures in order to have an effective dbt Mesh of project(s).
>
> In this peer exchange you will join a simulation game to co-create a Mesh Migration Plan. Players will take on specific roles to advocate for their teams as new processes are planned out, governance structures are established, and problem scenarios need to be solved. Achieve a collective win by finalizing your Mesh Council’s strategy and individual wins by accomplishing your role’s secret mission along the way.
>
> Participants should walk away with both ideas to take back to their organizations for implementing dbt Mesh and a new network of contacts they can reach out to for support.

A peer exchange is kind of like a formalized version of the "hallway track" - the casual conversations you have in the hallways at conferences that somehow end up being more valuable than the formal talks. The goal is to facilitate discussions among the attendees around a particular topic, rather than delivering a presentation and talking by yourself up on stage. The peer exchange sessions were all 1 hour long (whereas a talk was 30 minutes). 

I decided to do something a bit different for my peer exchange session, inspired mostly by my past experiences with Model United Nations (and also collaborative role-playing games like Dungeons & Dragons). The goal was to let participants practice doing the messy part of data governance: proposing policies and processes, figuring out how to formalize and enforce them, while dealing with the conflicting goals and motivations that come with people being people. You can learn a lot of technical skills with just yourself and a computer, but you can't learn how to effectively govern & strategize in isolation. Also... I really wanted my session to be enjoyable! What better way to make a conference session fun than to gamify it?

<div class="row">
    <div class="col-sm mt-2 mt-md-0">
        {% include figure.html path="/assets/img/coalesce2024_table3_1.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-2 mt-md-0">
        {% include figure.html path="/assets/img/coalesce2024_table3_2.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The peer exchange room was filled with round tables, each with 10 chairs. In my simulation game, each table became a "Mesh Council", composed of 10 representatives divided into 5 teams (so everyone had a partner). Each table got an "Architect's Handbook", which contained important background information and a starting proposal. Everyone also got their own "role sheet", which contained information about their individual role and shared information about their team. Most information was shareable, but each team and role also had "secret missions" that they should try to achieve by the end of the game. These secret missions enabled participants to achieve individual competitive wins, in addition to the collective win of coming up with a set of policies that passed a final vote. They also introduced conflict - a vital part of any realistic simulation. 

{% details *Click here to learn about Rainbow Road, the fictional organization participants were working for* %} 

Rainbow Road started as a local rescue, bringing pets from rural kill shelters into the city to ease the adoption process. They were successful at matching more pets with loving homes, and soon partnered with other nearby rescues to form a regional adoption network.

Rainbow Road was able to better serve the many adoption centers by centralizing logistics for mass distribution of resources and coordinating across partners. This worked great for a time, and allowed the rescue centers to focus on what they did best: the operational side of rescuing pets.

Rainbow Road started using a central data warehouse to consolidate information about the animals being rescued (including important information like their medical records and available history), the volunteers helping to take care of these animals, facilities where animals were temporarily housed, and more.

Rainbow Road soon adopted dbt to organize all of the needed transformations in the data warehouse. This enabled them to more quickly and accurately report statistics about the pets rescued, which allowed them to get more funding, and then to expand into other states and help even more animals.

This centralized model worked so well that within a few more years Rainbow Road grew to operate at the national level. Other parts of the organization started wanting to use dbt and the data warehouse too - for tracking donations, analyzing marketing efforts, reporting key performance metrics for each adoption center, and more.

Now the organization has grown enough that data-oriented teams are more independent, different regions have different needs, and the dbt project’s DAG has started to resemble an unmanageable spaghetti monster.

Data is an important part of keeping the pet rescue running & funded, so Rainbow Road hired a Data Architect consultant to evaluate the growing data infrastructure and advise the data teams. The data architect recommended migrating from the single monolithic dbt project to a dbt mesh of projects, and sketches out an overall design for the diZerent projects. Rainbow Road has outgrown the centralized model, and now it’s time to decentralize (a little? A lot? Only time will tell!)

{% enddetails %}
<br>
<div class="row">
    <div class="col-sm mt-2 mt-md-0">
        {% include figure.html path="/assets/img/coalesce2024_table5_1.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-2 mt-md-0">
        {% include figure.html path="/assets/img/coalesce2024_table5_2.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The session was guided by a slide deck - I started by laying out the rules and game plan, and quickly reviewed the backstory for the organization they would be representing. During the exercise, each slide contained the main objective for the current activity. There were 3 "Council Sessions", broken up by an emergency scenario (to help ground future policy making in an example of a specific problem) and a cross-council sidebar (to allow participants with the same role at different tables to confer and share ideas). After a final vote at the end of the 3rd session, each council presented out their final policies.

<div class="row">
    <div class="col-sm mt-2 mt-md-0">
        {% include figure.html path="/assets/img/coalesce2024_result1.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-2 mt-md-0">
        {% include figure.html path="/assets/img/coalesce2024_result2.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-2 mt-md-0">
        {% include figure.html path="/assets/img/coalesce2024_result3.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-2 mt-md-0">
        {% include figure.html path="/assets/img/coalesce2024_result4.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-2 mt-md-0">
        {% include figure.html path="/assets/img/coalesce2024_result5.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    The final policies from 5 of the Mesh Councils - each table had a large flip-pad to document their policies.
</div>

This was such a fun experience - both designing the simulation and getting to watch everyone play the game. I got some amazing feedback at the end - one person said that they felt they had accomplished more in the past hour than their organization's data governance team had accomplished in the past year! My favorite feedback though was actually a request: multiple participants requested access to the materials so that they could take the experience back home and run the simulation within their own organizations. I shared the materials in our slack channel, [#coalesce-peer-exchange-1](https://getdbt.slack.com/archives/C07NL2CENP7), and I'm also including them here:

<div class="row">
    <div class="col-8 mt-2 mt-md-0">
        <a href="/assets/pdf/C24_TUE_1115_PEEREXCHANGE_GOVERNANCE_CO-LAB.pdf">
        {% include figure.html path="/assets/img/coalesce2024_governance-co-lab_frontpage.jpg" title="Slidedeck" class="img-fluid rounded z-depth-1" %}
        </a>
    </div>
    <div class="col-4 mt-2 mt-md-0">
        <a href="/assets/pdf/Governance co-lab printed materials.pdf">
        {% include figure.html path="/assets/img/coalesce2024_rolesheet.jpg" title="Printed materials" class="img-fluid rounded z-depth-1" %}
        </a>
    </div>
</div>
<div class="caption">
    The slide deck and the printed materials from the session
</div>

If anyone else does end up running this simulation game, I would really love to hear how it goes! Please, please reach out and let me know.

While this session was in-person and designed to be specific to dbt, I'm also planning on adapting the exercise to be playable online (e.g. over Zoom) and more general (for any data mesh, independent of any tech vendor's implementation). So stay tuned for future data strategy simulation games!

# Working Session on dbt Mesh at the Chicago dbt Meetup

The simulation game at Coalesce was amazing - it was big, complex, required a lot of setup, and took time to play through. While we only had an hour, ideally this simulation game should have taken 2-4 hours. But you can learn through role-playing and simulation in shorter exercises as well, and this is what I did at the [Chicago dbt Meetup](https://www.meetup.com/chicago-dbt-meetup/events/302721675/) a month prior.

Analytics8 hosts the dbt Meetup in Chicago, and with my upcoming peer exchange session at Coalesce I was offered the opportunity to "preview" the session at the meetup. I wanted to keep the theme of role-playing to solve the people & process problems that come with governing a dbt Mesh, but reduce the setup and complexity. So I adapted the "emergency scenario" part of the larger simulation exercise and created 3 "problem scenarios" that involved 3 different roles. For light background context, I used the dbt Lab's Jaffle Shop mesh project, which was helpfully composed of 3 different projects. I've always found 3 to be the magic number for small group discussions. Finally, before actually diving into the problem scenarios, I reviewed the core dbt features that were important to dbt Mesh governance, to ensure that everyone would have a familiar floor of understanding.

For each problem scenario I gave the groups about 10 minutes to discuss and come up with a final solution. I then facilitated the feedback, so that groups could compare their solutions to others. I started by asking one group to present their solution, and then asked the other groups if anyone came up with a similar solution, to build on that first approach. After one approach was fully fleshed out, I then asked if any groups came up with a completely different solution, and repeated the process. This resulted in some great discussions and back-and-forth between the groups, and overall everyone seemed really engaged and interested. I would highly encourage other meetups to try out a similar approach - after all, people usually go to meetup to meet other people, network, and have good conversations... and this "working session" was a great middle ground between a straight presentation and just generic casual conversations.

<div class="row">
    <div class="col-sm md-auto">
        <a href="/assets/pdf/dbt_Mesh_Working Session.pdf">
        {% include figure.html path="/assets/img/dbt_Mesh_Working Session.jpg" title="Slides"  class="img-fluid rounded z-depth-1" %}
        </a>
    </div>
</div>
<div class="caption">
    Slides from the "working session" half of the Chicago dbt Meetup
</div>
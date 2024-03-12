---
layout: page
category: Data Engineering
importance: 1
title: "dbt Migration at City of Boston"
permalink: /projects/dbt-migration-cob
description: "Modernizing the Analytics Team's engineering pipelines by migrating transformations and tests to dbt and enabling the team's first data catalog."
img: /assets/img/coalesce2023_from-coast-to-coast_frontpage.jpg
github: https://github.com/CityOfBoston/cob_analytics_dbt_skeleton_project
---

During the last year I worked on the Analytics Team at the City of Boston, I proposed and led a redesign of our data warehouse and ETL pipelines centered around the implementation of dbt. This effort started in March 2023 with a proposed new set of schemas for the PostgreSQL data warehouse, and by March 2024 the migration of the engineering team's pipelines to a dbt-centered implementation was nearly complete. The Analytics Team's first Data Catalog, built from the dbt-generated docs, also launched for a select group of users in March 2024.

## Presenting at Coalesce 2023

<div class="row">
    <div class="col-sm md-auto">
        <a href="https://coalesce.getdbt.com/agenda/from-coast-to-coast-implementing-dbt-in-the-public-sector">
        {% include figure.html path="/assets/img/c23-session-promo.png" title="Session Promo Card"  class="img-fluid rounded z-depth-1" %}
        </a>
    </div>
</div>
<div class="caption">
    City of Boston's dbt migration was one of 3 case studies in our Coalesce 2023 talk
</div>

I had the opportunity to share out about this migration to dbt at Coalesce in October 2023. Along with my cospeakers Ian Rose at the California Office of Data and Innovation and Laurie Merrell at Jarvus Innovations, we made the case for why public sector data teams should consider adding dbt to their toolset and presented 3 dbt implementation case studies from our respective organizations.

<div class="embed-responsive embed-responsive-16by9">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/6aX7tAfMmIM?si=BiAR8rRA6mjgrQ9I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>
<div class="caption">
    Official recording of "From coast to coast: Implementing dbt in the public sector" on YouTube
</div>

Our goal with this talk was to help other public sector data teams who might be interested in implementing dbt to (1) know whether they should consider dbt (is their team ready for it, and what value would dbt add), (2) if so what might that implementation look like (three case studies with supporting open-source GitHub repos), and finally (3) to jumpstart a community of dbt users in the public sector or adjacent fields. We also wanted to advocate for data professionals currently using dbt to consider working in the public sector.

<div class="row">
    <div class="col-sm md-auto">
        <a href="/assets/pdf/coalesce2023_from-coast-to-coast_slides.pdf">
        {% include figure.html path="/assets/img/coalesce2023_from-coast-to-coast_frontpage.jpg" title="Slides"  class="img-fluid rounded z-depth-1" %}
        </a>
    </div>
</div>
<div class="caption">
    PDF of the slides presented during the talk
</div>

I collated all of the resources associated with this talk in a GitHub repo ([dbt-public-sector-resources](https://github.com/jenna-jordan/dbt-public-sector-resources)), which has links to the talk, the slides, and the public GitHub repos for each case study.
<br>
<div class="repo p-2 text-center">
  <a href="https://github.com/{{ include.repository }}">
    <img class="repo-img-light w-600" alt="{{ include.repository }}" src="https://github-readme-stats.vercel.app/api/pin/?username=jenna-jordan&repo=dbt-public-sector-resources&theme={{ site.repo_theme_light }}&show_owner=true">
    <img class="repo-img-dark w-600" alt="{{ include.repository }}" src="https://github-readme-stats.vercel.app/api/pin/?username=jenna-jordan&repo=dbt-public-sector-resources&theme={{ site.repo_theme_dark }}&show_owner=true">
  </a>
</div>
<br>
For the City of Boston's public GitHub repo, I created a copy of our dbt project minus any of the models - so, just the skeleton - along with supporting resources like Civis workflow YAML files and bash & python scripts ([cob_analytics_dbt_skeleton_project](https://github.com/CityOfBoston/cob_analytics_dbt_skeleton_project)). Hopefully, any other teams who use Civis Platform and want to see how to run a dbt build can use this repo as an example.
<br>
<div class="repo p-2 text-center">
  <a href="https://github.com/{{ include.repository }}">
    <img class="repo-img-light w-600" alt="{{ include.repository }}" src="https://github-readme-stats.vercel.app/api/pin/?username=CityOfBoston&repo=cob_analytics_dbt_skeleton_project&theme={{ site.repo_theme_light }}&show_owner=true">
    <img class="repo-img-dark w-600" alt="{{ include.repository }}" src="https://github-readme-stats.vercel.app/api/pin/?username=CityOfBoston&repo=cob_analytics_dbt_skeleton_project&theme={{ site.repo_theme_dark }}&show_owner=true">
  </a>
</div>
<br>
{% details March 2024 update %}
I first published our dbt project skeleton in October 2023 (in time for Coalesce), but by March 2024 we had significantly evolved our dbt implementation - making full use of the elementary package, selectors, stateful dbt builds, and more. So the public skeleton repo is now up to date with the actual dbt project as of March 11, 2024.
{% enddetails %}
<br>

## Data Catalog

While implementing dbt was a significant improvement for the Data Engineering team, the primary impact for the rest of the Analytics Team and other users of the data warehouse was in the documentation that it enabled. The dbt-generated docs website was dbt's primary selling point for non-engineers (the lineage graphs are especially stunning). So starting in November 2023 we began a concerted effort to get the docs site published as an officially supported DoIT application, with a boston.gov URL and Single Sign-On authentication.

<div class="row">
    <div class="col-sm md-auto">
        <a href="/assets/pdf/dbt-lunch-learn.pdf">
        {% include figure.html path="/assets/img/dbt-lunch-learn.jpg" title="Slides"  class="img-fluid rounded z-depth-1" %}
        </a>
    </div>
</div>
<div class="caption">
    PDF of the slides presented for the DoIT Lunch & Learn
</div>

By March 2024, after a significant collaborative effort across many teams in the department, the first iteration of the official Analytics Data Catalog was published. I am so proud that this important resource is now available to city workers, and to know that my coworkers will continue to iterate on and build both the dbt project and the Data Catalog after my departure.

<div class="row">
    <div class="col-sm md-auto">
        {% include figure.html path="/assets/img/data-catalog-mar11.png" title="Data Catalog"  class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Screenshot of the Data Catalog from March 11, 2024
</div>
---
layout: distill
featured: true
title: So you want to build a data mesh
date: 2025-10-15
description: "... with your dbt project(s)"
permalink: /blog/data-mesh-dbt
thumbnail: assets/img/header_data-mesh.png
categories: data essays
authors:
  - name: Jenna Jordan
    url: "https://jennajordan.me"
    affiliations:
      name: "dbt community member"
      url: "https://docs.getdbt.com/community/spotlight/jenna-jordan"
bibliography: 2025-10-15-data-mesh-dbt.bib
toc:
  - name: A brief history of data mesh (and further resources)
  - name: Why data mesh and dbt
  - name: The 4 principles of data mesh
    subsections:
      - name: Domain Ownership
        subsections:
          - name: Applied to dbt
      - name: Data as a Product
        subsections:
          - name: Applied to dbt
      - name: Self-serve Data Platform
        subsections:
          - name: Applied to dbt
      - name: Federated Computational Governance
        subsections:
          - name: Applied to dbt
  - name: People and Process
    subsections:
      - name: Decision time
        subsections:
          - name: Domain Ownership
          - name: Data as a Product
          - name: Self-serve Data Platform
          - name: Federated Computational Governance
      - name: Map out your process
  - name: Wrapping Up
  - name: Appendix
---

{% include figure.html path="assets/img/header_data-mesh.png" class="img-fluid rounded z-depth-1" %}

> The Coalesce session recording is now available! See the [Appendix](#appendix)

During my time as a consultant with Analytics8, I worked with two different companies who were both implementing dbt Mesh. I learned so much from both of those engagements, both from my very smart colleagues at both Analytics8 and the clients, and from the problems I had to solve while implementing dbt Mesh. I also started learning more about data mesh, and added the Data Mesh bible to my bookshelf. I saw the chaos that could result from implementing dbt Mesh simply as a convenient higher level of organization, and I became convinced that one of the best ways to implement dbt Mesh was with data mesh as a grounding, opinionated philosophy.  

Data Mesh exploded into the data scene in 2022 with Zhamak Dehghani’s book “Data Mesh: Delivering Data-Driven Value at Scale”.<d-footnote>Every quote throughout this blog post, unless otherwise noted, is from this book.</d-footnote> Zhamak characterized data mesh as a “decentralized sociotechnical approach to share, access, and manage analytical data in complex and large-scale environments -- within or across organizations.”<d-cite key="Dehghani_2022"></d-cite>

She clarifies that data mesh is about analytical data, not operational data, and that it is an approach to data management, not an architecture. It belongs properly as part of an organization’s data strategy, and provides a target state to iterate towards for both the organizational operating model (socio) and enterprise architecture (technical).   

Data mesh is defined by its 4 core principles, which when applied can shift how data is managed organizationally, architecturally, technically, operationally, principally, and infrastructurally. And perhaps most importantly, data mesh is not for every organization - it is only intended for organizations that have reached a certain scale and maturity (and therefore complexity) in their data practices.   

Zhamak is purposefully tech & tool agnostic in her book, though she went on to found her company Nextdata to create the tech to best implement her vision of a data mesh. This means that as long as you are following the 4 principles of data mesh, you can use any set of tools you want to build your own data mesh - including dbt.   

We are going to explore these 4 principles through the lens of dbt, with the goal of outlining an opinionated approach to how you should architect your dbt Mesh of project(s). While dbt is extremely flexible in how it can be implemented, often a strong structure and grounding philosophy can be more helpful than endless possibilities.   

Much like data mesh, dbt Mesh should really only be considered if your organization has reached a certain scale and maturity in your data practices. Like data mesh, dbt Mesh was designed to solve problems encountered by organizations maintaining very large and very mature dbt projects. If this is not you, congratulations: you don’t have to deal with all of the additional complications data/dbt mesh introduces for a while yet. Enjoy it while you can!

### A brief history of data mesh (and further resources)

Zhamak first started writing about Data Mesh in 2019, when she published “[How to Move Beyond a Monolithic Data Lake to a Distributed Data Mesh](https://martinfowler.com/articles/data-monolith-to-mesh.html)” on her ThoughtWorks colleague Martin Fowler’s blog. She followed this up with “[Data Mesh Principles and Logical Architecture](https://martinfowler.com/articles/data-mesh-principles.html)” in 2020, and then fully articulated the data mesh approach in her 2022 book “[Data Mesh: Delivering Data-Driven Value at Scale](https://www.thoughtworks.com/en-us/insights/books/data-mesh)”.  

Data mesh made it onto Gartner’s 2022 Hype Cycle for Data Management in the “Innovation Trigger” phase (the first phase), but was predicted to become obsolete before reaching the final phase, the “Plateau of Productivity”.   

Data mesh quickly gained a following among data practitioners who believed this approach could solve many of the pain points they had been experiencing in managing data at very large organizations. The [Data Mesh Learning Community](https://datameshlearning.com/) was founded in 2021 to help practitioners connect and learn about data mesh from each other.   

After Zhamak’s book was released in 2022, she quit her role at ThoughtWorks to found her own company, Nextdata, to create her ideal implementation of a data mesh architecture. For 3 years they were quietly building, and meanwhile many in the data community declared that data mesh was dead (as they are often wont to do) - that while it sounds great in theory, it is impossible to actually implement, and data teams should instead adopt pieces of the data mesh strategy and then move on. But in April 2025 Nextdata publicly launched their product [Nextdata OS](https://www.nextdata.com/product), an operating platform purpose-built for autonomous data products. Data mesh is once again in the public dialogue - it seems to have survived the “trough of disillusionment” and is now climbing the “slope of enlightenment” (though I suppose we’ll have to wait for next year’s hype cycle report to see if Gartner agrees).  

Data mesh as a concept has also evolved as the thought leadership on data mesh has expanded beyond Zhamak to include others like Jean-Georges Perrin (JGP), who co-authored “[Implementing Data Mesh](https://www.oreilly.com/library/view/implementing-data-mesh/9781098156213/)” with Eric Broda in 2024 and authored the soon-to-be-published “[Building Data Products](https://www.oreilly.com/library/view/building-data-products/9798341629394/)”. JGP’s focus is primarily on the principle of data as a product, and you can read more about his approach in the blog post “[The Next Generation of Data Platforms is Data Mesh](https://dataintelligenceplatform.substack.com/p/the-next-generation-of-data-platforms)”. JGP is also the chair of the Linux Foundation’s [Bitol](https://bitol.io/) project, which has published the [Open Data Product Standard (ODPS)](https://bitol-io.github.io/open-data-product-standard/latest/) and [Open Data Contract Standard (ODCS)](https://bitol-io.github.io/open-data-contract-standard/latest/).

### Why data mesh and dbt

Data mesh and dbt both share a single fundamental mission: bringing software engineering best practices to data engineering. With [dbt](https://www.getdbt.com/blog/data-engineering), analytics engineers got version control, CI/CD, isolated development and production environments, testing, and documentation out of the box. Similarly, Zhamak positions data mesh as bringing the decentralization revolution in software engineering (microservices architecture) to the data world. Notably, both data mesh & microservices architecture were deeply influenced by Eric Evans' book [Domain-Driven Design](https://domainlanguage.com/ddd/).   

While the product name choice of “dbt Mesh” may make you think that it is dbt’s solution to data mesh, there have actually only been a few explicit lines drawn between dbt Mesh and data mesh. For the most part, [dbt Labs](https://docs.getdbt.com/best-practices/how-we-mesh/mesh-5-faqs) maintains that dbt Mesh is a natural evolution of dbt as enterprises scaled up from a single dbt project into needing multiple interconnected projects. However, [Hope Watson](https://www.linkedin.com/posts/activity-7284688805645697024-cQFA?utm_source=share&utm_medium=member_desktop&rcm=ACoAAAiK2FABKHqWAaEnq7CdATQwY_GSauRe0Xg) (a dbt Labs Resident Architect) made the connection between data mesh and dbt Mesh explicit in her training course “[Data Mesh with dbt Cloud for dbt Practitioners](https://www.loom.com/share/ea99434045ab4d1da4f794cee9e28500?sid=134d190f-c84e-420c-9ed9-1b185b1bed29).”  

dbt Mesh’s product history reflects this natural evolution, and I could not have always recommended dbt as a way to implement data mesh. There are still several serious limitations that will influence your dbt Mesh architecture, but I also hope that the perspective in this blog post - dbt Mesh as a way to implement a version of data mesh - can influence the dbt Mesh product roadmap enough that these shortcomings will eventually be resolved (read: dbt product and developer experience teams, this is for you too!).  

dbt Lab’s product strategy has also shifted to better enable a data mesh implementation - beyond support for Iceberg and Cross-Platform Mesh, the metadata capabilities unlocked by dbt Fusion are hugely important for enabling key features needed in a data mesh. We’ll cover the most important feature, state-aware orchestration, in the section on the principle of domain ownership.  

One final note: for the most part, folks implementing data mesh using dbt will be dbt Labs Enterprise customers. Most dbt Mesh features require an Enterprise or Enterprise+ plan. However, if you are really set on a data mesh with dbt core, it is not an impossibility - you will just need to work a bit harder and figure out your own setup. I’ll point you to the [dbt-loom plugin](https://github.com/nicholasyager/dbt-loom) for cross-project dependency management and [Dagster](https://dagster.io/) for [multi-project orchestration](https://github.com/cnolanminich/dbt-loom-example/tree/bi-directional-data-mesh) (see a [demo](https://www.loom.com/share/059ce1e196834fc6a427de071fb9cc24) of how it works!).

## The 4 principles of data mesh

Data mesh is defined by 4 principles that work in concert:

1. Domain Ownership  
2. Data as a Product  
3. Self-serve Data Platform  
4. Federated Computational Governance

Each of these 4 principles can guide how you should implement dbt Mesh for distributed data management at scale. Let’s take them one at a time.

### Domain Ownership

The principle of Domain Ownership is the first stumbling block for organizations trying to implement data mesh, because it requires organizational change. While other principles can be (mostly) accomplished by technologists, this principle requires buy-in from leadership and long-term investment in data mesh as the data strategy.   

Rather than having a central data team that serves all departments, organizations should decentralize the ownership of analytical data to the business domains, and ensure that team structure is aligned by domain. Each business domain (already its own organizational unit) should be responsible for curating, maintaining, and sharing the data that it is most familiar with.  

The implication here is: if your organization currently has a single centralized data team, and cannot or does not wish to functionally have many small domain-oriented data teams, then your organization is not ready for data mesh (and that’s okay!). But if your organization is already organized by domain with data practitioners embedded, they are probably itching for ownership over their own data and the support to do so successfully.

#### Applied to dbt

Simply put, the recommendation here is simple: align your dbt projects to your domains. Each business domain, with its own set of self-sufficient data practitioners, should have ownership over their own dbt project.  

Of course, nothing can be simple when you are playing in the waters of distributed systems. Up until very recently, it was not possible (and then not recommended) to completely align your dbt projects to your domain teams due to complications around bidirectional project dependencies.   

When dbt Mesh was first announced at Coalesce in 2023, dbt Labs advocated a hub-and-spoke model, where a central data team still maintained the “hub” project, but now downstream domain teams could use models from the “hub” while developing their own custom models in isolated “spoke” projects. This architecture was necessitated by the fact that project dependencies could only go one way - the “hub” project could never depend on models from one of the “spoke” projects. Not very meshy, was it? In a data mesh, domain teams should be able to serve and consume data products to and from each other.  

This meant that, functionally, all dbt projects had to be a DAG (directed acyclic graph) as well. As a result, organizations were either forced into a hub-and-spoke strategy (though this likely was not an issue for organizations wanting to continue with having a single central data team), or domain-oriented projects would get split up into “producer” and “consumer” projects.   

Fortunately, after product feedback from customers (including yours truly), dbt Labs made bidirectional project dependencies possible in 2024, with the feature generally available in October along with a suite of other mesh-related product announcements at Coalesce (notably cross-platform Mesh). While all of the models across all of the projects still had to adhere to the “acyclic” rule of DAGs, the projects themselves no longer had to form a DAG.  

But - and this is a very big but - there was still no elegant way to orchestrate for these bidirectional dependencies. dbt Labs knew that they would need to figure this out, and pre-emptively [announced adaptive jobs](https://youtu.be/KB3Xrhvg-_0?si=0-ZZmh3x7U6c5QYY&t=829) as a feature that would be coming soon, but until then it would be inadvisable to architect a dbt Mesh with bidirectional project dependencies.   

We finally got resolution for this story in May at dbt’s Launch Showcase with “[State Aware Orchestration](https://docs.getdbt.com/docs/deploy/state-aware-about)”, a feature of the new dbt Fusion engine… which as of this week at Coalesce 2025 is now in public preview! This means that there is now a way to orchestrate for dbt Meshes with bidirectional project dependencies, but only if you are also able to transition over to the dbt Fusion engine. dbt Fusion and state-aware orchestration are also not yet generally available, so implement with caution (and report bugs).  

Now that we’ve covered some of the major dbt Mesh product developments that have resulted in the fact that I can finally now recommend organizing your dbt projects according the first data mesh principle of domain ownership, let’s talk about the other complicating factor: your organization. There are two different organizational profiles that are likely to implement dbt mesh:

1. The organization that has been using dbt for years, with model counts ballooning into the thousands and DAG that looks like the Cthulu version of a spaghetti monster, finally needing to split their single project up into many for the sake of everyone’s sanity  
2. The organization that is new to adopting dbt but knows they either want a data mesh or are already operating with a data mesh strategy, and therefore want many domain-aligned dbt projects

Both types of organizations may read my recommendation of “align your dbt projects to your domains” and say,  “yes, let’s do exactly that!” and immediately proceed to create many domain-aligned dbt projects. To which I must say… “wait! Not yet.”  

Cue the disgruntled groans and disappointed sighs. To the organizations of the former type - those with old and overgrown dbt projects - you will only need to take a short pause. To the organizations of the latter type - those new to dbt - you will likely need a much longer pause (but only a pause! I promise you can get to multiple projects soon enough). Both are on the same journey, but one is much further along, while the other can get to the final goal (true mesh with many projects) much faster but still needs to go on the journey of adopting dbt in the first place.  

I know that dbt Mesh sounds very exciting and promising (and really, it is), but it also introduces a lot of complications that you really should not want to deal with until you absolutely have to. As dbt Labs DevEx advocate Benoit so elegantly [stated](https://getdbt.slack.com/archives/C04FP5LQA15/p1756225114294919?thread_ts=1756198154.211049&cid=C04FP5LQA15), “dbt mesh is about adding **good** friction to the data transformation process.” Adopting dbt introduces enough friction in the first place, and jumping straight to dbt Mesh may introduce too much friction - enough that the transition may fail entirely.   

All of this to say: if your organization is new to dbt, start in a single project. You can just architect this single project with the goal in mind that you will eventually transition to multiple projects. The adage of “slow is smooth, and smooth is fast” comes to mind - I promise that you will have a smoother time adopting dbt if you start with one project, and you will get to a *successful* dbt Mesh implementation faster than if you had started with multiple projects.  

So, let’s talk about how to design your single dbt project such that the transition to multiple dbt projects will be as painless as possible. Type 1 organizations (those with old & overgrown projects), this is what you want to transition your existing dbt project to look like. Type 2 organizations (those new to dbt), this is how you want to design your new dbt project from the ground up.  

First, use [groups](https://docs.getdbt.com/reference/resource-configs/group) to plan out your projects. Before creating one dbt project per domain, create a group per domain, and ensure every model belongs to a group. Planning is cheaper than doing (see: [How Big Things Get Done](https://www.penguinrandomhouse.ca/books/672118/how-big-things-get-done-by-bent-flyvbjerg-and-dan-gardner/9780771098437)), and groups provide a cheap (time is money!) way for you to plan out (and iterate!) your domain-oriented projects. Trust me - it is way easier to change what group a dbt model belongs to than the project it belongs to, and it is way way easier to change what groups exist than to change what projects exist. The group config can be assigned by folder in the dbt_project yaml file, and overridden on a model-by-model basis.  

Next, align your folder structure to your groups. You may already have a well organized dbt project and find that all models in the same folder belong to the same group - in that case, assigning groups and consolidating the folder structure will be very easy! But if you find that you need to assign groups on a model-by-model basis, then you are going to need to spend some time reorganizing your models and folder structure.   

The typical folder structure for a single dbt project is to organize by pipeline stage first - staging, intermediate, and marts as the top-level folders in the model folder. Then you should organize by source or domain inside those folders. As you get closer to migrating to multiple projects, however, I recommend flipping that structure: your domain (a.k.a all models in a single group, a.k.a all models that will be split out into their own project) should be your top level folders, with the pipeline stage folders (staging, intermediate, marts) replicated inside each top-level domain folder. If you are starting out in a new dbt project that you know will be split out later on, I recommend using this configuration to start with. This structure of top-level domain folders should be replicated across all of the top level dbt project folders (models, seeds, tests, macros, analyses).  

Once your project is organized by domain folders, you can start enforcing domain ownership within your git workflow by implementing a [codeowners](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners) file. Create teams in your git platform of choice that aligns with the domain-oriented team that will be owning the future domain-oriented dbt project (a.k.a the dbt groups). Any changes to folders belonging to that team must be approved in a pull/merge request by the team that owns it. Similarly, you can now start to slowly shift more and more dbt project ownership activities to these domain teams, like maintaining orchestration jobs, monitoring for test failures, etc.   

It can be easy to underestimate just how much work it is to manage a dbt project. It requires more advanced skills in git, dbt, and cloud platforms, and by slowly transitioning these responsibilities one at a time, you can provide a safe space for domain teams to advance these skills and figure out for themselves how they want to distribute responsibilities. This is one of the primary reasons I strongly encourage organizations new to dbt to start with a single project: to centralize and thus reduce this burden until enough people have the skillset required.  

Assigning your dbt models to groups provides another key advantage in drafting out your dbt projects: enforcing model access. By default, models have an access level of “protected” - they can be referenced by any other model in the same project. Once you have implemented dbt groups, you should change the default access level for models in your project to “private”, limiting only models within the same group to reference each other. Then, you will want to decide which models should be referenceable by models in other groups (and eventually other projects), and assign them to have an access level of “public”. These are the models that will turn into “data products” - more on that in the next section.   

You may encounter some errors in this process, as you realize that models with access level “private” were actually being used by other groups. This is a good thing! You are finding these errors now, while everything is still in the same project and errors are easier to resolve through refactoring or configuration changes, versus after migrating models into many projects (after which it becomes much more difficult to refactor and resolve).  

At some point, your groups will reach a point of stability, your domain teams will reach a point of self-sufficiency, and your public models will be mature enough that you can finally say: we are ready. We planned, we drafted, we prepared, and now we are ready to migrate into multiple projects. Even if domains do not reach this point on the same timeline, if you have followed my recommendations on your dbt project structure, pulling a single domain out into its own project one-at-a-time should be relatively easy. If you want to do it all at once, I recommend you check out [dbt-meshify](https://github.com/dbt-labs/dbt-meshify).   

Once you reach the end of this process and all of your domain teams have moved into their own dbt projects, don’t be so fast to deprecate the original project. You may have new domains who need help getting started with their own project, and the original project can continue to serve as an incubator - a project that is already set up, fully functional, and just needs the model files created. Much like when your organization was in the mesh transition phase, the original project provides a safe place for domain teams new to dbt to gradually learn how to manage their own projects. Furthermore, there may be a need for models that don’t fit neatly into one of the domains. The original project is a convenient place to stash them until ownership can be decided. 

### Data as a Product

The principle of Data as a Product is the one that has received the most attention and may be considered the most valuable or pressing to adopt. And while there is a lot to say about this principle and how to implement it with dbt Mesh, I will remind everyone that the four principles are designed to work together: if you focus only on this principle and forget the others, you may be producing data products but you will not be following the data mesh approach.   

According to this second principle, we should apply *product thinking* to domain-oriented data. Zhamak cites Marty Cagan’s book “[Inspired](https://www.svpg.com/books/inspired-how-to-create-tech-products-customers-love-2nd-edition/)”, which describes successful products being feasible, valuable, and useful. Data products should likewise have a common set of characteristics that make them usable, valuable, and feasible - and Zhamak outlines the eight characteristics she believes are fundamental to data products:

1. Discoverable  
2. Addressable  
3. Understandable  
4. Trustworthy & Useful  
5. Natively Accessible  
6. Interoperable  
7. Valuable on its own  
8. Secure

These eight characteristics are inclusive of and expand beyond the older concept of [FAIR data](https://www.go-fair.org/fair-principles/) - Findable, Accessible, Interoperable, & Reusable - to include the traits necessary in a distributed system. (However, FAIR is a much easier acronym to remember than DAUTNIVS!).  

Beyond these characteristics and the technical methods to implement them, Zhamak highlights the cultural shifts needed to truly treat data as a product, vs treating data as an asset. Success should not be measured simply by vanity metrics like how many “data products” exist or the volume of data (measures that assume data is valuable by virtue of its very existence), but rather in how many people are using the data products and their satisfaction with the experience of using the data. Quality data products need continuous care and curation, and furthermore, this care should be administered by the domain-oriented teams that are producing it in the first place, not by downstream centralized data teams that often lack needed context for the data.  

In other words, you cannot simply declare a table in one of your mart schemas to be a data product by virtue of its existence. That is “data as an asset” thinking, not “data as a product” thinking. Instead, you should carefully consider how (and whether!) you can evolve this mart model to meet each of the eight characteristics of a data product.

#### Applied to dbt

Not every model in a dbt project should be considered a data product - nor do you want them to be. So, which models are our candidate data products? Most likely the models living in your marts (or equivalent) layer, which have an access level of “public” (assuming you followed the recommended steps from applying the first principle of Domain Ownership to dbt). These are the models that live at the intersection of projects, the models that other projects will use as cross-project references. These are the models that other teams are going to use - teams that lack the domain knowledge and development context that your team has. All of this means that these models should adhere to a stricter set of rules and documentation standards than models reserved for internal use. Your goal should be for another domain to successfully use your data product without ever needing to contact your team. So, let’s use the eight fundamental characteristics of data products to determine the rules mart models should follow in order to evolve into true data products.

##### Discoverable

When a user is browsing a catalog of data products and needs to find one that will suit their needs, a discoverable data product can be easily surfaced during this search. The data product itself should include the necessary and standardized metadata needed to enhance discoverability. In dbt, this metadata is provided in the model yaml file. While dbt does not require any metadata to be provided, there is a standard set of [properties](https://docs.getdbt.com/reference/model-properties), as well as the extremely flexible [meta](https://docs.getdbt.com/reference/resource-configs/meta) config. Your team should decide on the minimum acceptable metadata needed for a mart model. Furthermore, the more detailed your descriptions, the more discoverable your model will be. Having a controlled vocabulary can also aid users in discovering the right data products. Try putting your librarian hat on when crafting the metadata for your models ;)

##### Addressable

Functionally, this means that a data product should have a permanent and unique address (and/or id). You get this by default with dbt, as all model names must be unique within a project. The model name also serves to group together all relevant information about the model in the catalog. One implication of this, however, is that once a mart model is considered a data product, its model name should not change. The relation name in the database can change via the [alias](https://docs.getdbt.com/docs/build/custom-aliases) config, but the model name should remain consistent. [Model contracts](https://docs.getdbt.com/docs/mesh/govern/model-contracts) can enforce this, among other things, with [model versions](https://docs.getdbt.com/docs/mesh/govern/model-versions) providing a way to change the model over time without breaking references. The [deprecation date](https://docs.getdbt.com/reference/resource-properties/deprecation_date) should be set for individual versions and the root model prior to the model being removed (and at this point, changing its name is equivalent to removal).

##### Understandable

Once a data product is found, in order to use it, the user must be able to understand it - its context, its meaning, the entities and relationships involved, and how to relate it to other data products. In other words, it must be well documented! A few sentences in the description field are really not sufficient. This is where [doc blocks](https://docs.getdbt.com/docs/build/documentation#using-docs-blocks) can come in handy. Beyond enabling the DRY principle to apply to documentation, doc blocks are a great mechanism to isolate the description into a markdown file, which can be lengthier and include standard markdown formatting. You can even include images and diagrams! Your team should decide on a standard for documentation of data products that will allow users to independently and successfully use the data. Table and column names should follow clearly documented naming conventions. You may find that using doc blocks can help consolidate columns that mean the same thing but have slightly different names! I also highly recommend making writing documentation someone’s entire job - technical documentation is its own specialty, and it requires a different perspective to write documentation for the end users. Hire a documentation specialist!

##### Trustworthy & Truthful

Zhamak cites Rachel Botsman’s concept of trust, and states that “a data product should close the gap between what data users know confidently about the data, and what they don’t know but need to know to trust it.” One way to do this is to attach service-level objectives & agreements to the data product, where uncertainty is measured and some degree of certainty is guaranteed. Users want to know how often the data is updated (and the gap between the time the data is updated and when business fact happened in reality), how complete the data is (measuring nullness across key fields), basic descriptive statistics, and data lineage. Within dbt, [data tests](https://docs.getdbt.com/docs/build/data-tests) and [freshness checks](https://docs.getdbt.com/reference/resource-properties/freshness) are a way to measure and enforce some of these SLAs. (In fact, there were some very exciting announcements at the Coalesce 2025 keynote on setting freshness SLAs and smart dbt test execution using column level lineage!). 

Beyond the basic dbt tests you get out of the box, dbt packages like [dbt-utils](https://hub.getdbt.com/dbt-labs/dbt_utils/latest/), [dbt-expectations](https://hub.getdbt.com/metaplane/dbt_expectations/latest/), and [elementary](https://hub.getdbt.com/elementary-data/elementary/latest/) allow analytics engineers to easily add sophisticated tests to models and columns. By carefully adding these tests prior to the mart, deciding when they should error vs warn, and materializing the marts as tables (not views), you can ensure that the data available in a mart meets data quality agreements. With robust observability using packages like [elementary](https://hub.getdbt.com/elementary-data/elementary/latest/) or other products like [Metaplane](https://www.metaplane.dev/) (now a Datadog company) and established triage processes when issues inevitably arise, you can identify and resolve data quality issues before they ever reach the user. And of course, data lineage features are included out of the box in any dbt project.

##### Natively accessible

For a data product to be natively accessible, it should be available in wherever and in whatever format the user needs it. Since dbt has traditionally operated within a single platform, your data product would only be available as a table/view within a database. However, there are two features that address this limitation: [cross-platform Mesh](https://www.getdbt.com/blog/introducing-cross-platform-dbt-mesh) via [Iceberg support](https://docs.getdbt.com/docs/mesh/iceberg/apache-iceberg-support) and the dbt [Semantic Layer](https://docs.getdbt.com/docs/use-dbt-semantic-layer/dbt-sl).    

If you materialize your data product model using an Iceberg materialization - and assuming you are on a platform that supports Iceberg - users can now access that data from their own data platform (assuming their platform also supports Iceberg). Open table formats are changing the game around accessibility and interoperability - at least that is the vision that we seem to be on our way to realizing. Until support is more widespread and reliable, additional infrastructure may still be needed to move data between platforms.  

If you create a semantic model for your data product model and define the metrics that can be calculated on it, your data product becomes accessible in many different BI tools (again, subject to the BI tool’s support of the semantic layer). This opens up the world of dashboards and even spreadsheets to analysts who want to use the data product.

##### Interoperable

While each data product should be self-sufficient and usable on its own, it should also be able to be used together with other data products. The closest that dbt gets to offering a feature to serve this characteristic is the semantic layer - you can identify your entities across your models and how they can be related together, with the semantic layer handling how to query the underlying tables in order to produce the desired metrics sliced and diced any which way you want (as long as these dimensions are defined in the semantic layer). 

However, the bulk of the work in making data products interoperable relies on you, the analytics engineers, data modelers, and data architects. It is up to you to model your data in a sensical way, to have understandable and consistent naming conventions, and to document your data products well and focus on how they should be related to each other. You should go through the exercises of conceptual data modeling and even master data management to make sure that the entities defined in one domain (project) match up to the same entities defined in another domain (project). I do think that dbt has room to grow in better enabling interoperability: for example, while the data lineage graphs are extremely useful when it comes to tracing the provenance of a data product, they are not so useful when it comes to querying the final product. I’d love to be looking at the documentation page for a mart model and be able to see the star schema diagram as well!

##### Valuable on its own

This principle seems self-explanatory on the surface, but it has some interesting implications for data product developers. For a data product to be valuable on its own, all components of a data product must be packaged up and considered together: the data, the code, the documentation, and even the infrastructure that produces it all. Zhamak defines a new unit of logical architecture, the “data quantum”, which encapsulates all of the structural components needed to build, publish, and share the data product. Within dbt, this means that your “data product” is not simply your sql model file - it is the combination of the sql file, yaml file, markdown files with any associated doc blocks, the data in the database created by the dbt model, and even the entire upstream lineage of models that produce the final data product model. One interesting implication here is that in a data mesh world you may want to shift from orchestrating dbt projects to orchestrating individual data products. The updates that will be made to dbt core to support state-aware orchestration should be in line with this shift towards model-centric orchestration.  

Zhamak also uses this principle to caution against lifting and shifting your dimensional data model into data products in a data mesh. While data products should be able to be joined to each other, they should not *have* to be joined prior to being useful. When you think about your traditional star schema, usually you must join dimensions to your fact before it can really be used for analysis. So, you should not consider your typical “fact” table to be a data product - rather, the entire “star” is the data product. There are some interesting implications here: you may want to have a standard 4th layer between your intermediate and mart layers for these facts and dimensions, leaving the mart layer to follow the “One Big Table” methodology and pre-joining needed dimensions to your facts to form the final data product. Or perhaps you leave your facts and dimensions in your mart layer and introduce a new “product” sub-layer to follow it. Regardless, if you choose the data mesh approach, this must influence your data modeling methodology. 

##### Secure

Since we have already established that a pure dbt implementation of data mesh is limited to the medium of relations in a database (see principle 5, natively accessible), this principle is likewise limited to database security capabilities. Zhamak states that access control policies should be defined centrally but enforced at runtime by the data product, taking into account the level of access any individual may have. Fortunately, modern data warehouses can have quite complex and expressive access control policies. However, to truly take advantage of these, you will want to look outside of dbt, and use a tool like Terraform instead. There are some excellent resources on how to use terraform with dbt and data warehouse platforms, such as [Katie Claiborne’s talk at Coalesce last year](https://www.youtube.com/watch?v=6les3dVoYh0). The one dbt feature it is important to be aware of in respect to security is the [grants](https://docs.getdbt.com/reference/resource-configs/grants) config. However, at the scale of users participating in a data mesh, you’re likely to quickly outgrow the capabilities of the grants config alone, as you seek to centrally manage access control policies for your data platform in a way that can be “versioned, automatically tested, deployed and observed, and computationally evaluated and enforced” - for this, you need a tool like [terraform](https://developer.hashicorp.com/terraform) (or [OpenTofu](https://opentofu.org/)).  

One last side note: while it is not available yet, the future dbt Fusion capability of tracking PII via project-wide column lineage will be highly relevant to this principle (when it is available).

##### Score your data product models

So, let’s summarize the actions you should take in order to evolve your mart models into data product models:

1. Data product models should have model access set to “public”.  
2. Data product models should have enforced contracts, which means any changes applied needs to go through the model versioning process, and before a model can be removed it must go through the deprecation process.  
3. Data product models should be thoroughly documented, at both the model and column level, such that a new user could successfully use the data product as intended based on the available documentation alone. It’s highly recommended that doc blocks be utilized in the documentation process.  
4. Data product models must be tested - and these tests should occur upstream of the final data product model, with all assertions that are tested documented with the data product model, and the results of these tests made available. (sidenote for the dbt product team: make it easy to see what upstream tests were run!)  
5. Data product models should have a standard set of metadata fields that provide further context and enable discoverability (pro-tip: include data product owners in this metadata)
6. Data product models should be useful on their own, with all needed columns already included (OBT methodology over Kimball). Don’t just call your fact and dimension mart models data products - create new models that join them together.  
7. Data product models should have explicit documentation about who has access to the data, and this should be enforced via grant configs.  
8. If possible and needed at your organization, materialize the data product model as an iceberg table.

This is a lot! Data products require a lot of careful curation, and this requires time and effort. We want to evolve our mart models into data product models iteratively, not all at once (or it will never happen!). So let me make a further suggestion: develop a scoring system for your data products. Whether it be a 5-star rating, “medallion” score, or low-to-high maturity rank, have an agreed upon methodology for scoring your data product models, and surface this to users. You don’t want a user to expect the same thing from a 1-star model that meets the bare minimum standard of having access = public as they do from a 5-star model that is tested and documented up the wazoo. Utilize a [meta config to document your model maturity](https://docs.getdbt.com/reference/resource-configs/meta#designate-a-model-owner). I’m not going to tell you what your scoring system should be, but I am going to tell you that you need to get together with all of your teams across the mesh and agree on one.

### Self-serve Data Platform

The principle of Self-serve Data Platforms is not, as you may initially think, about “self-service analytics”, enabling end users to access and use the produced data products. Instead, it is all about enabling the domain teams to produce those data products in the first place. This third principle is essential to making the first two principles actually work in practice. Without a self-serve data infrastructure as a platform, decentralized is just a synonym for fragmented, and domain ownership over data starts to feel like an untenable burden. Organizations that focus on the first two principles of data mesh will soon find themselves falling back to previous patterns, and return the onus of data management to a centralized data team.  

What does a self-serve data platform look like? Primarily, it should make it easy for a new domain team to go from 0, to 1, to many published data products. Publishing that first data product should not require going through a central team to set up infrastructure - teams should be able to accomplish this independently, without needing deep specialized technical expertise. There should be a low barrier to adoption, and integration with other systems (namely, operational systems) should be as seamless as possible. And while working with this platform should be as easy as possible for generalists (or rather, those with specialties besides data) to work with, it must not compromise on software engineering best practices of testing, versioning, and modularity.   

However, the platform must enable all of this… while being decentralized. Zhamak posits that there are very few existing platforms/technologies that meet these requirements, as most platforms currently in vogue are highly centralized. She argues that centralization only introduces bottlenecks that slow down the speed of change & innovation. A self-serve data platform must strike the right balance of enabling decentralized data ownership while only centralizing the most essential tasks and resources so that domain teams can operate at a higher level of abstraction. Furthermore, the self-serve platform must centralize enough of the underlying services that data products developed by different domains remain interoperable.

Supporting all of this is a platform team. If you do not already have a platform team in your organization, this may be what your centralized data team evolves into. It is the responsiblity of this platform team to support all of the features and tools needed by all domain teams. It is the platform team who should support the dbt resources I'm about to recommend in this next section.

#### Applied to dbt

Before describing how you should apply this principle to dbt, I must first acknowledge something: I think it is highly unlikely that Zhamak would agree that is even possible to create a self-serve data platform in accordance with her vision using dbt. Zhamak has spent a considerable amount of time and effort creating her vision of a true self-serve data platform with her company’s product, [Nextdata OS](https://www.nextdata.com/product).   

So, I am not going to even try to recommend you implement this principle with dbt, especially with respect to the decentralization component. Instead, I am going to focus on a sub-principle: that it should be as easy as possible for new domain teams to get started producing their first data products.   

First, I want to point out some of the excellent product developments out of dbt Labs that have made it easier than ever for non-data specialists to contribute to dbt projects - products that you should be making full use of if you are a dbt Labs customer. Then, I’ll outline some specific suggestions that you can implement in your organization to make it easier for other teams to manage their own dbt projects and start producing data products.  

##### dbt Product shoutouts:

- The [dbt Studio IDE](https://docs.getdbt.com/docs/cloud/dbt-cloud-ide/develop-in-the-cloud) and [dbt VS Code extension](https://docs.getdbt.com/docs/about-dbt-extension) (also, big shoutout to Altimate AI for their work in developing & maintaining the [dbt Power User extension](https://docs.myaltimate.com/) for VS Code). These tools make the experience of developing within a dbt project smooth and the Studio IDE in particular walks new developers through the necessary steps in a user-friendly way.  
- [dbt Canvas](https://docs.getdbt.com/docs/cloud/canvas) for opening up dbt projects to contributions from those who feel uncomfortable with code and prefer a GUI-centric drag & drop interface. Bonus shoutout to [dbt Copilot](https://docs.getdbt.com/docs/cloud/build-canvas-copilot) for further enabling these users to still contribute to the underlying codebase.  
- [dbt Insights](https://docs.getdbt.com/docs/explore/dbt-insights) to more easily enable users to query and explore data - think ad-hoc analysis with superpowers from the additional context of your project’s documentation, metadata, and an assist from AI.  
- [dbt Semantic Layer](https://docs.getdbt.com/docs/use-dbt-semantic-layer/dbt-sl) for enabling analysts to define and correctly query metrics across different dimensions in their BI tool of choice (so long as it is a supported option)  
- [dbt Catalog](https://www.getdbt.com/product/dbt-catalog) for providing the best presentation layer of dbt projects, turning version-controlled code repositories into documentation that is easy for users to explore and discover data products they can use - as well as all of the context that goes with it.  
- The [dbt Learn Course Catalog](https://learn.getdbt.com/catalog) for providing the best self-serve courses (all free!) to learn every aspect of dbt - both the open source dbt Core and paid products.

Now, I will acknowledge that it is very much in dbt Labs’ self-interest to lower barriers of entry and make it easy for a wider user base to adopt their products. However, I think they have done an excellent job at striking that balance of lowering barriers to entry while not compromising on the software engineering best practices that they brought to data management - a core part of their founding mission. On the other hand, these dbt products all belong to one centralized platform - they certainly do not embody the principle of decentralization that Zhamak emphasizes. Perhaps at some point there will be an integration between dbt and Nextdata OS, and we can see what it looks like to develop data products using dbt on a true decentralized self-serve data platform that fully embodies the original data mesh vision.  

I’ll also mention that some of these tools are likely to have widely varying adoption across your teams, and can significantly impact the code that gets committed to your project. So you may want to keep this in mind when deciding what your domain projects look like - a team of downstream marketing analysts may want to make heavy use of dbt Canvas for developing their dbt models, and this will influence what the sql in their models looks like. This is not a bad thing - and this team should be able to operate with their tools of choice! The self-serve data platform should enable all of these types of workflows, while the principle of *federated* computational governance protects the independence of domain teams (within the bounds required for interoperability).  

##### 3 things your platform should build/support

Now, let's move on to some suggested dbt Mesh best practices that will also help your organization strike the right balance between decentralized domain-oriented dbt projects and centralized support for those projects.  

**Pro-tip #1:** create an internal dbt package. You have used public dbt packages before from the [dbt Package Hub](https://hub.getdbt.com/) (I dare you to find someone who hasn’t at least used dbt-utils), but did you know that you can also create your own dbt packages purely for internal use at your organization? And it’s easier than you may think - after all, a dbt package is just a dbt project. There are number of great resources on how to develop a dbt package, including [this official guide](https://docs.getdbt.com/guides/building-packages?step=1), [this tutorial](https://docs.getdbt.com/blog/so-you-want-to-build-a-package) from dbt PM extraordinaire Amy Chen, this [past Coalesce talk](https://www.youtube.com/live/Bp6keIz0Jvc?si=sjmGmFzDSL8K623X), and [this blog post](https://www.phdata.io/blog/how-to-use-a-dbt-package-in-your-project/) from phData.   

What does an internal dbt package get you? Code sharing between all of your projects in the mesh. The top use case is macros: there are going to be certain macros that you want available to all projects - and you only want there to be one version of it (imagine the confusion if everyone developed their own version of a macro that performs a common transformation… in slightly different ways!). Macros can go through a promotion process - one domain project may develop a new macro, iterate on it, generalize it, and then add it to the internal dbt package when another team has a use for it as well. Custom generic tests are just macros - you can create standarized custom tests for the whole mesh to use as well. There may also be certain models you want made available to everyone - for example, a common reference table made queryable through a seed + model in the package. It is up to your organization to decide what code would be useful to be centralized and shared across all projects, and decide on a process for what code gets added to this centralized repository.  

**Pro-tip #2:** create a dbt project template. There are a number of ways to do this, ranging in sophistication. It may be as simple as a repo with a standardized dbt project setup that can be forked, or as sophisticated as a terraform template that can set up the new dbt project & all related infrastructure. Katie Claiborne gave an [excellent talk at Coalesce](https://www.getdbt.com/resources/coalesce-on-demand/coalesce-2024-why-analytics-engineering-and-devops-go-hand-in-hand) last year about exactly how to do this! Regardless, the goal is to make it fast, easy, and efficient to create new dbt projects that comply with all expectations your organization has of a dbt project in the mesh. With infrastructure-as-code tools like terraform, this setup is reproducible and version controlled.  

**Pro-tip #3:** create a dbt project (or multiple projects) that are only for the purpose of learning dbt. While dbt Learn offers many amazing courses, learners are still meant to follow along by creating their own projects to practice on. By pre-creating these learning projects, you are reducing barriers for new dbt contributors. My recommendation is to do the set-up steps for the lessons, and then ask learners to create their own branches in that dbt project repo in order to complete the course and follow along. They may submit Pull/Merge Requests for their work to be evaluated, but learners should be blocked from merging any of these changes to main - the main branch should remain clean for any new learner to create a branch and progress through the course from the beginning on their own.   

For the dbt Learn course developers/maintainers: it would be lovely if y’all could consolidate the various course-specific dbt projects in order to minimize the total number of “learning projects” that need to be set up. There are many different versions of the Jaffle Shop project out there!

### Federated Computational Governance

Finally, we arrive at our fourth and final principle: Zhamak’s modern re-imagining of data governance for the data mesh, Federated Computational Governance. Zhamak’s approach uses systems thinking to govern the mesh, balancing the autonomy of decentralized domains with the harmony of global interoperability. The challenge is in finding equilibrium while the two opposing forces fight for optimization. Zhamak was inspired by Donella Meadows’ “[Thinking in Systems](https://donellameadows.org/systems-thinking-book-sale/)”, and describes how to use feedback loops to adjust behavior and leverage points to adjust the strength of those feedback loops and significantly impact the overall system. In a large-scale distributed and dynamic system like a data mesh, it is essential that traditional data governance evolves to become federated and automated.  

To become automated, policies that were previously enforced by manual intervention must now be enforced automatically by the platform (and this means these policies must be expressed in such a way that they can be automatically enforced - as code). For example, a standard might be that all models should have a primary key test. A policy might be that all PII data must be masked.   

To become federated, domains must be allowed to create their own policies to some extent (primarily around how data products are created, maintained, and served), while also adhering to some minimum viable set of global policies & standards (primarily those that facilitate interoperability). As a reminder on what “federated” means, think of the governance model outlined by the US Constitution: the federal government sets certain policies/laws that apply across states, but state governments have the power to set policies/laws that apply only to people in their state (so long as compliance with federal laws is maintained. If not... that's what the Supreme Court is for).  

Standards and policies are code - administered, enforced, and customized locally after inheriting from global policies - and this code should be subject to the same agile principles as other software: easy to change, iterate, and evolve.

#### Applied to dbt

If there is one key leverage point to adjust people’s behavior when contributing to a dbt project, it is during a Pull/Merge Request. The [CI/CD process](https://www.getdbt.com/blog/adopting-ci-cd-with-dbt-cloud) as a whole is a feedback loop, and the event of a CI job passing or failing is a leverage point. It is an excellent demonstration on how policies can be defined in code and enforced automatically.   

A [typical setup](https://github.com/savannah-dbt-labs/sharing_is_caring) for a dbt project looks something like this: when a Pull/Merge Request is opened, a [CI job](https://docs.getdbt.com/docs/deploy/continuous-integration) is automatically kicked off. This CI job should either build all new/updated models and their downstream models ([slim CI](https://docs.getdbt.com/best-practices/best-practice-workflows#run-only-modified-models-to-test-changes-slim-ci)) or the entire project (inefficient, but ok for smaller projects with no way to handle state or deferral yet), in an isolated environment (typically, a new schema is created for the PR, then dropped after the PR is merged). Note that if you have enforced model contracts in your project, any violation of the contract will cause the job to fail. If the dbt job is successful, you can safely merge the code to main (or a develop branch, depending on your [git strategy](https://docs.getdbt.com/blog/git-branching-strategies-with-dbt)) - after a code review by a human as well. CI jobs offload some of the burden from human reviewers, by letting computers do what computers are good at (making sure code runs without error).  

On the surface, requiring a successful CI job prior to merging code to main is a way to protect against bugs that could cause production jobs to fail. However, you can test for more than just the fact that models run successfully - you can also test that the code follows certain agreed upon standards. This is where the [dbt Project Evaluator package](https://hub.getdbt.com/dbt-labs/dbt_project_evaluator/latest/) comes in handy.  

The [dbt Project Evaluator](https://dbt-labs.github.io/dbt-project-evaluator/latest/) turns your dbt project(s) into data - and then builds dbt models on that data and tests for certain assertions. While dbt Project Evaluator comes with a standard set of policies it enforces out of the box, you are able to customize which assertions it tests for and even the parameters for some of those tests. For example, let’s say that your team has an expectation that every model should have a primary key test. Typically, it would be the human reviewer’s responsibility to ensure this policy is followed. However, with dbt Project Evaluator enabled and run during the CI job, the [missing primary key test](https://dbt-labs.github.io/dbt-project-evaluator/latest/rules/testing/#missing-primary-key-tests) will fail if any model is missing a primary key, thus preventing a merge until the issue is resolved.   

One useful side effect of using the dbt Project Evaluator package is that your dbt project - the actual code repository - is modeled out and materialized in your database. This means that you can build further models and tests on top of these Project Evaluator models, in order to enforce custom policies that are not included out of the box in [Project Evaluator’s ruleset](https://dbt-labs.github.io/dbt-project-evaluator/latest/rules/).  

And if you have multiple dbt projects, all with dbt Project Evaluator enabled for staging (or production) jobs, you can put these project-specific tables together to form a cohesive dataset about the entire mesh. And then you can test new and interesting things in this comprehensive set of tables - in other words, you create mesh-wide tests. For example, let’s say that you only want one project in the mesh to use a given table as a source (in order to reduce duplicative and possibly diverging efforts). This mesh-wide test is now possible to run and enforce once you create the model that sources in and consolidates the Project Evaluator core models across all projects.  

Once your dbt project - the code itself - is data that can be queried and tested, the possibilities are endless. And a great place to put these mesh-wide tests and models? In your internal dbt package, which should be imported by every domain project, enabling these mesh-wide tests to be run during the CI job as well. I would further suggest that you turn your internal dbt project into a full project, with its models materialized in the database in a single permanent location, as this will make it much easier to query and monitor the status of data products across the mesh. (Remember: CI schemas should be dropped after the PR is merged, so you can’t build permanent infrastructure on models built just during CI jobs).  

Here comes another request for the dbt Labs team: it would be amazing if default project configurations (think: the configs that you set in your dbt_project.yml file) could be inherited from that internal dbt package (which evolves into a central project that underlies the entire mesh). While code can be imported from packages (models, macros), configurations cannot - but it would make setting up and governing the mesh easier if they could be!

## People and Process

As I’m sure you’ve noticed while reading this blog post, there are a lot of decisions to be made about how, exactly, your organization will decide to implement dbt Mesh. And when you are operating at the scale of a mesh, with governance and ownership distributed across the domains, it is no longer feasible for a single leader or centralized governance team to make these decisions for everyone. While it may be tempting to put the responsibility of crafting data mesh governance policies on the existing (likely highly centralized) governance team (or, conversely, to leave them out completely!), please resist the temptation. Instead, you need a “federated team of domain product owners, subject matter experts, and central facilitators.” Identify a core group of decision makers that allows for every domain to be represented, and charge this group collectively with crafting the policies, making decisions, and steering the development of the mesh. Start to transition data stewards from the centralized governance team into the domains, and pull domain data product owners into the new (federated!) mesh governance team. (Note: this federated mesh governance team is an important component of the fourth principle).  

In short - you need to convene your mesh! Let’s review some of the decisions this Mesh Governance Council will need to make, one principle at a time.

### Decision time

#### Domain Ownership

- What qualifications must a domain team meet in order to manage their own dbt project? 
- Who determines when they have met these qualifications? 
- Who manages the creation of the new dbt project and the migration of models into it?

#### Data as a Product

- What is the scoring system that will be used to rate data product models? 
- What qualifications does a model need to meet in order to reach the next level? 
- Who is able to make this determination, and how is this score represented in the model metadata? 
- What other metadata is expected for all data product models across all projects?

#### Self-serve Data Platform

- Who is responsible for maintaining the internal dbt package? 
- Who can contribute to the internal dbt package? 
- When should code be promoted from being managed in domain dbt projects to being generally available in the internal dbt package? 
- Who is responsible for creating and maintaining a dbt project template? 
- Who is responsible for making sure existing dbt projects get any needed updates after changes are made to the template? 
- Who is responsible for supporting new dbt learners, and maintaining the learning projects?

#### Federated Computational Governance

- Who will be monitoring the health of the overall mesh, and making sure that individual domains and projects are adhering to the mesh-wide policies? 
- How will issues be detected, and who is responsible for ensuring those issues get resolved? 
- What will the standard CI job look like across dbt projects, and when can CI jobs diverge from this standard template? 
- What is the standard suite of tests dbt Project Evaluator should run for all projects, and in what tests can individual projects have more flexibility? 
- Who is responsible for setting, maintaining, and monitoring the mesh-wide tests?

### Map out your process

Hopefully these questions clarified that the transition to a dbt-powered data mesh introduces a lot of new problems and complexities… ones that will take time, iteration, and input from every participating dbt project team to solve. I would highly recommend mapping out the process that the teams should follow in order to craft new policies and solve each problem. (Shameless plug: helping teams figure out what this decision-making process would look like for a dbt Mesh environment was the goal of [my peer exchange at Coalesce in 2024](https://jennajordan.me/projects/dbt-mesh-council-simulation)!)  
Here is an example of what this process may look like at one organization:

1. Someone (hereafter the Champion) brings a proposal to the Mesh Governance Council.
2. The Council can either reject the proposal immediately (process stops), or let it go forward.
3. If the process goes forward, the Council evaluates whether this is a major or minor proposal. In essence, a minor proposal can be approved immediately, while a major proposal requires a working group to flesh out the details.  
4. If the proposal is minor, the proposal is either approved or rejected by the Council (by a vote or some other decision making function).  
5. If the proposal is major, the Champion forms and leads a working group, recruiting interested parties. This working group crafts the proposal, and gathers feedback. When they are ready, they bring this detailed proposal to the Council.  
6. Once again, the Council decides whether to reject (process stops), request changes (process loops), or approve the proposal (process moves forward).  
7. The proposal may need to go through additional approval processes, depending on the organization’s requirements. The Council determines what further approval processes the proposed policy needs to go through. If the policy is rejected by any other approving body, the Champion and working group can decide whether to stop or loop back through the process again with revisions.  
8. Once the policy has all needed approvals, the final version of the policy should be thoroughly documented and stored in a central and accessible location. This final policy should also include the planned (automated if possible) enforcement mechanism. The policy should be communicated out to all projects, along with an expected timeline for compliance. (Pro-tip: the internal dbt package - which may double as a central monitoring project - would be a great initial place to put these policies as markdown files!)  
9. Individual domain teams can petition the Council for exceptions to the new policy. The Council decides whether to approve or reject these petitions.  
10. New mesh-wide tests (or other automated enforcement mechanism) should be implemented according to the communicated timeline and any approved exceptions. I highly recommend a gradual approach - set tests to warn for a period first, before transitioning the tests to error on failure.

As a reminder, this heavier process should only be needed for policies that must apply across the mesh for the sake of interoperability. Individual domains should be able to set their own policies internal to their projects in a much faster and lighter process. Mesh-wide policies should lean towards being minimal, with individual domains empowered to enforce stricter policies for their own projects.

## Wrapping Up

I hope that you walk away from this blog post (and accompanying talk) also convinced that dbt Mesh + data mesh is a strong approach for organizations using dbt to manage data at scale. I also hope that I’ve caught you at the right time in your dbt Mesh implementation journey, and you can put into practice some (or all!) of the suggestions I’ve made. Of course, while this is (naturally, for me) an absurdly long blog post, I can only cover so much, and I’m limited by my own experiences. I would love to hear from y’all if there is anything I should add - if you have any pro-tips for the others who have chosen to adopt data mesh by way of dbt - please reach out and let me know!

## Appendix

<div class="row">
    <div class="col-sm md-auto">
        <a href="/assets/pdf/so-you-want-to-build-a-data-mesh.pdf">
        {% include figure.html path="/assets/img/header_data-mesh.png" title="Coalesce Talk Slides"  class="img-fluid rounded z-depth-1" %}
        </a>
    </div>
</div>
<div class="caption">
    PDF of the slides presented during the talk
</div>

<div class="embed-responsive embed-responsive-16by9">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/yKScVw4gVfo?si=e0el1KQG8u0Xaol2" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>
<div class="caption">
    Official recording of "So you want to build a data mesh" on YouTube
</div>
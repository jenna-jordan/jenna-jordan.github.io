---
layout: post
featured: false
title: Analytical Data Warehouses - an introduction
date: 2023-08-13
description: what? how? why? data warehousing for analytics, explained (mostly)
permalink: /blog/analytical-data-warehouses
toc:
  sidebar: left
thumbnail: assets/img/header_data_warehouses.jpg
categories: data essays
---
{% include figure.html path="assets/img/header_data_warehouses.jpg" class="img-fluid rounded z-depth-1" %}

When I first started working on the City of Boston Analytics Team, I had never really worked with an analytical data warehouse before. I had experience with databases, and with the data flow in analytics projects (mostly using pandas, in jupyter notebooks), and I had used databases as a starting point for analytics projects, but I had not yet put all of those pieces together. Then I started working as a data engineer whose primary role was to operate within an analytical data warehouse, and I took a 4-week crash course in dbt... and my brain went into overdrive trying to sythesize everything I already knew and was learning in order to come up with a mental model of what an analytical data warehouse was, how it should operate, and why. Now, almost two years later, I'm pretty sure I get it - and I want to share how I conceptualize a data warehouse in hopes that it makes the journey easier for anyone else who may be in the same position I was. 

But first, a couple caveats: 
1. I'm still learning, and I know my understanding will continue to evolve as I continue to learn
2. This is largely influenced by how my team uses our data warehouse, and it may be different for other teams

## Databases vs data warehouses, transactional vs analytical (the what, and why)

An analytical data warehouse is the data source that powers analytical outputs - dashboards, reports, one-off statistical analyses, machine learning models, etc. Having a data warehouse makes sense when you are working in a team - you often need to share data, pick up other people's projects, and know that an analytical output will continue to function even after a project is wrapped up. Having a reliable, managed, and shared infrastructure is a huge productivity boost. Also, pretty much every BI tool is built to at least connect to a database.

But what makes a data warehouse different from a (relational) database? In large part, this is simply a matter of semantics. Any database can be a data warehouse, it all comes down to how you use it. If you are using a database for analytics, you are likely doing a lot more and more complicated queries to read from the database. If you are using a database to power an application, you are doing a lot more (and need faster) writes to the database. Transactional databases are optimized for writes, and analytical databases are optimized for reads. Some DBMSs are balanced and can be used for both (i.e. PostgreSQL). Others optimize heavily for one use case (Snowflake is pretty much only used for analytics). How you are using a database also dictates how you organize it. If you are using a transactional database to power an application, there is a very good chance your database is normalized (most typically into 3rd or Boyce-Codd Normal Form). 

Normalizing your data is the best way to organize your data when you want to reduce the duplication of data, avoid data anomolies for inserts/deletes/updates, and ensure relational integrity. But the normalized structure can make it difficult to answer seemingly simple questions - you often have to write complex queries with many joins. And analytics is all about asking questions of your data.

If you are using your database to answer many different analytical questions, you probably have many different data sources - and many of those data sources may be completely different from each other and never intended to be joined together. This is when a database starts to become a data warehouse - rather than one cohesive place to store data for one purpose (and therefore the data is all related), the data warehouse is more like a data repository. It is stored in a single place because of the convenience, not because the data is necessarily related (though some if it certainly will be). 

In a well-designed relational database, it is usually pretty easy to understand how data is organized and linked through primary and foreign keys. You don't necessarily need to know the data to query it so long as you know the structure. But an analytical data warehouse is not so easy to comprehend. There are almost never foreign keys, because they introduce complications to the ETL processes that update the data. If you are lucky, there are primary keys on some of the tables. To understand how an analytical data warehouse is organized, you instead need to look at the transformation flow.

## The transformation flow (the how, and why)

If you have worked on enough code-based analytics projects, you have probably learned the value of maintaining a proper data transformation flow. This may show up in how you organize your data folder: you have your "raw" data that is never to be altered, your cleaned/processed data that is an intermediate output, and your final data. You learn the value of using code to transform data - it means all transformations are documented, replicable, and easy to alter. Your notebooks/scripts are a mix of exploration, small cleaning tasks, and big transformations. You may have some functions in there for transformations that need to be performed repeatedly or to encapsulate more complicated code. You are displaying chunks of dataframes in order to visually examine the results and decide what needs to be done next. You are also saving dataframes to CSVs to be used elsewhere.

All of these elements show up in the analytical data warehouse as well - they just look a bit different. No matter where the data lives, analytics data work should follow a set of core principles that cement data management best practices in the analytical output.

### Principles of data management

1. Preserved raw data: raw data should be a direct copy of the source as much as possible, and should not be altered (besides being updated with new data)
2. Replicable transformations: all transformations of the raw data should be replicable/documented (the SQL/python code is saved, preferably in a git-tracked central repository) and automated if needed (transformations performed on a schedule in line with data imports)
3. Tested production data: all data considered "production" (ready for analysis) should be able to pass tests of data quality. These tests should be documented and automated if needed, like the transforms

### Preserved raw data

When raw data is loaded into a data warehouse via an ETL process, it is loaded in a "source" table. Different teams have different names for this set of tables - "base", "staging", etc - but I will use "source" for the sake of simplicity/consistency. These source tables are often isolated or otherwise identifiable in the data warehouse. Some teams have a separate database only for source data, others have a separate schema or set of schemas for source tables, and some may use a naming convention to identify these tables (e.g. a suffix of "_stg"). 

These source tables reflect the actual source data as closely as possible. This means that they may have the wrong datatypes, need to be cleaned (e.g. trimming whitespace), split out into multiple columns (especially if it is JSON text), the column names may need to be changed, or some other transformation is needed before it can be considered "production ready". But it is important that these raw source tables remain exactly the same as they were when first loaded into the database - you want to avoid `alter table` statements.

Sometimes, these raw sources may come from a relational database. In this case, you may want to implement primary keys on the source tables - because if the primary key constraint is violated, that means something went wrong in the ETL process. However, implementing foreign keys is generally not recommended, as it can severely complicate the ETL process. Instead, document these foreign keys (in tests, in text, etc) and use them to inform downstream transformations.

### Replicable transformations

The next step is to transform these source tables into "production" tables. There may be many transformations before producing the table that will be used for analysis, but there should always be at least one. In a data warehouse, a "transform" usually means a SQL select query that is used to create either a table or a view. For the purpose of this post, "production" refers to tables or views in the database that are ready to be used for any downstream analytical purposes (dashboards, analysis, further downstream views, etc), have been through a development and approval process, and have been designated as being "production" based on its name, schema, database, or some other indication.

The first transform is the simplist - it should select from the source table and apply any basic cleanup that is needed. Let's call the result of this first transformation the "base production" table. It should correspond to the source table closely, and should have a 1:1 relationship to the source table (so, no joins). It should also always be materalized as a table (not as a view). The base production tables - and all downstream transforms - should live in a separate schema/database from the source tables, or otherwise be easily distinguished from the source tables. 

Even if no cleanup or alteration from the base table is needed, this first transformation is still a necessary step. Why? Sometimes there is an error in the ETL process, and the source table may be wiped. If you only have one table (the source table), then you have lost that data, and it will effect any downstream uses on that table. However, if you have a base table (which selects from the source table), and the source table is wiped, then you can stop the transformation before the corresponding base production table is wiped. So, the base production table still has data (even if it is outdated - which is preferable to no data at all). Note: this is only possible if the base production table is materialized as a table, not a view.

Even if a source is static (not being updated by an ETL process), you still want to have this source -> base production table transform, and preserve both this separation and the tranformation applied. Why? You may discover at a later point that the base production table needs to be altered in some way - a column should be renamed, a data type needs to be corrected, whitespace needs to be removed, etc. Or, you may discover that a transform you thought you needed is actually incorrect, and you need to alter the transform. Once you alter the source table, there is no going back (besides dropping the table and re-creating it from the source). Whereas if you have a transformation query, you can simply re-run the query to re-create the altered production table. This is only possible if the raw data in the source table remains the same - and if the SQL used to do the transform is saved (preferably in a git-tracked repo).

#### Further transformations

While base production tables should be materialized as a table and should have a 1:1 relationship with its source table, all further downstream transformations can be materialized as views and query multiple tables. The primary reason that a downstream transformation would be materialized as a table instead of a view is for performance reasons - if the query is computationally expensive and takes a long time to run. Otherwise, views are preferred. 

Note: further downstream transformations should never query a source table - only the production tables/views. These tables/views generally live in the same schemas/databases as the base production tables.

There may be many, many downstream transformations for a particular data source, and the structure of these can vary widely. There are many different design philosophies around this area of the data warehouse, but I will leave that for another post. Suffice to say, a large portion of the "thinking" work in a data warehouse is in writing these downstream transforms.

### Tested production data

When new data is imported and transformed on a regular cadence, it is important to have Data Unit Tests (DUTs) to automatically check that previous assumptions about the data still hold true. DUTs can be performed on any table/view in the data warehouse - source, production, or downstream views. For example, you might want to check that the source table contains some minimum number of rows before doing the transform to production - and if the test fails, then the transform will not happen. You may want to check that a field you assume is your primary key is actually unique and has no null values. You may want to check that a categorical field only has a limited list of values - and if it fails the test, you only want it to warn you, but not prevent the transformation. The most important tests (the ones you want to stop downstream transforms if they fail) should be performed as early in the transformation flow as possible (ideally, the source tables), while the nice-to-have tests that should only warn you about failures (and not prevent transformations) can be implemented further downstream.

DUTs are a way to productionize data testing, but can also be useful during the exploratory phase when first designing transformations. You can test your data through a formal DUT structure, or through a series of queries.
For example, you may want to `select distinct` on a field to see all possible values, or `select count(distinct __)` on a field compared to `select count(__)` to see whether there are duplicates. Based on this exploratory data testing, you may wish to revise your transform. And while it is important to document and preserve any SQL transform queries so they can be re-run, it is less essential to preserve these ad-hoc data tests - their primary purpose for static data is to inform your SQL query for transforming source data into the production table. However, if the data source may be updated, then formalizing them into DUTs is a good idea.

## The implications (or, why dbt)

Imagine you are an analyst, staring at this data warehouse and all of its many tables, trying to figure out which tables are going to have the answer to your question. Or, imagine you are an engineer, informed that something has gone wrong in a dashboard and you need to figure out what (and where) in the data flow something went wrong. What is the one thing that you are really going to want (need!) in order to do your job effectively and efficiently?

Documentation.

You are going to want documentation for your tables, the columns in those tables, the relationships and dependencies between those tables, the tests performed on those tables, and any external dependencies (dashboards relying on those tables, ETL processes powering the source tables). But documentation has a dirty secret - (almost) nobody wants to or has time to write documentation. Unless you make documentation fast and easy to produce (or you pay for it by making documentation someone's job or primary responsiblity), it isn't going to happen (at least not consistently).

dbt may be advertised as a tool to transform (and test!) your data, but its real superpower is in the documentation that is produced as a side effect of how those transformations and test are implemented. If you do not currently have an infrastructure to support transformations and data unit tests within your data warehouse, then implementing dbt is a no brainer because it is the easiest out-of-the-box way to accomplish those fundamental tasks. But even if you do have a (likely custom/house built) infrastructure to do those transforms & tests, making the switch to dbt is worth it, because of the documentation that is produced (and the culture of documentation that is encouraged/supported). Once you see a DAG (directed acyclic graph of table nodes) that visualizes every step from source to dashboard, there is no going back.

Why? Because given enough time, your team will accumulate enough data sources (and the people most knowledgable about those sources will leave at some point), and enough complicated transforms and table structures, that working within the data warehouse will become a snakes' nest of tangled dependencies, table rot, and dangerous assumptions. And if you can't rely on your data warehouse, then your stakeholders can't rely on your analytical outputs. Documentation is not just a nice to have - it is essential. Document your data, your transforms, your tests, your analytical outputs, everything - and then put that documentation in one easily accessible and searchable place. dbt makes this easy, and that is the real reason it has become the darling of the data community - and the reason I've wanted to implement it for our team ever since I learned enough about the tool and our current data infrastructure.

Which bring us back to our principles of good data management for analytics. There was, in fact, one principle missing from the list, so let's round it out.

### Principles of data management (final version)

1. Preserved raw data: raw data should be a direct copy of the source as much as possible, and should not be altered (besides being updated with new data)
2. Replicable transformations: all transformations of the raw data should be replicable/documented (the SQL/python code is saved, preferably in a git-tracked central repository) and automated if needed (transformations performed on a schedule in line with data imports)
3. Tested production data: all data considered "production" (ready for analysis) should be able to pass tests of data quality. These tests should be documented and automated if needed, like the transforms
4. Documented data: the data (each column, each table) should be documented, as well as the data lineage (how the final data was produced from the raw source data)

## Bonus: the development cycle

Now that we've brought dbt into the picture, we can talk about one final piece of the (modern) analytical data warehouse: the development cycle. In the principles above (and the blocks of text further above), note the use of the term "production". The presence of "production" data implies the presence of data that is not "production" - something distinct from the raw source data already described. This missing something is the "development" version of the data - basically, the data/transform that has not yet been finalized. 

Tables that are still in development should be distinguished from production tables in the data warehouse. Dev tables may live in a separate database or schema, or be indicated through a table naming convention. Teams may also have less formal (read: social) ways of indicating that a table is in development, though this introduces opportunity for error. A table in development is not finalized - column names, order, and content may change, the table name itself may change, and the logic has not yet been reviewed and approved by the team. Essentially, it's very risky (and certainly inefficient) to build downstream dependencies on dev tables, though there will always be cases where speedy delivery is a necessity and this rule has to be broken.

One great feature of dbt is that this development phase of tables/views (dbt refers to them all as "models") is built into how dbt works through the use of profiles. It's very easy to designate a specific schema or database as a dev schema/database, and to build models agnostic of the dev/prod schema. It's also why git is a core component of any dbt project - the "main" branch should have models in "production", while feature branches should have models in "development". You have to be familiar with the use of version control in a software development cycle in order to use dbt effectively, and the fact that dbt brings these software engineering practices into the modern analytical workflow is considered a major selling point of dbt.

## In conclusion

Unless you are already part of a data team that uses a data warehouse, it can be hard to understand what an analytical data warehouse is, how to use it properly, and why it is such an important part of working on a data team. If you're in school or otherwise studying for a career in data, knowing how to work within a data warehouse will give you a big leg up over other entry level candidates. My hope is that this blog post can (1) convince you that you already know the most important pieces of the puzzle, (2) fill in some of the missing pieces of the puzzle, and (3) help you synthesize and put all of the pieces together to form a cohesive picture.

In future posts I would like to continue to flesh out how to work in a data warehouse, but this concludes the introduction. If you have any questions or future topics you'd like me to focus on, let me know!
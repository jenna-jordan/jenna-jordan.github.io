---
layout: distill
featured: true
title: The librarian's reference interview for data teams
date: 2025-06-30
description: What data teams can learn from the reference interview librarians perform to identify and serve true information needs
permalink: /blog/reference-interview-for-data-teams
thumbnail: assets/img/header_reference-interview.jpg
categories: data essays
authors:
  - name: Jenna Jordan
    url: "https://jennajordan.me"
    affiliations:
      name: "Data Librarians #datalibs"
      url: "https://bsky.app/profile/jennajordan.me/post/3lak6v5pgmc24"
bibliography: 2025-06-30-reference-interview.bib
toc:
  - name: The data team dilemma (the ad-hoc deluge)
  - name: The DIKW pyramid
  - name: The reference interview
    subsections:
      - name: Roles of the reference librarian
  - name: Data professionals are Information professionals
  - name: The reference interview for data teams
    subsections:
      - name: For the individual contributor
        subsections:
          - name: Assuming the Instructor role… and a path to self-service?
          - name: Gathering requirements with the reference interview
      - name: For the data team leader
        subsections:
          - name: A different definition of “service”
  - name: Wrapping Up
    subsections:
      - name: Special thanks
---
{% include figure.html path="assets/img/header_reference-interview.jpg" class="img-fluid rounded z-depth-1" %}

If you’re an analyst on a data team, the following scenarios are probably very familiar to you:

1. A stakeholder you’ve worked with before comes to you with a new request. They saw what kinds of questions could be answered with a dashboard in the last project, and now they have some new questions to try and find answers for  
2. You get an email from someone in the organization who wants a dashboard for their data. Right now they do a lot of manual work and one-off visualizations in a spreadsheet, and their friend in another department recently showed them a dashboard that the data team made  
3. An executive asks your boss for a set of very specific metrics. Your boss tells you to write some SQL queries to generate numbers for those specific metrics, so they can then email those numbers to the executive

New project requests can come from many sources: an email to a shared inbox, a DM from a former stakeholder, a verbal request from your boss, or even just a jira ticket created by your project manager. No matter how you get the request, once you’ve received it, you will need to choose how to respond.<d-footnote>Not responding at all is still a form of response</d-footnote>

## The data team dilemma (the ad-hoc deluge)

Perhaps your team is already over maximum capacity and you get requests like this every day. You could choose to ignore the request, or mentally bookmark it to respond to later, only to forget about it<d-footnote>hello executive function overload!</d-footnote>. Perhaps you have a project request form, so you redirect all inquiries to filling out a generic form. Maybe you don’t have capacity for this request, but your coworker just wrapped up a project, so you ask them to take it on. If interrupt tasks are common for your team and you are lucky enough to have time allocated to ad-hoc requests, you may try to quickly provide an answer before moving on to the next request or project. If it’s obvious this request is a huge ask, you may reply that you don’t have capacity right now, but they can put a meeting on your calendar for sometime next month. The request may get added to the project backlog, to be re-examined during the next sprint planning phase. 

You’re on a data team, and in today’s world that means<d-footnote>you've trauma-bonded</d-footnote> you are understaffed, always working at maximum capacity with pre-planned projects, and also expected to drop everything to answer some higher-up’s one-off question. Half of your week is filled with meetings, and you know that if you just had some uninterrupted quiet time you’d be able to actually crank out some real work and make real progress on that dashboard that was supposed to be done last week. Fortune forbid that the data isn’t fresh today or the column you were counting on is a free-text field full of inconsistent garbage. Why did your stakeholder organize their spreadsheet like this, don’t they know that will break the import? Why does your boss think you can just `select * from some_perfect_table_that_does_not_exist`? You don’t have enough time to clean up the data going into the dashboard the executives supposedly look at every day (they don’t), you certainly don’t have time to model the data used in 1 project into a star schema!

Let’s all stop and take a deep breath. In… out… in… out. If you are very lucky, and you have always worked on a fully staffed, well-managed data team with a reasonable number of projects and minimal interrupts, perhaps the above situations have never happened to you. But for the rest of us (and, I bet, the vast majority of us), these situations are familiar (and perhaps slightly triggering). And I’m about to give you some advice that you really won’t want to hear: you need to talk to your stakeholders more.

“What? Didn’t you hear that half my day is already filled with meetings and I can’t find the time to do the work I’ve already been assigned? I already talk to my stakeholders every week and they never tell me anything helpful. They’re just not data people<d-footnote>I'm going to need you to do the big airquotes for me here</d-footnote>, they don’t get it. I can make the dashboard they need without them micromanaging every pixel of it. They’re always going off on tangents unrelated to the project, how is talking to them *more* going to help?” 

I hear you. I understand your doubts. I know you don’t have enough time to dive into each project as deeply as you want to. I know how frustrating it can be to talk to “non-data” people who just don’t understand why their seemingly simple ask isn’t reasonable. Trust me - I’ve been there, and I get it. But I want to zoom out for a moment, and look at the bigger picture.

What is the role of a data professional? What is the purpose of a data team? What is the function of data in an organization? What even is data?

Pause. Take just a few minutes to really think about these questions. What are your answers? I really want to hear! Wherever you may have seen this posted, please let me know in the comments. 

No really, come up with your own answers before you read what I think - then come back and hear how a librarian would approach this dilemma.

## The DIKW pyramid

My background is in Library & Information Sciences, and I also have a deep fondness for philosophy, which informs my opinion. You may have a totally different answer informed by your own background and expertise, and that is awesome! If we put together all of our perspectives, we can arrive at a more complete picture.

What is data?

When I think of what data is, I think of it in the context of the DIKW  (data-information-knowledge-wisdom) pyramid, which is a foundational concept in the field of Library & Information Sciences. Rather than try to explain the DIKW pyramid myself, I’m going to pull quotes from [this excellent encyclopedia page](https://www.isko.org/cyclo/dikw)<d-cite key="Frické"></d-cite>, which itself pulls quotes from significant literature on the DIKW pyramid (mostly Ackoff’s “[From Data to Wisdom](https://www.researchgate.net/profile/Rob-Keller/post/Original_paper_of_From_data_to_wisdom_by_Ackoff_1989/attachment/63f67d8997e2867d5081d0de/AS%3A11431281121841684%401677098376991/download/Ackoff89.pdf?_tp=eyJjb250ZXh0Ijp7ImZpcnN0UGFnZSI6InF1ZXN0aW9uIiwicGFnZSI6InF1ZXN0aW9uIn19)”)<d-cite key="Ackoff_1989"></d-cite>.

On data:

> Data are symbols that represent properties of objects, events and their environments. They are products of observation. To observe is to sense. The technology of sensing, instrumentation, is, of course, highly developed (Ackoff 1989, 3)<d-cite key="Ackoff_1989"></d-cite>.

On information:

> Information is relevant, or usable, or significant, or meaningful, or processed, data (Rowley 2007, Section 5.3 "Defining Information")<d-cite key="Rowley_2007"></d-cite>.

On data vs information:

> The vision is that of a human asking a question beginning with, perhaps, “who”, “what”, “where”, “when”, or “how many” (Ackoff 1989, 3)<d-cite key="Ackoff_1989"></d-cite>; and the data is processed into an answer to an enquiry. When this happens, the data becomes “information”. Data itself is of no value until it is transformed into a relevant form. In consequence, the difference between data and information is functional, not structural (Ackoff 1989, 3)<d-cite key="Ackoff_1989"></d-cite>.

> Information systems generate, store, retrieve, and process data. In many cases their processing is statistical or arithmetical. In either case, information is inferred from data. (Ackoff 1989, 3)<d-cite key="Ackoff_1989"></d-cite>

On knowledge:

> Knowledge is know-how, for example, how a system works. It is what makes possible the transformation of information into instructions. It makes control of a system possible. To control a system is to make it work efficiently. (Ackoff 1989, 4)<d-cite key="Ackoff_1989"></d-cite>

On wisdom:

> Wisdom adds value, which requires the mental function we call judgement. […] The value of an act is never independent of the actor [… ethical and aesthetic values] are unique and personal. […] wisdom-generating systems are ones that man will never be able to assign to automata. It may well be that wisdom, which is essential to the effective pursuit of ideals, and the pursuit of ideals itself, are the characteristics that differentiate man from machines. (Ackoff 1989, 9)<d-cite key="Ackoff_1989"></d-cite>

All organizations collect and store data as a by-product of doing business. However, this data cannot be used beyond its functional purpose of making the widget work until it is processed into information. That information can be used to help the people in the organization gain a better and more accurate understanding of how well the organization is functioning. Knowing how an organization is functioning helps the people serving the organization make decisions, which will then affect how the organization functions. Leaders making these decisions should have a vision of the organization’s ideal state, and we consider these leaders wise when they can effectively move the organization closer to that ideal state.

The purpose of a data team is to turn data into information, so that their stakeholders elsewhere in the organization might gain knowledge and make wise decisions. **The role of a data professional is to navigate this process of turning data into information in the most efficient and useful way possible.** An excellent data professional will partner with stakeholders to see through the process of generating knowledge from the processed information, and the most effective data leaders are those empowered to make decisions alongside other leaders.

In order to provide information that will increase the knowledge of your stakeholder and help them make wise decisions, you must talk to them in order to find out what the decisions they need to make are, what their current understanding of the knowledge landscape is, and what information they need in order to enhance their understanding. This conversation requires time, empathy, and trust. Most likely, your stakeholder has already thought about this… and then gone the extra step of trying to translate this into a request for a data team. 

Their idea of a data professional is probably just that - someone who only operates at the level of data. But it is your job to demonstrate that while you have the technical know-how to work at the data level, you also have the business acumen to understand and converse at all levels of the DIKW pyramid. **You can do your best work at the foundation when you have the entire context.** The translation from a business-oriented request into a data-oriented request should be on the data professional, not the stakeholder.

This is where I’m going to introduce another concept from the field of Library & Information Sciences… and the primary topic of this blog post: the reference interview.

The reference interview is designed to solve a problem common to most information professions - one that you have undoubtedly encountered before and may have already developed techniques to address. My hope is that by learning how librarians approach a reference interview you can add another set of techniques to your toolbox, and perhaps even adopt a new perspective that will help you approach one of the most frustrating aspects of your job. 

## The reference interview

Before adapting the reference interview for data teams, let me first explain it in its original context: that of a librarian responding to patron inquiries. Have you ever walked into a library with a research question, but weren’t quite sure where to start? Soon after walking in, you probably saw a circular desk with signs above it proclaiming “Reference Desk”. Behind that desk are one or two librarians, next to computers with the catalog ready for searching, ready to help you with your research quest. You walk up to the desk, ask your first question - and what happens next is the reference interview. 

My primary source for this section will be the Reference and User Services Association (RUSA) Guidelines for Behavioral Performance of Reference and Information Service Providers<d-cite key="ALA_2008"></d-cite> - as [these guidelines](https://www.ala.org/rusa/resources/guidelines/guidelinesbehavioral) are industry-standard and referenced by most institutional guides to the reference interview. I’ll also be drawing from the [book](https://alastore.ala.org/content/conducting-reference-interview-third-edition) “Conducting the Reference Interview: A How-To-Do-It Manual for Librarians”<d-cite key="Ross_Nilsen_Radford_2019"></d-cite>, which goes into much more depth than the short RUSA Guidelines.

The importance of the reference interview is founded on a simple assumption: that patrons rarely start out asking the librarian for the information they actually need. The goal of the reference interview is to identify what the patron really wants to know, so that the librarian can then more efficiently search the system for resources that will fulfill the patron’s true information need. Librarians should take the time to establish rapport with the patron, engage in active listening, and confirm that the information provided is what they actually needed - in the end, this will save the time of both patron and librarian (compared to jumping straight to the search and repeating through trial and error until an adequate resource is found).

While on the surface the reference interview is a structured format for going from initial question to identifying resources that can fulfill the true information need, the real magic is in the empathetic communication style and active listening that underlies these techniques. Excellent interpersonal skills and emotional intelligence are key for the librarian to build trust with the patron, cultivate an inclusive and collaborative learning environment, and work towards a mutual understanding of what the patron really wants to know.

Reference interviews generally follow these 6 steps:

1. Establish contact with the patron and listen to the initial request, without interruption or judgement
2. Paraphrase the initial request, to demonstrate you were listening and verify you correctly understood the question  
3. Ask open-ended questions first that encourage the patron to elaborate on their initial request (focusing on the big picture), followed by clarifying close-ended questions to understand the specifics of certain parts of the request  
4. Verify the patron’s request by restating the question and asking for confirmation, incorporating what you have learned during the question phase. If the patron verifies this rephrased request is accurate, start the search. If not, repeat the question phase until the patron verifies the restated question is accurate.  
5. Conduct a search of the system collaboratively, sharing your screen/resource and explaining each step of the process. Check in with the patron to see if they want to do the search themselves at any point in the process, and if so, continue to offer assistance as needed. This is the phase where you can offer instructions or advice, guiding the patron with your special expertise and knowledge.  
6. Follow up with the patron to verify that the patron’s information need was met. You may need to review the resources found and identify different/additional resources if needed, repeating the search phase. It may also be necessary to explain when a request is beyond the scope/capacity of the library, in which case the patron should be referred to an external resource/institution. This final phase is also the appropriate time to ask for feedback on the process.

A reference interview is most successful when the librarian and patron share a common purpose: finding materials that will fulfill the patron’s information need. It is the librarian’s responsibility to find out what the patron wants and guide the interview in order to achieve this goal. The modern reference interview comes from the perspective that libraries are primarily service-oriented, and should provide information in the manner that is most useful to its patrons.

Of course, there are plenty of opposing viewpoints in the LIS literature - that the reference interview is not always necessary, that it is only useful for certain types of inquiries, that libraries shouldn’t be service-oriented, that the reference interview can only be performed in person… and the dominant viewpoint in the literature has changed over time. If you’re curious, feel free to explore the literature, but I’m not going to dive any deeper in this post beyond noting the fact that the importance and role of the reference interview has been contested and evolved since it first became a thing over a century ago. 

It should also be noted that even when librarians are trained to always conduct a reference interview, studies have shown that a majority of the time they do not conduct a full reference interview, or default to the “question-oriented model” (answering the patron’s original question) rather than the “needs-oriented model” (addressing the patron’s information need - the initiating problem). Being empathetic, curious, and patient all of the time for every patron query is hard work, and nobody is perfect - but the reference interview provides an ideal guideline for these engagements.

### Roles of the reference librarian

Before we move on to how this translates to the work data teams do, I want to spend some time on the different roles that a librarian takes on during the reference interview. My primary source for this section is a [chapter](http://www.amyvanscoy.net/uploads/5/7/7/9/5779319/vanscoy_inventing_the_future.pdf) in the book “Leading the Reference Renaissance: Today's Ideas for Tomorrow's Cutting Edge Services”, called “Inventing the future by examining traditional and emerging roles for reference librarians”<d-cite key="VanScoy"></d-cite>.

The most dominant role of the reference librarian is that of the “information provider”: the highest priority for a reference librarian is to provide answers to questions - the more complete the better, whether that be through directly telling the enquirer the answer to their question or helping them find the information resources they need (e.g. books, journal articles, news articles, magazines, etc). After all, the ultimate goal of the reference interview is to fulfill the patron’s information need. But while “information provider” is the most obvious role, it is far from the only (or even, arguably, the most important) role that a reference librarian fulfills.

The other major role for a reference librarian is that of the “instructor”. No reference librarian wants to be the sole provider of answers - think of all the questions that would never get answered simply due to time and resource constraints! Instead, reference librarians can instruct users in library and research skills, so that they can be self-sufficient and navigate the library to find the answers and resources they need on their own. While reference librarians can lead classroom-style teaching sessions, instruction can also occur during the reference interview. 

Read the first sentence of step 5 again: “Conduct a search of the system collaboratively, sharing your screen/resource and explaining each step of the process.” By the end of the reference interview, the patron should feel more comfortable conducting a similar search on their own next time. While this may mean the current reference interview may take slightly longer, it will save time in the long run.

There are some further minor roles that are implied by, or overlay, these two major roles, such as: 

- Communicator: librarian as the human connection between a user and the resources  
- Relationship builder: librarian building a long-term relationship with the user  
- Guide/advisor: librarian guiding the user in selecting good and appropriate resources  
- Counselor: librarian mentoring users in the research process, and treating the user as a holistic person  
- Partner: librarian and user act as a team, each bringing their own knowledge and skillsets

The final role I want to focus on is that of the librarian as an expert: this is the foundation for all of the previously outlined roles. A librarian is an expert at navigating (and cultivating!) the system that organizes the library’s resources. That expertise allows the librarian to quickly find needed information, and some portion of that expertise is what the librarian is attempting to transfer with instruction (though much of the expertise is likely to remain as [tacit knowledge](https://commoncog.com/tacit-knowledge-is-a-real-thing/)<d-footnote>"What is Tacit Knowledge? Tacit knowledge is knowledge that cannot be captured through words alone." Sidenote: I'm very happy to be linking out to some Cedric Chin content here, his essays are gold!</d-footnote>). This expertise is what the librarian brings to any research partnership, and what allows the librarian to be a guide for users. 

## Data professionals are Information professionals

The parallels between data professionals (especially analytics engineers) and librarians have been drawn [before](https://www.getdbt.com/analytics-engineering/transformation/data-catalog) ([many](https://www.getdbt.com/data-careers/adam-stone#describing-analytics-engineering-to-a-friend) [times](https://youtu.be/T0Z_ibd3Hx0?t=46)), albeit usually by those on the data side of the divide. If you’ve read this far, I’m hoping that by now it is obvious that this is because both data professionals and librarians are really information professionals. And while data (engineer/analyst/scientist/etc) is a relatively new profession, librarianship is not, and there is a lot for the data professional to gain by considering themselves part of the wider information profession - and the larger body of knowledge and practice that comes with it.

One such practice? The reference interview.

Before I give my take on how data teams can learn from and adapt the reference interview, I once again want to ask you, dear reader, to pause and consider for yourself: based on everything you’ve learned so far, how can you borrow from the typical reference interview the next time a stakeholder comes to you with a new request for the data team?<d-footnote>And if you shift how the data team engages with the rest of the organization, how can this change the role of the data team?</d-footnote> Revisit the scenarios from the very start of this blog post: how would you have approached these scenarios before, and how would you approach them now from the perspective of a data-savvy reference librarian who starts every stakeholder engagement with a reference interview?

Remember, the difference between data and information is functional - it is only by processing data into information that we give it meaning, purpose, and value. Which level do you want to be operating at? Which level does the rest of your organization think you are operating at? What do you need to do to get to the next level?<d-footnote>(A question for a future post… how can data professionals further elevate their work to be *knowledge* professionals?)</d-footnote>

## The reference interview for data teams

So how can data teams learn from library science, adapt the reference interview, and elevate their practice from being data practitioners to information practitioners? I want to approach this from two perspectives: that of an individual contributor on a data team who has the power to adjust how they interact with stakeholders, and that of a data team leader who has the power to make structural and process changes that affect the environment that the individual contributors on a data team work in. 

### For the individual contributor

Let’s start with the individual contributor perspective. Remember the pithy and unwanted advice I gave near the start of this post? You need to talk to your stakeholders more. Beyond that, the attitude and emotional presence you bring to those interactions matters. Your stakeholder has an information need. They know you are busy and have a dozen other projects that need your attention, and they likely have already formed some opinion about what you know and are capable of doing. 

So in an effort to be helpful and efficient, they have likely already taken that information need and refined it, restricted it, reshaped it in a query or request that they think you can do/answer in order to fulfill their information need. So here is my first and most important request to you: don’t accept that query at face value. It is *your* job, *not theirs*, to dig deeper and discover their true information need *before* you try to fulfill it.

Here is an abbreviated and reframed version of the 6 steps to the reference interview, which you can use and adapt in order to uncover their true information need. Think of this as a formula for a structured or guided conversation:

1. Listen to the initial request without interruption or judgement  
2. Paraphrase the request back to them  
3. Ask open ended questions first, followed by clarifying close-ended questions  
4. Restate the request yet again, now altered by their responses to your questions. Repeat until the rephrased request is confirmed as accurate  
5. Collaborate to find an answer to the rephrased information request, using the interviewer’s expertise in navigating the information system and the interviewee’s guidance and background knowledge. Depending on the need/relationship, either can be the “driver”.  
6. Verify that the true information need was met. If not, the process can be repeated, or the requestor may need to be directed to further resources if their information need is beyond the capacity of this process. Finally, you can ask for feedback on the process.

Conversations like this (in which you are trying to unearth their true information need)  will generally be more successful when you approach them with empathy, non-judgement, and genuine curiosity. Take the time to establish a rapport first. Apply the techniques of active listening. Intentionally cultivate an inclusive and collaborative space. This means that your language *matters*. Erase words like “simply”, “just”, and “easy” from your vocabulary<d-footnote>Any other words to add to the list?</d-footnote>. When you ask questions, show that you are paying close attention to their response by rephrasing and restating what you heard. Ask yourself first what assumptions you are making, and at the very least verify/clarify those assumptions or don’t bake them in to your first round of (open-ended!) questions. 

Remember: the interpersonal skills and empathetic mindset that a librarian brings to the reference interview is just as important (if not more!)  to the ultimate success of uncovering the user’s true information need as the structured interview process that they follow. I want to acknowledge that this is hard, and it is a skill to develop just as vital as any technical skill, so give yourself grace and time to reflect as you start to adjust your approach. And if you feel like this is already how you engage with stakeholders, that’s fantastic! Make sure you are collecting feedback - from your stakeholders, your peers, and your managers/mentors - so you can continue to improve your approach (everyone has blindspots!).

If this sounds preachy, I apologize, but I genuinely think this is both the hardest and most impactful skill you can develop. It is a skill I know I will need to continue to practice and improve on throughout my entire career, and it is a skill that is almost never taught in professional contexts (unless, perhaps, you were a therapist in a previous life). If you are struggling to make the jump to senior, demonstrating this skill will be one of the most important things you can do to show your manager and your team that you are someone who can handle the more nebulous projects - the kinds of projects typically given to seniors.

Ok, so what do we have so far? 

- Talk to your stakeholders more (especially at the start).   
- Never assume that their initial request matches their true information need.   
- Make it your goal to uncover their true information need.   
- Cultivate an empathetic, non-judgemental, and curious mindset.   
- Practice active listening techniques. 

What else can we adapt from the reference interview?

#### Assuming the Instructor role… and a path to self-service?

I want to pull your attention to step 5 of the librarian’s reference interview:

> Conduct a search of the system collaboratively, sharing your screen/resource and explaining each step of the process. Check in with the patron to see if they want to do the search themselves at any point in the process, and if so, continue to offer assistance as needed. This is the phase where you can offer instructions or advice, guiding the patron with your special expertise and knowledge.

I also want to remind you of one of the major roles the reference librarian plays: the instructor. Most likely you already assume the other major role of the “information provider” when you receive an ad-hoc request, but how often do you assume the “instructor” role? What would that look like for a data analyst?

Let’s revisit the first scenario:

> A stakeholder you’ve worked with before comes to you with a new request. They saw what kinds of questions could be answered with a dashboard in the last project, and now they have some new questions to try and find answers for

After some investigation (read: asking a series of open-ended and then clarifying close-ended questions, rephrasing their ask, and then repeating until you understand their underlying information need), you realize that this stakeholder is trying to do some exploratory data analysis (EDA) for a new project, and they want to gut check whether the trends that they think are happening are actually happening. They don’t actually need a dashboard (or at least, not yet), but that’s how they’ve been doing EDA for the other project, and they figured another dashboard for this new dataset would let them see whether these numbers were actually going up over time.

Do you want this stakeholder coming to the data team every time they want to do some EDA? Go that route, and you will soon have a graveyard of unviewed dashboards, not to mention the opportunity cost of devoting valuable analyst time that could’ve been spent on higher value projects. Why is the stakeholder asking for a dashboard when the underlying information need could be fulfilled more efficiently with some SQL queries? Likely, because dashboards and interactive visualizations are familiar. For the sake of this example, let’s say that this stakeholder knows some basic SQL. How could the data analyst approach step 5 of an adapted reference interview?

The first step is to invite the stakeholder to be a partner in this EDA. Assuming that this stakeholder is not an executive, if they are asking for the data team to invest time in answering their question, they should be willing to put that time in themselves, as well. Who knows - they may even be excited at this opportunity to learn some analyst skills from an expert! Set up some pairing sessions, and use those sessions to time-box the project - you’ll only work on it during those pairing sessions. During those sessions, you will be sharing your screen and narrating your process. 

Don’t try to prepare a cleaned up version of the process - let the stakeholder see and participate in every messy step (yes, that includes googling for how that window function works again, and running queries with typos). The ultimate goal here is for the stakeholder to feel comfortable going through this process by themselves, and that includes knowing what to do when something goes wrong<d-footnote>My opinions here have been heavily shaped by The Carpentries pedagogical model - see: https://carpentries.github.io/instructor-training</d-footnote>. You want the stakeholder to lose the perception that the skilled technical data analyst is able to magically produce a dashboard with a few precise keystrokes!

Start from the very beginning - the first thing you’ll have to do is identify the right datasets to query. You are an expert at navigating the data warehouse - you know how it is organized, the naming conventions, and how to identify high quality ready-to-use datasets. You know how to search the data catalog (or whatever other documentation there may be), and you are all set up to query the database. **Your stakeholder is also an expert**<d-footnote>Let's say it louder for the folks in the back!</d-footnote> - they may or may not know what the data looks like, but they do have a lot of knowledge in this domain. You need to use your expertise to guide the stakeholder in the research process, and you can lean on your stakeholder to know what information they expect and want to find. You might find that by working together, you can fulfill your stakeholder’s information need better and faster than going off on your own… a 1 + 1 > 2 effect.

The next time this stakeholder has a question, hopefully they are more comfortable performing some of this process themselves - and maybe in some future request, they will ask to drive in the pairing sessions, with you providing support when needed. By inviting the stakeholder into your workflow and process, you are enabling and empowering them to use the data resources available to them more independently, freeing up your time to focus on more complex analysis.

This is one of the foundational building blocks of true self-service - not only making the data and tools available, with the data documented and findable in a curated data catalog, but also providing the training, support, and guidance for users so that they are empowered to navigate the system by themselves or in partnership with a data expert if they so choose. Sorry, but no magic BI tool is going to be able to provide self-service if those core fundamentals aren’t in place.

#### Gathering requirements with the reference interview

Generally, the first step in a new project is to gather requirements. This phase is often responsible for most of the frustration and angst you experience while working on a project. How many times have you thought you reached the end of a project, only to be told that the report or dashboard you delivered does not actually meet the stakeholder’s expectations? This needs to be tweaked, that needs to be reworked… but sometimes that little tweak is a change to a fundamental assumption that requires overhauling the entire product! 

How does your team gather requirements? When does the requirements gathering start? (Likely during the initial intake phase!) Who typically performs the initial requirements analysis? Does this person have the necessary context and technical skills to gather all requirements? Is there a handoff? What problems typically occur during this handoff? When does the individual contributor who will be doing most of the work for the project get involved? How much of the requirements gathering process do they typically need to re-do? Crazy idea: draw a process map and start identifying waste in your requirements gathering process. How can you improve the experience of gathering requirements for both the data team and the stakeholders?

As you may have guessed, I believe the reference interview has something to offer here. First, the individual contributor(s) who will be directly working on the project should be brought into the requirements gathering phase as early as possible. While a project manager or data product manager can direct and guide the process, they should not try to collect all of the requirements in a vacuum and then hand off those requirements to an analyst/engineer. Second, the analysts/engineers/managers involved in the requirements gathering should be conscientious about the emotional energy they are bringing to these stakeholder conversations: adopting an empathetic, non-judgemental, and curious mindset. Third, they should try to follow the key principles of the reference interview in these conversations: that the stakeholder is not likely to start with their true information need, to utilize active listening techniques, and to approach the process as a collaborative exercise in which all parties have special expertise to offer. The data team should iteratively develop a set of requirements and seek consensus on those requirements and the true information need.

If you were to make one change to your typical requirements gathering process to align it closer to a reference interview, what would it be?

### For the data team leader

If you’re a data team leader, I hope that you haven’t just skipped ahead to this section - because your whole job is to cultivate an environment that encourages and supports all of the suggestions I made in the previous section for the individual contributor. So let’s review some strategies that will allow your team to start acting more like information professionals, and implement their own version of a reference interview.

Let’s start with the most significant environmental change you can make: creating the data team’s equivalent of a reference desk. When you walk into a library with a question, do you ask the first person you see with a name tag? I mean, maybe - but any trained library page should know to then direct you to the reference desk. But most likely you look for the big desk with signs above it and a reference librarian ready and waiting behind said desk. This librarian isn’t (usually) doing other activities like cataloging or purchasing new books - if they are at the reference desk, their sole job is to help any patron who walks up to the reference desk. How can we replicate this experience for stakeholders reaching out to a (e.g. remote) data team?

First, someone needs to be “at the reference desk”<d-footnote>I need to caveat here that this really only applies to medium-to-large data teams, as smaller data teams are unlikely to have capacity for this.</d-footnote> -  a dedicated analyst/engineer/etc whose only job during that shift is to respond to stakeholder requests. We can borrow from “on-call” best practices for software engineers here as well - while a reference librarian is typically responding to new information requests and an on-call software engineer is typically responding to active issues/outages, the assigned data team member is likely to encounter both of these situations. Regardless, the data team member who is on-call/at-the-desk should not be expected to complete any typical project work during their shift, and it is your job to organize sprints and/or project planning around this. 

On the flip side, team members who are not currently on-call/at-the-desk should not be expected to respond to ad-hoc requests. The goal here is to minimize overall context switching, account and plan for all types of work (after all, we all know ad-hoc requests are inevitable), and better serve the data needs of the whole organization without sacrificing the needs of the data team itself. What virtual “signs” can you put up to direct stakeholders to the data team’s “reference desk”, to hopefully minimize the number of redirects that are needed? What culture changes are needed to shift and enforce this new social norm?

Next, you’ll need to consider training: how can you enable data team members to be successful when it’s their turn to serve at the reference desk? Unless you have a librarian on your team (which, honestly, you should consider!), this is going to be a learning experience for everyone. Consider pairing two team members to be at the reference desk together, so they can observe and learn from each other. Collect and encourage feedback, from each other as well as stakeholders.

Here’s a crazy idea: try going to a library with a research topic in mind, and ask a reference librarian for help. Experience the reference interview for yourself as a patron! Your experience may vary depending on the library that you go to, so try visiting a few different libraries (especially if you’re lucky enough to be close to a research university!) - try to pay attention to the overall experience from entering the library with a question to (hopefully) leaving with some resources and/or answers.

If you’re willing to try this data team reference desk idea out, I fully encourage setting it up as an experiment. What are you trying to improve? What metrics can you track? How can you test whether this change is actually improving processes for the data team and your stakeholders? What surveys should you send out before, during, and after the experiment?

#### A different definition of “service”

For many data teams - and data “thought leaders” on LinkedIn - “service” is a dirty word. You don’t want your data team to be like the typical IT service desk, where data team members are just ticket takers who fulfill stakeholder requests. No, you want your data team to be working on strategic high-value projects that will drive measurable impacts on the business. After all, how can you focus your limited resources on driving the highest impact if your team is churning out dashboards and emailed reports by the dozen?

Let’s reframe the word “service” from an IT context to a librarian context. Going back to “Conducting the Reference Interview”, Chapter 1, the authors state unequivocally that “this book is founded upon the principle that libraries must take a service orientation.”<d-cite key="Ross_Nilsen_Radford_2019"></d-cite>

> We are convinced that the institutions that will survive in the twenty-first century are those that serve their clients and give them the help they need. If libraries don't provide helpful information services, users will turn to other service-providers who are more service-oriented… librarians provide a professional "value added" knowledge component that is lacking in many commercial services. The RUSA (Reference and User Services Association, 2000) "Guidelines for Information Services" state: "Provision of information in the manner most useful to its clients is the ultimate test of all a library does."<d-cite key="Ross_Nilsen_Radford_2019"></d-cite>

Some useful context for this quote: there was a significant contingent of LIS researchers convinced that search engines would render the profession obsolete. While the role of librarians and the value they provide may have shifted, librarians are still around and more vital than ever. 20 years later, a similar debate is ongoing… this time focused on generative AI. The conclusion to this debate seems even more obvious than the one over search engines.<d-footnote>The librarian skillset is only going to become more and more important in this "age of AI"</d-footnote>

A side note in the book elaborates on this idea with a further citation from the literature:

> Herbert White (1992) says that librarians need to emphasize their strengths. As computers increasingly take over clerical tasks that computers are good at, librarians should focus attention on aspects of service involving human communication that computers can't do well. Let computers get involved in document identification, document delivery, overdue notices, interlibrary loans and cataloging, White argues, and let librarians take a proactive role in information intermediation.<d-cite key="Ross_Nilsen_Radford_2019"></d-cite>

Reframed: a service-oriented data team is focused on providing information in the manner most useful to its stakeholders, and is a proactive human intermediary between the organization and its data resources. (I’ll posit that this approach is not opposite of a product-orientation, but rather complementary.)

As a data team, you acquire, organize, curate, and retrieve data resources. The team’s collective expertise is vital to interpreting and analyzing these data resources. However, the data team is rarely (if ever) the one making the decisions (or the ones accountable for the results of said decisions). Data teams can be as strategic as possible, working directly with the C-suite on the most important objectives for the organization, but by virtue of their raison d'être, data teams will serve a supporting/helping role. 

For some, this can grate - you may want to be the “hero” data scientist, crafting machine learning algorithms that make the decisions for the business, rescuing the organization from heuristics-driven (poor) decisions and instead achieving the lofty goal of data-driven (smart) decisions. Rock, meet hard place - given human nature and organizational realities, your hero aspirations are likely a pipe dream, and the sooner you realize that humans will always be in the loop, the faster you can start making a real impact.

How does your data team currently operate? How do you want your data team to operate in the future? What does your organization currently need out of the data team? What are your organization’s goals for how to use data in the future? How does the data team need to operate in order to help the organization achieve their data goals? 

As a data team leader, it’s your responsibility to consider these questions and create a strategic plan to ensure not only that the data team is adding net value, but that the rest of the organization recognizes that value. Do you think that the librarian’s frame for being “service-oriented” should be a part of that strategy? If analysts start new projects or respond to ad-hoc requests with some version of a “reference interview” (vs immediately building out a dashboard based on the description field in a Jira ticket), how do you think that will shift both the actual and perceived value of the data team?

## Wrapping Up

At the start of this post, I gave a few examples of scenarios data teams may encounter:

1. A stakeholder you’ve worked with before comes to you with a new request. They saw what kinds of questions could be answered with a dashboard in the last project, and now they have some new questions to try and find answers to  
2. You get an email from someone in the organization who wants a dashboard for their data. Right now they do a lot of manual work and one-off visualizations in a spreadsheet, and their friend in another department recently showed them a dashboard that the data team made  
3. An executive asks your boss for a set of very specific metrics. Your boss tells you to write some SQL queries to generate numbers for those specific metrics, so they can then email those numbers to the executive

If you made it all the way to the end of this extremely long blog post, then I hope you can start to brainstorm how you might approach these scenarios as a librarian would. The point of this post is not to say that all data teams should adopt the reference interview for all ad-hoc requests and requirements gathering activities for longer-term planned projects. Rather, I hope that you have a new perspective on how your data team’s processes and procedures might be shifted - that you have a new hat you can wear, a new lens through which to see the world, another tool in your toolbox… whatever metaphor floats your boat. 

There are 2 key things you should remember about the purpose of the reference interview:

1. A stakeholder’s first stated information need is rarely their *true* information need  
2. The best way to uncover their true information need is by approaching the conversation with empathy, nonjudgement, and genuine curiosity, as a partner who acknowledges everyone’s respective expertise, and by utilizing the techniques of active listening

The idea that stakeholders rarely ask you for what they actually want is hardly a new one or unique to the reference interview. Just ask your product managers, or anyone with a few years of experience interfacing between the people who *want* things and the people who have to *deliver* those things. Hopefully this is not a revelation for you either - though if it is, it’s a valuable [lesson to learn](https://youtu.be/g0_P55Y4H_c?si=ef4zQGJl48trsU5x)<d-footnote>Shachar Meir has given talks and put out content that is very aligned with the ideas in this post, just from his own experience/perspective - I would highly encourage anyone to follow his work!</d-footnote>. 

**Far more important than realizing that stakeholders rarely state outright what information they actually need, is the perspective switch that it is *your* role to uncover their true information need.** You will always be handicapped if you blame your stakeholders for not accurately translating their information/business request into the data team’s language.

The reference interview provides a structured way to accomplish this vital discovery process, and it really doesn’t take too much translation to go from a librarian-performed reference interview to a data analyst-performed reference interview.

To review (in short), this structure is:

1. Listen to the initial request without interruption or judgement  
2. Paraphrase the request back to them  
3. Ask open ended questions first, followed by clarifying close-ended questions  
4. Restate the request yet again, now altered by their responses to your questions. Repeat until the rephrased request is confirmed as accurate  
5. Collaborate to find an answer to the rephrased information request, using the interviewer’s expertise in navigating the information system and the interviewee’s guidance and background knowledge. Depending on the need/relationship, either can be the “driver”.  
6. Verify that the true information need was met. If not, the process can be repeated, or the requestor may need to be directed to further resources if their information need is beyond the capacity of this process. Finally, you can ask for feedback on the process.

If you have the time, take a moment to think about each of these 3 scenarios. How would your team approach them today? How would a reference librarian approach them? Role play is an extremely effective way to learn and practice new skills - grab a partner and try conducting a reference interview for each of these scenarios!

This post had a lot of questions for you, the reader - many of which were left unanswered, because every reader will have a different answer. I hope that you put some time into considering these questions, and the next time you get one of those annoying ad-hoc requests your memory might be jogged, and something will prompt you to put on your reference librarian hat. (There are certainly worse hats to wear!) I hope you will experiment with the reference interview method - adapt it and make it your own. And I hope that you consider the time that you spent reading this post well spent - thank you for reaching the end!

If after reading this post you are intrigued enough to try any of these strategies for yourself or your team, I would love to hear about it! Please reach out via email, on socials, or by leaving a comment on this post. I would love to hear your story.

### Special thanks

Most students in an MSLIS program take a class called “Reference & Information Services”. It’s a core part of the curriculum, if not required. Many MSLIS graduates go on to work in a library and gain experience in conducting the reference interview. Unfortunately, neither applies to me - I veered hard into the “information management” side of my program, and then kept on veering straight into the data field. However, I do have the great fortune of having a group of friends from my cohort who did take Reference, and who did go on to be librarians who conduct reference interviews. When the idea for this blog post was first taking shape, they were the first people I went to for help and resources. They sent me their class syllabus and readings, and patiently answered all of my questions about the reference interview based on their knowledge and experiences. Thank you for the references and the conversations - I wouldn’t have been able to write this without you. To Yvonne Freebourn, Taylor VanTryon, Adam McConville, and Christine Willson, UIUC iSchool Class of 2020.

Also<d-footnote>Thank you to the family, friends, and colleagues who read a draft of this (absurdly long) post in advance and offered feedback/edits/thoughts. I appreciate y'all <3</d-footnote>, special shoutout to Amalia Child for [citing this post](https://locallyoptimistic.com/post/the-five-laws-of-data-enablement-how-the-father-of-library-science-would-make-his-data-team-indispensable/#a70ebd47-9401-411b-878d-923fe05d6606)<d-footnote>at long last, your footnote can have a link :D</d-footnote> long before it even existed, and fighting the good fight with me to spread the wisdom of Library & Information Science to the data world.

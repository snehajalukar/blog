---
layout: post
title: Observability Engineering - Part 1 (Chapters 1 - 4) Summary
categories:
- General
feature_image: "https://picsum.photos/2560/600?image=872"
---

Hi! My name is Sneha, and this is the first post in a series of blog posts I'm writing where I summarize key takeaways from Observability Engineering, by Charity Majors, Liz Fong-Jones and George Miranda. There are 5 parts to this book, and so I'm planning on writing 5 individual posts in total - and will keep adding to each part as I progress reading.

Now that the logistics are covered: let's get into it!

![here we go](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExeTk4YTAxZHMyYzdjOWxvemg3djA0NXh6dWFnNGlzaHVlaGY4anVscCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/dSSbVlZgIXBtv2gK5k/giphy.gif)

<b> Chapter 1: What is Observability </b>

Summary/Key Takeaways

- Starts with the mathematical definition of observability - coined by an engineer (Rudolf E Kálmán in 1960) as: a measure of how well internal states of a system can be inferred from knowledge of external outputs.
- Covers items that form a litmus test for an observable system, including a few that really spoke out to me:
    - "Can you understand what any particular user of your software may be experiencing at any given time"
    - "Can you identify which system user is generating the most load (and slowing performance the most), as well as the 2nd, 3rd or 100th most load generating users?"
    - Paraphrasing here but: can we get ahead of data needs and get insight on issues even when it's the first time we're exposed to something? 
    - Are we continuously aggregating data to be able to extrapolate on trends?
- Definition of observability is "how well you can understand and explain any state your system can get into, no matter how novel or bizzare"
- Thought an interesting note was not only how can we gather useful data/what are technical requirements for processing that data but: what team capabilities are necessary to benefit from that data? Having the data is one thing, but how do we consume it in a useful way.
- Mischaracterizations: observability is not just telemetry
    - 3 pillars of telemetry: metrics, logs, traces
    - The goal is to evolve the way we think about gathering the data needed to debug effectively.
    - The book makes a stark distinction between monitoring systems and observability. Open question in my eyes that this raises: how do we move past monitoring?
- Monitoring alone doesn't help us fully see our systems. Setting performance thresholds is an arbitrary process.
- The book mentions limits to low-level commands like strace, tcpdump, print statements, ect. (Personally, I disagree - I find so much use out of low level commands to dig into root causes and look at individual systems - the book seems to fault them a bit)
- Monitoring and metric-based tools are built with assumptions: including your app/system is a monolith, and everything runs on containers, VMs, or bare metal which we control. Things are rarely isolated in systems and infra is dynamic and interacts with many services.
- Debugging with observability starts with understanding deep context: understanding how a system works end to end, reconstructing the environment and circumstances. 
- "Monitoring is for the known-unknowns, but observability is for the unknown-unknowns"
- Cardinality: the uniqueness of data values contained in a set. 
    - Low cardinality means that there are lots of duplicate values
    - High cardinality means we have a large amount of unique values
    - For observability, high-cardinality information is almost always most useful
- Dimensionality: number of keys within that data
    - In observable systems, telemetry is "wide" - lots of key-value pairs. 

<b> Chapter 2: How Debugging Practices Differ Between Observability and Monitoring </b>

Summary/Key Takeaways

- Elaboration on how monitoring is all about checking a system against conditions (reactive)
- Meanwhile, observability is about exploratory investigations and determining where and why performance issues may be occuring (proactive)
- Often times we get familiar with systems and learn how to debug, given metrics/alerts, by intuition. However, with a different application, different architecture this doesn't apply.
- Institutional knowledge is unwritten information that may be known to some but is not commonly known by others. With monitoring-based approaches, teams often orient themselves around those with the most senority/knowledge as they have the most insight on patterns.
- With teams that practice observability, the best debugger on a team is typically the most curious - exploratory questions lead towards more discovery.

<b><u>Page Updated (March 20th, 2025)<b><u>

<b> Chapter 3: Lessons from Scaling Without Observability </b>

Summary/Key Takeaways
- Author worked for Parse (aquired by Facebook) - which had its observability issues but they prioritized dev speed, which was the right thing to do. However In August 2012 they faced a massive scaling problem (Parse went down when an app hosted with them livestreamed).
- It was hard to isolate the problem as when something got slow, everything got slow.
- The first attempt at solving this was overprovisioning instances (expanding capacity so things run at 20% utilization normally so spikes are able to be handled).
- Things have evolved from just "the app" and "the database" to modern systems (including microservices) used by different tenants that require scaling and different levels of usage. A single database has turned into a range of storage systems. This has led to complexity in operating/administering systems but also difficulty in understanding systems.
- Interesting note: "User experience can no longer be generalized as being the same for all service users. In the new model, different users of a service may be routed through the system in different ways, using different components, providing experiences that can vary widely."
- "Engineering teams must reprioritize the value of production and change their prac‐ tices accordingly. By not shifting production systems to their primary focus, these teams will be relegated to toiling away on production systems with subpar tooling, visibility, and observability. They will continue to treat production as a fragile envi‐ ronment where they hesitate to tread—instinctively and comfortably rolling back deployments at the slightest sight of potential issues—because they lack the controls to make small tweaks, tune settings, gently degrade services, or progressively deploy changes in response to problems they intimately understand."
- Once they made the shift to an approach to slice and dice and follow a trail of breadcrumbs to a solution (high cardinality tool called Scuba) - triaging issues became easier.

<b> Chapter 4: How Observability Relates to DevOps, SRE, and Cloud Native </b>

- "Observability and testability require continuous investment rather than being a onetime addition, or having a one-size-fits-all solution."
- The Cloud Native Computing Foundation (CNCF) defines cloud native as “building
and running scalable applications in modern, dynamic environments...[Cloud native] techniques enable loosely coupled systems that are resilient, manageable, and observable. Combined with robust automation, they allow engineers to make high-impact changes frequently and predictably with minimal toil.”
- The definition above doesn't just focus on scalability, but on development velocity and operability as goals.
- The goal of observability is to provide a level of introspection that helps people reason about the internal state of their systems and applications.
- Seeing a recurring theme: there's an emphasis on how observability is about understanding the stack trace and flow. Distributed tracing allows us to break down and vidualize each individual step to see how a buggy environment became that way.
- Goal: shift away from cause-based monitoring and toward symptom-based monitoring (from reactive to proactive).
- Observability can be a precursor to many things such as:
    - chaos engineering/continuous verification
    - feature flagging
    - progressive release patterns (blue/green deployments)
    - incident analysis/blameless postmortem

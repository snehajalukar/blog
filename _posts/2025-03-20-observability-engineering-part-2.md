---
layout: post
title: Observability Engineering - Part 2 (Chapters 5 - 9) Summary
categories:
- General
feature_image: "https://picsum.photos/2560/600?image=872"
---

Hi! My name is Sneha, and this is the second post in a series of blog posts I'm writing where I summarize key takeaways from Observability Engineering, by Charity Majors, Liz Fong-Jones and George Miranda. There are 5 parts to this book, and so I'm planning on writing 5 individual posts in total - and will keep adding to each part as I progress reading.

Grab a snack, and let's continue!

![here we go](https://media.giphy.com/media/fvqIM1ZedWCcYNboBZ/giphy.gif?cid=790b7611nmkfoh4myzj0j0wsv4e0iuna5ir65ibhuwmmnxy4&ep=v1_gifs_search&rid=giphy.gif&ct=g)

<b> Chapter 5: Structured Events Are the
Building Blocks of Observability </b>

Summary/Key Takeaways
- The fundamental building block of observability: structured event.
- Prerequisite for observability: arbitrarily wide structured events.
- Definition of an event: a record of everything that occured while one particular request interacted with your service.
- The book makes a distinction between metrics/telemetry and observability; metrics are pre-aggregated reports and disconnected (singular pieces of data).
- Events are snapshots of what happened at a particular point in time.
- Structured data is clearly defined and searchable; unstructured data isn't organized in an easily searchable manner and is usually stored in its native format.
- Unstructured logs can be made into structured logs - by adding context and exploring different formatting.

<b> Chapter 6: Stitching Events Into Traces</b>

Summary/Key Takeaways
- Distributed traces are simply an interrelated series of events.
- "Distributed tracing is a method of tracking the progression of a single request—called a trace—as it is handled by various services that make up an application. Tracing in this sense is “distributed” because in order to fulfill its functions, a singular request must often traverse process, machine, and network boundaries."
- Requests often traverse messy and upredictable paths through a distributed system. To construct the view, we need five pieces of data for each component:
    - TraceID, SpanID, ParentID, Timestamp, Duration
    - Any additional data added to a span is a series of tags:
        - ex: Service Name, Span Name
- "Events are the building blocks of observability, and traces are simply an interrelated series of events. The concepts used to stitch together spans into a cohesive trace are useful in the setting of service-to-service communication."
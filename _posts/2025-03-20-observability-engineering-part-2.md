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

<b> Chapter 7: Instrumentation with OpenTelemetry </b>
- Telemetry records what your code did when processing a particular set of requests.
- OTel (Open Telemetry) is the open source standard for application instrumentation among observability solutions. 
- This chapter provides a crash course in OpenTelemetry concepts. 
    - Concepts (that I didn't know):
        - Tracers: A component within the SDK that is responsible for tracking which span is active in your process. It also allows you to access and modify the current span.
        - Meter: A component within the SDK that i responsible for tracking which metrics are available to report on in your process.
        - Context propagation: An integral part of the SDK that deserializes context about the current inbound request from headers (andand serializes it to pass downstream to a new service)
        - Exporter: A plug-in for the SDK that translates OTel in-memory objects into the appropriate format for delivery to a specific destination. Destinations may be local (like a log file or stdout) or remote (like an aggregator or monitoring service of some sort).
        - Collector: A standalone binary process that can be run as a proxy or sidecar that receives telemetry data, processes it + tees it to a configured destination.
- We can go an extra mile and add metrics to traces.

<b> Chapter 8: Analyzing Events to Achieve Observability </b>
- Prior to observability, system and application debugging mostly occured by building upon what you know about a system. This strategy of relying on runbooks, however, is largely wasted as modern systems rarely fail in precisely the same way twice.
- First principle: a basic assumption about a system that was not deduced from another assumption. Debugging from first principles is basically a methodology to follow in order to understand a system scientifically.
- The core analysis loop is useful:
    - Start with "What are you trying to understand"
    - Visualize telemetry data to find relevant performance anomalies.
    - Search for common dimensions with in the anomalous area by grouping or filtering for different attributes in your wide events.
    - Has this isolated likely dimensions that identify potential sources of the anomaly?
- A case against AIOps (at least as far as it stands today): AI will usually fail to pinpoint the right size of cases and parameters that will ultimately be used to nail down a root cause.

<b> Chapter 9: How Observability and Monitoring Come Together </b>
- Monitoring is best suited to evaluating the health of systems.
- Observability is best suited to evaluating the health of software.
- Orgs that take on the responsibility of running their own bare-metal systems need monitoring that examines low-level hardware performance. Organizations that outsource hardware-level operations to an IaaS provider won't need metrics and aggregates that perform at that level. 
- The exception to the above are higher-order infra metrics like CPU usage, memory consumption and disk activity - which are indicative of physical performance limitations (so important to watch as a software engineer as they can indicate problems triggered by code). 
- Observability is more proactive - its practices demand that engineers should always watch code as it is deployed and should time exploring code in production, watching users use it, and looking around for outliers and trails to follow.
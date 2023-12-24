# Shared Principles

## Introduction

### Purpose

Our program creates many different software products across its large multi-organizational team. In order to develop interoperable software and facilitate productive collaboration, this document establishes a set of shared principles for software development. 

### Request

All teams working with the program will review this document and raise any concerns, questions, or comments with the program as necessary. After discussion, revision, and/or establishment of further clarifying procedures, organizations will commit to following these common principles in their work.

<!-- above this can be deleted -->

## Shared principles for general collaboration

### Inter-organization collaboration

<!-- this has gone into swd methodology -->

Projects within the program will involve multiple teams, each with different areas of expertise and focus. 

While the government will delineate areas of focus for each organization, there will often still exist areas of overlap and ambiguity between efforts, as well as areas for synergy and collaboration. 

Teams will work to proactively identify these areas and directly connect with each other in order to share progress, find areas of synergy, and collaborate on products. In particular, teams will not let the government to become the bottleneck in communication or collaboration with other teams. 

In the situation when focus areas or tasks must be clarified or delineated in order to move forward, teams will proactively escalate to the government for a decision.

### Organize around iterative value delivery

<!-- this has gone into swd methodology -->

Products should not be made for their own sake; rather, they should be aimed at delivering value by meeting the needs and requirements of the end customer. Teams will organize their work around value delivery and impact towards the end customer. 

Iterative delivery presents opportunities for discovery of and reprioritization to customer requirements, as well as opportunities for inter-team collaboration. Teams will deliver in-progress work items iteratively, in order to receive feedback from the customer, government, and larger program, as well as to allow greater opportunity for collaboration and coordination with other teams. While there is no universal rule for delivery cadence, teams will strive to reduce their cycle time for value delivery.

### Use of common platforms

<!--This has gone into common platforms-->

Shared platforms with collective adoption and usage are critical for facilitating collaboration, coordination, information sharing, and situational awareness across a large, multi-organizational team.

The preferred communication platform for the program is Slack. Teams will ensure that they are quickly reachable within Slack and will use it for program communications as much as is securely possible. The preferred platform for information sharing, intra-program planning, and collaboration is Gitlab. Teams will use Gitlab for program information sharing, planning, and collaboration as much as is securely possible. 

Project-specific communications and collaboration platforms should default to these, but may deviate when necessary to accommodate project-specific needs, such as security.

### Use of common processes and standards

<!--This has gone into common platforms and is covered in team / program events-->

Similar to shared platforms, the use of common processes and standards are critical for facilitating collaboration, coordination, information sharing, and situational awareness.

The government will also specify common processes and standards across the program. These will include processes for higher-level strategic alignment, such as a synchronized portfolio planning / review process, as well as mundane processes for daily tasks, such as common processes and standards for meeting scheduling, support tickets, out-of-office indicators, or information organization. 

Teams will align with these processes and standards. In addition (and more importantly), teams will work to provide feedback and continuously improve on these common program processes and standards in order to become a more effective team.

### Transparency of work

<!-- this has gone into swd methodology -->

Transparency of work is critical to facilitating information discovery and situational awareness across a large, multi-organizational team.

Teams will make artifacts, code, and documentation transparent to the entire program as much as is securely possible. Teams will also make plans and ongoing work priorities, including roadmaps, epics, and issues, transparent to the entire program as much as is securely possible. 

Information that is made available to other teams should be **visible, accessible, and understandable** - meaning that other team members can locate it, access it, and recognize the content, context, and applicability of it. 

### Agile development methodology

<!-- This has gone into swd-methodology -->

Software development efforts will be organized using the Scaled Agile Framework software development methodology. 

All teams will operate on synchronized two-week sprints set by the government. Releases for each product will be held quarterly.

To each product team, the government will assign product owner(s), who ensure that the product direction is aligned with stakeholder needs. In particular, the product owner will continuously prioritize the backlog and create larger epics for the product, in consultation with the team and technical subject matter experts.

Each team is expected to have a team member to fulfill the “scrum master” role for the team. They need not be a certified scrum master but should be familiar with the principles of scrum and their responsibilities as a scrum master. 

The team should be familiar (or willing to learn) about the principles and processes of scrum. 

The product team will hold standard agile ceremonies, such as standup, sprint planning, backlog refinement, sprint demonstrations, and sprint retrospectives. The product owner will lead some of these meetings, such as sprint planning and backlog refinement. The government team will also lead a scrum-of-scrums, which a representative from each product team will attend. The government will engage end users for their feedback as often as possible, inviting them to sprint demos and other sprint meetings when appropriate. 

All work items, including items in the backlog, active work in progress items, and larger epics, will be tracked in the government Gitlab instance. All types of technical work, including code, documentation creation, research, integrations, etc., will be planned in sprint planning and tracked in the government Gitlab instance.

### Software delivery & CI/CD

<!-- This can go into SDP CI/CD part -->

All code and associated documentation will be delivered to the government Gitlab instance.  
Software delivery will follow DevSecOps best-practices. Code, corresponding to the work items completed, will be delivered by teams at least once each sprint. It will be automatically testing in the government’s CI/CD pipeline for unit and security tests. These results, as well as the tests themselves, will be easily viewable to teams for quick iteration.
CI/CD and automatic testing will be performed within the government Gitlab instance. 

### Interoperability of software products

<!-- This can go into SDP -->

Within software development efforts, teams will need to work closely with other teams and the government in order to ensure interoperable usage of their products.
Teams will work collaboratively with other teams and the government to design intelligent interfaces and APIs to enable interoperability with their products, as well as other AI/ML tools.
In order to ensure interoperability of products, the government will have the right to mandate the use of certain interfaces or APIs.

### Software development plan

<!-- This can go into SDP intro -->

Software development will follow the government’s Software Development Plan (SDP). This document broadly specifies the style, dependency management, testing plan, and common tools in order to ensure a baseline consistency between different teams’ code. 

The government will accept feedback and inputs on the SDP and make updates regularly in order to ensure best software development practices. The SDP is designed to simplify the process of creating high-quality  software and reduce variability between projects in terms of their structure, design, testing, packaging, and documentation. It is designed to be reasonable and not impose heavy burdens.

Each team will provide a sub-document to the government’s SDP which provides further details on the software development practices, style, and assumptions for their projects. 
# CDAO A2 Division Shared Principles for Software Development

## Introduction

### Purpose

The CDAO Assessment & Assurance (A2) Division creates many different software products across its large multi-organizational team. In order to develop interoperable softwfare and facilitate productive collaboration, this document establishes a set of shared principles for software development within the division. 

This document is an amendment to the [A2 Division Shared Principles](./shared-principles-general.md). 

### Request

All teams supporting CDAO A2 in software development efforts will review this document and raise any concerns, questions, or comments with the division as necessary. After discussion, revision, and/or establishment of further clarifying procedures, organizations will commit to following these common principles in their work with the division.

## Shared principles for A2 software development projects

### Interoperability of software products

Within software development efforts, teams will need to work closely with other teams and the government in order to ensure interoperable usage of their products.
Teams will work collaboratively with other teams and the government to design intelligent interfaces and APIs to enable interoperability with their products, as well as other AI/ML tools.
In order to ensure interoperability of products, the government will have the right to mandate the use of certain interfaces or APIs.

### Agile development methodology

Software development efforts will be organized using the Scaled Agile Framework software development methodology. 

All teams will operate on synchronized two-week sprints set by the government. Releases for each product will be held quarterly.

To each product team, the government will assign product owner(s), who ensure that the product direction is aligned with stakeholder needs. In particular, the product owner will continuously prioritize the backlog and create larger epics for the product, in consultation with the team and technical subject matter experts.

Each team is expected to have a team member to fulfill the “scrum master” role for the team. They need not be a certified scrum master but should be familiar with the principles of scrum and their responsibilities as a scrum master. 

The team should be familiar (or willing to learn) about the principles and processes of scrum. 

The product team will hold standard agile ceremonies, such as standup, sprint planning, backlog refinement, sprint demonstrations, and sprint retrospectives. The product owner will lead some of these meetings, such as sprint planning and backlog refinement. The government team will also lead a scrum-of-scrums, which a representative from each product team will attend. The government will engage end users for their feedback as often as possible, inviting them to sprint demos and other sprint meetings when appropriate. 

All work items, including items in the backlog, active work in progress items, and larger epics, will be tracked in the government Gitlab instance. All types of technical work, including code, documentation creation, research, integrations, etc., will be planned in sprint planning and tracked in the government Gitlab instance.

### Software delivery & CI/CD

All code and associated documentation will be delivered to the government Gitlab instance.  
Software delivery will follow DevSecOps best-practices. Code, corresponding to the work items completed, will be delivered by teams at least once each sprint. It will be automatically testing in the government’s CI/CD pipeline for unit and security tests. These results, as well as the tests themselves, will be easily viewable to teams for quick iteration.
CI/CD and automatic testing will be performed within the government Gitlab instance. 

### Software development plan

Software development will follow the government’s Software Development Plan (SDP). This document broadly specifies the style, dependency management, testing plan, and common tools in order to ensure a baseline consistency between different teams’ code. 

The government will accept feedback and inputs on the SDP and make updates regularly in order to ensure best software development practices. The SDP is designed to simplify the process of creating high-quality  software and reduce variability between projects in terms of their structure, design, testing, packaging, and documentation. It is designed to be reasonable and not impose heavy burdens.

Each team will provide a sub-document to the government’s SDP which provides further details on the software development practices, style, and assumptions for their projects. 
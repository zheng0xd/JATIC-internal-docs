# Agile Roles and Responsibilities

## Purpose

This document describes the key roles and their responsibilities within the Agile scrum methodology.

Details about agile ceremonies and meetings can be found in [`Calendar`](https://gitlab.jatic.net/jatic/calendar/-/issues/?sort=created_date&state=all&label_name%5B%5D=Sprint%20Ceremony&first_page_size=20).

All of the blocks are quotes from the reference below.

## Roles

### Development team member

> The development team can be comprised of all kinds of people including designers, writers, programmers, etc.  
>
> You can think of it in the same way as when you have a house project and you hire a developer. They develop the project and do the work. Yes, this might mean they lay bricks, do plumbing, even dig holes, but the person is known as a developer. So, that means the ‘developer’ role in scrum means a team member who has the right skills, as part of the team to do the work.
>
> The development team should be able to self-organize so they can make decisions to get work done. Think of a development team as similar to a production support team that is called in during the night because something has gone wrong. The development team, like the production support team, can make decisions and deliver the fix/value for the problem at hand. Self-organization isn’t about disrespecting the organization, but rather about empowering the people closest to the work to do what’s needed to solve the problem.   
> 
> The development team’s responsibilities include:
> 
> - Delivering the work through the sprint.
> - To ensure transparency during the sprint they meet at standup, which provides a dedicated place for team members to seek help, talk about success and highlight issues and blockers. The scrum master might facilitate the daily scrum, but ultimately it is the responsibility of the development team to run this meeting. It is their meeting to help them, as a group, to inspect and adapt the work they are doing and work in a more effective way.

### Development team lead

The development team lead is not a traditional agile role, but is relevant in the context when we have product owners from the government and development teams from industry. In this case, the development team lead is the techncial leader and main POC of the industry team.

Responsibilities of the development team lead include: 
- Technical leadership of the development team and guidance to the government product owner
- Close coordination with the government product owner to achieve shared product vision 
- Communicating programmtic information and shared vision with the development team to ensure situational awareness
- Day-to-day management of development team

### Product owner

> Scrum product owners understand the customer and business requirements, then create and manage the product backlog based on those requirements. Since agile teams are, by design, flexible and responsive, it is the responsibility of the product owner to ensure that they are delivering the most value. The business is represented by the product owner who tells the development team what is important to deliver. Trust between these two roles is crucial.
>
> The product owner should not only understand the customer but also have a vision for the value the scrum team is delivering to the customer. The product owner also balances the needs of other stakeholders in the organization.  
> 
> So the product owner must take all these inputs and prioritize the work. This is probably their most important responsibility because conflicting priorities and unclear directions will not only reduce the effectiveness of the team but also could break the important trust relationship that the business has with the development team.
> 
>  The Scrum Guide defines the product owner's responsibilities as:
>
> - Managing the scrum backlog - This does not mean that they are the only one putting in new product backlog Items into the backlog. But ultimately they are responsible for the backlog that the development team pulls to deliver from. That means the product owner should know about everything that is in the backlog and other people that add items to the product backlog should ensure that they communicate with the product owner. 
> - Release management - The sprint is not a release cycle, but instead a planning cycle. That means that scrum teams can deliver at any time. Ideally, they would deliver frequently throughout the sprint allowing the sprint review to review real customer usage and feedback. However continuous delivery is not always possible and other release models are required. It is important for the product owner to know when things can and should be released.
> - Stakeholder management - Any product will have many stakeholders involved ranging from users, customers, governance and organizational leadership. The product owner will have to work with all these people to effectively ensure that the development team is delivering value. That can mean a large amount of stakeholder management and communication.

It is ultimately the product owner's responsibility to have a clear vision for the product and manage its delivery of value to customers. This vision should be developed alongside the development team lead, building a shared vision for the product.

Some emphasized or additional product owner responsibilities within our context:

- Roadmap creation: In addition to managing the scrum backlog for the short term, the product owner is also responsible for creating epics, together constituting a roadmap, for the longer term development of the product. This roadmap and long term vision for the product must be clearly communicated with the product team. 
- Stakeholder coordination: The DOD has a huge number of stakeholders, many who are working in adjacent or overlapping spaces. In addition to stakeholder management to set priorities, the product owner must actively engage, coordinate, and collaborate with others working in the space to achieve adoption of our products.
  - Product owners should talk with their product team and with the program management team if they would like help in discovering or pursuing external engagements.
- Programmatic coordination: Since the JATIC program has multiple loosely coupled components, product owner is responsible for coordinating with the program manager and other product owners and managing the backlog to align their development to the broader vision. 

There are a few specific requirements for Product Owners necessary for appropriate execution of their actions. These are specific to the role within JATIC:

Day-to-day tasks:
- Perform backlog grooming to prioritize items in the backlog.
- Work with the team in refining Issue tickets.
- Verify and ensure satisfaction of program requirements by the team.

Weekly/Bi-weekly tasks:
- Participate in sprint planning meetings with the team, representing the user and program. 
- Participate in sprint review and retrospective meetings with the team, representing the user and program.
- Participate in weekly program-wide Product Owner Sync, representing the team.

Quarterly tasks:
- Participate in program increment planning sessions and help set objectives for the team.
  - Give the business value rating of team increment objectives (with discussion from team), both up-front during the increment planning as well as in review after the increment.

### Technical SME

The Technical SME is not a traditional agile role, but serves a unique and extremely important role within our program's context. For a given product, the Technical SME has a deep understanding of both the technical subject matter and the mission specific context in order to advise the product owner and development team. The role includes a variety of activities, including aiding in development and integration of the product, supporting deployment to DoD environments, and acting as the deputy product owner when necessary.

### Scrum Master

> The scrum master is the role responsible for gluing everything together and ensuring that scrum is being done well. The scrum master is a servant leader which not only describes a supportive style of leadership but describes what they do on a day-to-day basis. 
> They serve the product owner by helping them better understand and communicate value, to manage the backlog, help them plan the work with the team and break down that work to deliver the most effective learning. Serving the development team, the scrum master helps them self-organize, focus on outcomes, get to a “done increment,” and manage blockers. The scrum master also serves the organization at large, helping them understand what scrum is and create an environment that supports scrum.
> 
> The scrum master focuses on:
>
> - Transparency - To effectively inspect and adapt it is important that the right people can see what is going on. But this is actually much harder than it looks. The scrum master is tasked with ensuring that the scrum team works in a transparent way. Examples include creating story maps and updating Confluence pages with retrospective ideas.
> - Empiricism - A fundamental for scrum and agile approaches the idea that the best way of planning is to do work and learn from it. The empirical process is not easy and requires the scrum master to coach the scrum team on breaking down work, describing clear outcomes, and reviewing those outcomes.
> - Self-organization - Telling a development team they can self-organize does mean that the team will self-organize. In fact, self-organization comes over time and requires help and support. The scrum master will encourage team members to step outside their comfort zone and try different things and use practices such as ‘delegation poker’ to expose and challenge predefined ideas about role boundaries and responsibilities.
> - Values - Scrum defines 5 values of courage, focus, commitment, respect, and openness not because they are nice to have, but because they create an environment of physiological safety and trust. Following the values is the responsibility of everyone in the scrum team, but the scrum master takes an active role in encouraging and reminding everyone of the importance of those values.

## References

1. https://www.atlassian.com/agile/scrum/roles

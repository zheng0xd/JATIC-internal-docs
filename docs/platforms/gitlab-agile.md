# Gitlab for Agile Software Development

This page provides program guidelines on the usage of Gitlab's features for agile. It is particularly focused on Scrum, but can also be adapted to Kanban. 

## Issues

### Issue progression

Issues are used to represent user stories or work items. As an issue moves through its stages from product backlog to working software, its associated information and artifacts should also mature.

#### Added to the backlog

An issue added to the product backlog can simply be a neat idea, unrelated to the current objectives. 

Issues which require more information, scoping, or decomposition should be labeled as `stub`. 

#### Fully refined

When an issue is refined, it should have the following properties:

1. A populated description, with a problem statement, definition of done (potentially as subtasks), and any other relevant resources
1. An associated epic that the issue falls within
1. A weight, according to its number of story points
1. The `status::refined` label

#### Committed to for a sprint

When an issue is committed to for a sprint, it should have the following properties (in addition to the above):

1. The sprint that it was committed to (Gitlab calls this the "iteration")
1. The assignee who is responsible for completing it
1. The `status::ready to start` label

#### Work-in-progress

After starting to actively work on an issue, the assignee should change its status to `status::in progress`.

#### Opened merge request

After opening a merge request (MR) that fulfills an issue, the assignee should change its status to `status::in review`. 

#### Issue closed

Issues should be closed when the features have been developed an approved. Usually, this means that its corresponding MR has been merged, or its work has been accepted during sprint review.

### Visualization

#### Issue boards

Issues boards can be set up to view ongoing work as a Kanban by adding the `status` labels as columns. See the [MIT-LL Kanban board](https://gitlab.jatic.net/jatic/cdao/maite/-/boards/) as an example.

#### Burndown charts

Burndown charts can be used to visualize the amount of work that has been completed in a sprint. See this [JATIC program burndown chart](https://gitlab.jatic.net/groups/jatic/-/cadences/6/iterations/54) from NOV 2023 as an example.

### Story point estimation

Weights are standardized across all teams and follow the Fibonacci sequence. Story points correspond to the complexity of a task, amount of work, and risk or uncertainty. Below is a mapping to the approximate hours of each.

| Weight | Approximate hours |
| --- | --- |
| 1	| 0-4 hours |
| 2	| 4-8 hours |
| 3	| 8-16 hours |
| 5	| 16-32 hours |
| 8	| 32-64 hours |

To read more, see [Story points and estimation](https://www.atlassian.com/agile/project-management/estimation) from Atlassian.

## Merge requests

Many issues will create changes which must be incorporated into the larger project. These changes should be incorporated using a Merge request (MR). 

Merge requests include the following information:

- A description of the content or changes to be incorporated
- Code changes
- CI/CD status and logs
- Commit history

Before incorporating changes from an MR into the large project, the content typically needs to be reviewed. A Merge request review (MRR) provides mechanisms for the team to leave comments or make suggestions on the MR, giving evidence of the review and naturally documenting the relevant discussion, considerations, suggestions, and decision. 

To read more, see [Merge Requests](https://docs.gitlab.com/ee/user/project/merge_requests/) and [Merge Request Reviews](https://docs.gitlab.com/ee/user/project/merge_requests/reviews/) from Gitlab.

### Best practices for reviewing & approving

- MRRs should only be performed by those who did not make any commits in the MR. In other words, reviewers only review, make comments, and discuss with the people who suggested the changes. This is slower, but cleaner and less susceptible to bias. 
- A MR should be approved by the project maintainer or their delegated reviewer before being incorporated in to the main branch
- Projects should document their acceptance criteria for MRs within their documentation. 

### MRRs within an agile sprint

- MRRs do not not need to be completed within the same sprint that an issue was committed to. However, reviewers should consider reviewing MRs a priority and complete reviews in a timely fashion. 
- If a sprint is particularly heavy with MRRs, sprint capacity should be adjusted accordingly.
- An issue should not be closed until the corresponding MR has been merged.
- An issue and the corresponding MR should both be assigned to the author, while reviewers should be assigned as reviewers. 

!!! note

    The MR author may need to poke reviewers to encourage and remind them to complete their review.

## Epics

Epics are collections of issues and other epics which are used to group larger work efforts. 

We will track two types of epics: program epics and feature epics. 

### Program epics

Program epics are labeled as `epic::program`. The purpose of program epics are to:

1. Set the major goals for the associated product during a quarter or a longer time-period
2. Enable tracking, communication, consistency, and clarity of high-level goals within that time-period
3. Help group lower-level child epics

Within the description field, a program epic should contain:

- a high-level description of the epic goals
- the dependencies for the goals within the epic
- the risk items and mitigations
- the content which will be demoed the end of an increment

Program epics often correspond to objectives set for a product within increment planning.

!!! tip

    If an effort is expected to take three sprints or more, a program epic should probably be made, and the task should be decomposed into smaller child epics.

### Feature epics

Feature epics are labeled as `epic::feature`. The purpose of feature epics are to:

1. Set the goals for a larger effort or a sprint
2. For a set of related issues, provide a higher-level picture of what the issues should come together to achieve
3. Enable tracking and communication of the lines of effort at a higher level, for instance, at scrum of scrums sessions

The following provide some guidelines on when it may be appropriate to make an epic:

- If an effort is made up of multiple issues, none of which give a full picture of the effort, the product owner should probably make an epic to provide insight into the larger objective.
- If an effort involves substantial work across multiple projects, the product owner should probably make an epic.
- If an effort involves substantial work across multiple teams, the product owner should definitely make an epic.

These epics should be created for each product routinely by the product owner before sprint planning. The epics should be shared with the team during sprint planning as overarching sprint themes or goals.

### Visualization

#### Epic boards

Similar to issue boards, epic boards can be used to larger lines of effort across a team. See the [JATIC epic board](https://gitlab.jatic.net/groups/jatic/-/epic_boards/) as an example

#### Roadmps

Epics can also be visualized on a roadmap. See the [JATIC roadmap](https://gitlab.jatic.net/groups/jatic/-/roadmap) as an example. 

### Best practices

- Epics should be created at the lowest group possible. For example, if an epic only involves work involving one team, it should be creating in that team's subgroup.
- Epics should be labelled with the teams that are involved in the effort. This allows easy tracking and filtering at the top-level group.
- Near-term epics should be labeled with their work status, either `status::ready to start`, or `status::in progress`. This helps differentiating between epics which are actively being worked compared to epics which are used for longer term planning. 
- Epics which are actively being worked should be created with start and due dates. 
- Epics should not go on forever! Some larger teams may complete one or more epics per week. For teams working multiple efforts in parallel, they have multiple epics open at the same time for multiple sprints. 

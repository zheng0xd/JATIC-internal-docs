# Gitlab for Agile

## Purpose

This document specifies the usage of Gitlab concepts, such as labels, issues, and epics, for our Agile software development processes.

## Issues

Issues should be populated with a description of the problem statement, the desired behavior, and the definition of done. 

Generally, the product owner should create these, sometimes with assistance from the product technical SME. The work to be completed from a given issue should be understandable on its own. 

Issues will go through multiple stages of refinement, from being added to the backlog as a work item, to refined during backlog refinement, to work-in-progress during a sprint, to completion. As an issue moves through these stages, the information which is provided with the issue should also mature.

### Adding issues

Any one may add issues to the product backlog which correspond to work items, desired improvements / features, etc. The product owner is responsible for both adding issues and prioritizing all of the backlog issues.

### Refining issues

During backlog refinement (aka backlog grooming), the product owner, along with technical SMEs, will refine work items in the backlog, adding clarity to issues, resolving dependencies, and setting priorities. Once an issue is refined, the following properties should exist for an issue:

1. A populated description, with a problem statement, desired behavior, and definition of done (potentially as subtasks)
1. An associated epic / larger effort that the issue falls into (if applicable)
1. A weight, according to its number of story points, preferrably using Agile Planning Poker
1. The `status::ready to start` label should be added to the issue

**If an issue requires one to open a merge request, this should be noted.** If an issue will require technical review it should be noted as a requirement within the issue.  In this case, it is recommended that appropriate reviewers / approvers for the MR be explicitly listed in the issue.

## Labels

Labels can be attached to issues, epics, and merge requests to help organize them. The labels with `::` are "scoped labels", meaning that only one with the corresponding key may be added to a given issue.

At the `jatic` group level, labels the following labels currently exist:

- a labels for each organization involved in work
- `epic::program`, for program level epics. See **Epics**
- `epic::feature`, for feature level epics. See **Epics**
- `status::grooming`, for work items that are of near-term interest, but need to be decomposed or groomed before being added to an iteration
- `status::ready to start`, for work items that are fully refined, prioritized, and ready to be assigned
- `status::in progress`, for work items that are currently being worked on
- `status::in review`, for work items that have opened a merge request currently in review

Projects and groups may add labels to best suit their needs. 

#### Issue weights

Weights are standardized across all teams and follow the Fibonacci sequence. Story points correspond to the complexity of a task, amount of work, and risk or uncertainty. However, by popular demand, the below is a mapping to the approximate hours of each.

Weight / Approximate hours
- 1	/ 0-4 hours
- 2	/ 4-8 hours
- 3	/ 8-16 hours
- 5	/ 16-32 hours
- 8	/ 32-64 hours

### Committing to an issue for an iteration

During sprint planning, the team will commit to issues that they will complete during a sprint. Once an issue is committed to, the following properties should exist for an issue:

1. The current iteration for which planning is occurring
1. Assignment to a person or multiple people who will work on the task

### Issue in progress

During a sprint, when an issue is being actively worked, the **assignee** should add the `status::in progress` label to the issue.

## Merge requests

Many issues will create changes or artifacts which the assignee must incorporate into a larger project. To incorporate changes from a source branch to a target branch, you use a Merge Request (MR). 

When attempting to address an issue with a merge request, the issue should not be considered resolved until the merge request is merged. Merely creating a merge request should not complete the issue.  

Merge requests include:
- A description of the content or changes to be incorporated
- Code changes and inline code reviews
- CI/CD information
- Commit history

In general, a MR should be approved by the project maintainer or their delegated reviewers before being incorporated into the larger project's main branch. 

## Merge request reviews

Before incorporating changes or artifacts from an MR into the larger project, a review of the content is typically necessary. [Merge Request Reviews](https://docs.gitlab.com/ee/user/project/merge_requests/reviews/) provide mechanisms for the team to leave comments or make suggestions on the MR, giving evidence of the review and naturally documenting the relevant discussion, considerations, suggestions, and decision. 

When an issue has a related MR under review, it should be labeled with the `status::in review` label. 

As a rule, MR reviews should be only be performed by those who did not make any commits in the MR. In other words, reviewers only review, make comments, and discussion with the people who suggested the changes. This is slower, but cleaner and less susceptible to bias. 

The appropriate reviewer for a given artifact will depend on the specific project or repository that the artifact falls within. Different projects may have different acceptance criteria for a merge request, which will be documented in their project README. For instance, a MR into infrastructure configuration files may require a different review process than an MR into design documentation. 

Reviews, especially merge request reviews, need not be completed within the same sprint that an issue was committed to. Review requests do not show up formally in a particular user's weight. If it is the case that an iteration is particularly heavy with review requests, please note this to the team to adjust the workload accordingly.

The Merge Request should remain assigned to the author while reviewers are assigned as reviewers. It is important for reviews to be completed in a timely fashion. Reviewers should consider it a priority to review, otherwise the process grinds to a halt. Also, the Merge Request author should poke reviewers (early and often) to encourage and remind them to review. 

### Closing an issue

Issues can be closed when bugs are fixed or requested features have been developed and approved. Usually, this means that an issue can be closed when the merge request which addresses it is merged into the main branch. 
 
Issue can be made to close automatically when related merge request are merged into the default branch, and the commit message or merge request description containes keywoards from a default closing pattern. See [closing issues automatically](https://docs.gitlab.com/ee/user/project/issues/managing_issues.html#closing-issues-automatically) for more details.

## Epics

### Epics Background & Best Practices

Epics are collections of issues and other epics which are used to group collections of work. Epics live at the group-level, not the project-level. Epics can be nested within other epics.

1. Epics should be created at the lowest group possible. For example, if an epic only involves work involving one organization, it should be creating in that organization's subgroup.
1. Epics should be labelled with the organizations (i.e., sub-groups) that are involved in the effort. This allows easy tracking and filtering at the top-level group.
1. We will track two types of epics: Program Epics and Feature Epics. All epics should be labelled with either `epic::program` or `epic::feature`.
1. Epics should be labeled with their work status, either `status::ready to start`, or `status::in progress`. This helps differentiating between epics which are actively being worked compared to epics which are used for longer term planning.
1. Epics which are actively being worked (i.e., `status::ready to start` or `status::in progress`) should always be created with start and due dates. The start date should reflect when the epic was actually started, generally the first day of the sprint. The larger the epic, the more squishy the due date can be.

### Program Epics

The purpose of program epics are to:

1. Set the major goals for the associated product during a quarter or a longer time-period
2. Enable tracking, communication, consistency, and clarity of high-level goals within that time-period
3. Help group lower-level child epics

Program epics should be created for each product, by the associated product owner during quarterly planning. They should be created with feedback and discussion with the program manager and other product owners.

Within the description field, a program epic should contain:

- a high-level description of the goals for the product for the epic
- the dependencies for the goals within the epic
- the risk items across the epics
- the mitigations for those risk items
- the content which will be demoed the end of an increment (each quarter).

A common usage of a program epic may be as a Quarterly Epic, especially when a product has a release within the quarter. Then, this quarterly program epic would specify the features and goals to be delivered within that quarterly release. However, not all program epics need to be quarterly. For instance, a three month contracting effort starting mid-quarter should likely have an associated program epic.

If an effort is expected to take three sprints or more, a program epic should be made, and the task should be decomposed into smaller child epics.

### Feature Epics

The purpose of feature epics are to:

1. Set the goals for a larger effort or a sprint
2. For a set of related issues, provide a higher-level picture of what the issues should come together to achieve
3. Enable tracking and communication of the lines of effort at a higher level, for instance, at scrum of scrums sessions

The following provide some guidelines on when it may be appropriate to make an epic:

- If an effort spans more than 5 issues, the product owner should probably make an epic (especially if the issues interact in a complex way)
- If an effort is made up of multiple issues, none of which give a full picture of the effort, the product owner should probably make an epic to provide insight into the larger objective.
- If an effort involves substantial work across multiple projects (i.e., repositories), the product owner should probably make an epic.
- If an effort involves substantial work across multiple organizations (i.e., subgroups), the product owner should DEFINITELY make an epic.

These epics should be created for each product routinely by the product owner before sprint planning. The epics should be shared with the team during sprint planning as overarching sprint themes or goals.

Within the description field, an epic should contain:

- A high-level description of the goal of the epic, and
- The completion criteria for the epic.

Epics should not go on forever! They should be closed when the completion criteria is reached. Timeframes for completion and scope of epics may vary somewhat better teams. Some larger teams may complete one or more epics per week. For teams working multiple efforts in parallel, they have multiple epics open at the same time for multiple sprints. However, if an effort is expected to take three sprints or more, a program epic should be made, and the task should be decomposed into smaller child epics.

# Gitlab Organization

## Purpose

This document specifies the usage of Gitlab concepts for organization.

## Primer

For those who are unfamiliar with gitlab, we highly recommend [Gitlab Project Management](https://www.youtube.com/watch?v=9W4oxjdAwUs) and [Comparing Gitlab and Bitbucket terms](https://about.gitlab.com/blog/2017/09/11/comparing-confusing-terms-in-github-bitbucket-and-gitlab/) for background on groups, projects, issues, epics, milestones, and iterations.

## Groups, subgroups, and projects

The government team and FFRDC support are direct members of the top-level JATIC group. The subgroups of the JATIC group correspond to the different organizations who are working on the program. For example:

- CDAO - the CDAO Gov team, as well as FFRDC support are direct members.
- Kitware - the Kitware team are direct members.
- TwoSix - the TwoSix team are direct members.

Direct members in the top-level JATIC group will inherit permissions on all subgroups and projects within the subgroups. In general, they will have the developer role in all repositories within the namespace. Teams will be have the ability to set roles within their subgroup, which will be inherited by all projects within the group.

Projects will generally live within the subgroup corresponding to the organization who is leading development. Some projects, which are large and cross-organizational, may live in the top-level JATIC group.

**By default, it is recommended that groups, subgroups, and the projects within are set to the "internal" visibility, meaning that they can be discovered and cloned by any signed in users.** All groups are able to create "private" visibility repos as well if needed.

## Gitlab Project Points of Contact (POC) and Roles

Each project is responsible for managing roles within the project with respect to management of the Gitlab repository. The projects should set appropriate roles for project members to fill the following needs. Each of the below role also can fulfil the tasks of any subsequent role. E.g., the POC should also be maintainers on the repo and can perform mantainer tasks (fyi, maintainer is a user role defined in/by Gitlab). Maintainers also can do development, but cannot approve their own MR. 

1. POC: A role for responding to questions regarding to the repository. The POCs should be noted in the README.md of the repository. The POC is essentially a lead maintainer of the repo. All POCs should be assigned maintainer (or owner) roles of the repo in their repo's user rules on Github. Each project/repo should have either one POC and one deputy POC or two POCs assigned.
2. Maintainer: A role responsible for managing the repository. Approval from a maintainer is required for merge requests. Reviews can be largely delegated, but a maintainer is responsible for every change to the protected branches of the repository (e.g., main and dev). E.g., the main review might be done by a developer assigned by a maintainer and the maintainer then check the review and MR before approving. Maintainer are responsible for ensuring that the appropriate maintainer is providing approval of the merge request (there will be multiple maintainers for a repo), that appropriate reviews (by appropriate reviewers) take place, and that appropriate processes have been followed in the merge request. Maintainers should all have the "maintainer" user role defined in Gitlab.
3. Developer: A role for doing development and reviews. Developers can create issues, update issues, create branches, create merge requests, and provide feedback/review on merge requests.  

Other roles that exist in Gitlab are "reporter", "guest", and "minimal access". These roles are largely unused, in favor of the above. 

Upon creation of a new Gitlab Project, the above roles should be assigned for the project. Roles should be maintained.

Details on access by role can be found here https://gitlab.jatic.net/help/user/permissions

### Checking Roles
POC and DPOC should be noted in the README.md in the top level of the repo.
Maintainers and developer roles can be found under Project Information -> Members.

### Example

> # Example project
> ...
>
> ...
> 
> POC: David Jin @djin 
> 
> DPOC: Ari Kapusta @akapusta
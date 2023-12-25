# Gitlab Organization

## Gitlab Project Points of Contact (POC) and Roles

<!--Think that everything below is probably not necessary-->

Each project is responsible for managing roles within the project with respect to management of the Gitlab repository. The projects should set appropriate roles for project members to fill the following needs. Each of the below role also can fulfil the tasks of any subsequent role. E.g., the POC should also be maintainers on the repo and can perform mantainer tasks (fyi, maintainer is a user role defined in/by Gitlab). Maintainers also can do development, but cannot approve their own MR. 

1. POC: A role for responding to questions regarding to the repository. The POCs should be noted in the README.md of the repository. The POC is essentially a lead maintainer of the repo. All POCs should be assigned maintainer (or owner) roles of the repo in their repo's user rules on Github. Each project/repo should have either one POC and one deputy POC or two POCs assigned.
2. Maintainer: A role responsible for managing the repository. Approval from a maintainer is required for merge requests. Reviews can be largely delegated, but a maintainer is responsible for every change to the protected branches of the repository (e.g., main and dev). E.g., the main review might be done by a developer assigned by a maintainer and the maintainer then check the review and MR before approving. Maintainer are responsible for ensuring that the appropriate maintainer is providing approval of the merge request (there will be multiple maintainers for a repo), that appropriate reviews (by appropriate reviewers) take place, and that appropriate processes have been followed in the merge request. Maintainers should all have the "maintainer" user role defined in Gitlab.
3. Developer: A role for doing development and reviews. Developers can create issues, update issues, create branches, create merge requests, and provide feedback/review on merge requests.  

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

### Using boards

Issue boards are recommended for viewing issues as a Kanban. 

Each project will have a list of issues associated issues. 

A group will show all of the issues associated with its subprojects. Boards at higher level groups will often contain a large number of issues from a large number of disparate projects. Thus, 

Therefore, if one is only interested in issues related to a specific project or group, viewing issues at that project or group level is recommended for more precision. For example, compare the [SDP board](https://gitlab.jatic.net/jatic/docs/sdp/-/boards/) with the JATIC board above. 

Epics can be viewed with epic boards, as well as on the roadmap. For example, see the [JATIC epic board](https://gitlab.jatic.net/groups/jatic/-/epic_boards/) and [JATIC roadmap](https://gitlab.jatic.net/groups/jatic/-/roadmap).

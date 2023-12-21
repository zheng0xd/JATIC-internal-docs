# Branch, Merge, Release Strategy

JATIC software libraries will be developed and maintained as projects on GitLab.
The following outlines the recommended strategy for creating branches, merging, and releasing versions of individual JATIC libraries via GitLab.
For more general guidance on using GitLab within the Agile project management process, see the [Gitlab for Agile page](https://gitlab.jatic.net/jatic/docs/org-process/-/blob/main/Gitlab%20for%20Agile.md).

Project maintainers are ultimately responsible for defining the branch, merge, and release procedures for their project. The [Gitlab for Agile page](https://gitlab.jatic.net/jatic/docs/org-process/-/blob/main/Gitlab%20for%20Agile.md) describes roles within the project. 
While each project should generally follow the guidance below, the procedure can be modified as needed to support the unique needs of the project.
Each project's strategy should be clearly documented in the Contributing section of the project's README.

## Branch Strategy

- Development on the project will be defined, assigned, and tracked using [GitLab's Issues](https://docs.gitlab.com/ee/user/project/issues/).
Issues may include new features, bug fixes, updates to documentation, or development of demonstrations.
Developers who have been assigned Issues will implement their updates to the code by creating and pushing commits to feature branches.
All feature branches must have an associated Issue in Gitlab.

- JATIC projects should follow one of three common [Git branching strategies](https://www.gitkraken.com/learn/git/best-practices/git-branch-strategy): Git Flow, GitHub Flow, or GitLab Flow.
Their selected strategy should be documented in the Contributing section of the project's README.
Any differences from the official branching strategies should also be noted in that section.

- Feature branches should have an intuitive name, with the Issue number as the prefix,
followed by the name of the Issue or a description of the feature (e.g., %{issue id}-%{feature}).
See [GitLab's guidance on branch names](https://docs.gitlab.com/ee/user/project/repository/branches/#name-your-branch) for more information on how to connect Issues to their corresponding branch and merge request.

## Merge Strategy

- Updates to the main/dev branch should only be made through [GitLab's Merge Requests](https://docs.gitlab.com/ee/user/project/merge_requests/). When ready, the developer will open a Merge Request (MR) to merge their feature branch into the main/dev branch.
If the developer would like feedback on their work before they have finished completing their changes, they should mark the MR as a draft.

- When creating the MR, the developer will also assign reviewers who may be other developers or repository maintainers on the project.
While developers can perform review, a project maintainer must provide final approval before the MR can be merged.
Explicit rules on the minimum number of reviewers and who can perform reviews can be specified on a per-project basis and enforced via GitLab settings for the project.
Product Owners can make note of any suggested or required reviewers when creating the original Issue.

- The feature branch should not be merged until the branch is passing all tests and a project maintainer has approved the MR.
Once the MR has been approved, the developer who opened the MR should merge the feature branch into the main/dev branch and the feature branch should be deleted.
If the original Issue number is included as the prefix of the branch name, GitLab will automatically close the Issue when the MR is closed.


## Release Strategy
- Releases should be created and timed according to the desires of the team handling the repo (which includes the product owner), to keep the release version functional.
- [GitLab's Releases](https://docs.gitlab.com/ee/user/project/releases/) will be used to indicate the most stable, up-to-date, and thoroughly tested version of the code.
Prior to a new release, tests should be added for all new functionality and bug fixes (e.g., strive for 100% coverage), and all tests should be passing.
The library's documentation should also be updated to reflect any changes in the new release.
At a minimum, all functions added since the last release should be properly referenced in the documentation's "reference" section.
"Howtos" and "tutorials" should also be added to the documentation for any new functionality, when appropriate.

- Upcoming releases should be announced in the JATIC Slack's "announcements" channel.
- All JATIC integration tests (integration tests at the JATIC level, whichever exist at the time) should pass, in addition to your repo's internal tests. In the case of breaking integration tests, you should communicate closely with the components that break from your change to coordinate a joint release. Coordinated releases should release all necessary updates within an hour of each other.

- Once ready, releases should be created from the main branch if following the Git Flow or GitHub Flow strategy, or from a release branch if following GitLab Flow.
Releases should be named and tagged using [semantic versioning](https://semver.org/),
(i.e., \<Major\>.\<Minor>\.\<Patch\>).
Patch is incremented to indicate bug fixes,
Minor is incremented to indicate new functionality that does not change the core API,
and Major is incremented to indicate compatibility-breaking API changes.

- All changes associated with each release should be documented and communicated to the broader JATIC team via changelogs, release notes, and announcements in JATIC Slack's "announcements" channel. One announcement for the upcoming release, one for the completed release.
Individual projects can decide how to structure and maintain their project's release notes
(e.g., via a "pending release" notes document, with bullets added from each merge request and automated CI checks),
and this process should be documented in the Contributing section of their README.

- JATIC users or other project teams that are also building JATIC T&E tools should use the latest release of any given JATIC library,
and keep their code up to date with each subsequent release.

- Currently, the definition of "deployment" within JATIC can be described as uploading an official release of a JATIC library to publicly available code repositories. Once an official release has been created within GitLab, JATIC libraries can be "deployed" to the following initial approved target environments:
    - [GitHub](https://github.com/)
    - [PyPi](https://pypi.org/)
    - [Conda-forge](https://conda-forge.org/) 

    The procedures and implementation of continuous deployment to these environments via GitLab CI is currently in progress.


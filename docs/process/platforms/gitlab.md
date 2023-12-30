# Gitlab Usage

Our program uses Gitlab as the preferred platform for code storage, CI/CD, DevSecOps, maintaining the product backlog, and tracking in-progress work. 

Our Gitlab instance can be reached at [`https://gitlab.jatic.net`](https://gitlab.jatic.net) and is open for registration to all U.S. government personnel, FFRDC, and UARCs. Furthermore, access to the Gitlab can be provided to all government contractors. 

[Check out Gitlab! &nbsp; :simple-gitlab:](https://gitlab.jatic.net){ .md-button .md-button--primary }

## Joining the instance

### Creating an account

An account can be created in two different ways.

- Users with a `.mil`, `.gov`, or an FFRDC/UARC-affiliated email can self-register for an account at [https://gitlab.jatic.net](https://gitlab.jatic.net).
- Users without such an email should contact program support to have an account created on their behalf. After the account is created, they will receive an email to confirm their email address and reset their password. 

??? note

    If you're reading this, you probably already have access to Gitlab! Hopefully this can still be a helpful reference. :smile:

### Requesting an account for someone else

You can request an account for someone else by create an issue ticket within [`jatic/support`](https://gitlab.jatic.net/jatic/support/-/issues/new#) using the "onboarding" template. 

After the account is created for them, they will receive an email to confirm their email address and reset their password.

### Two-factor authentication

After successfully logging into your account, you will be required to setup two-factor authentication (2FA). Personal devices are authorized for 2FA use.

### Setting up a personal access token

Since our Gitlab instance requires 2FA to login, you will need to set up a personal access token to authenticate with Git or the Gitlab API. See [Personal Access Tokens](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html) from Gitlab for more details. 

If you are not familiar with using Git, feel free to ignore this step.

### Getting added to groups

The program use Gitlab groups to provide team-based and role-based access control to different projects and repositories. These groups are also used for managing calendar invitations, so that invitations do not need to be updated or forwarded when new team members join. 

After you have logged in to Gitlab, ensure that your team admin or program support adds you to the correct groups, corresponding to your team and roles. 

!!! example

    If Alex is onboarding as a scrum master with the IBM team, she will want to be added as a Developer on "TEAM - IBM" at `jatic/ibm` and "JATIC Scrum Masters" at `roles/scrummasters`.

    Because Alex was added to the groups "TEAM - IBM" and "JATIC Scrum Masters", she will automatically be sent meetings for their scrum meetings, as well as the scrum of scrums. 

## Learning how to use Gitlab

Gitlab is quite a complicated program because it contains so many capabilities, including code repositories, issue tracking, kanban boards, CI/CD, team access control, wikis, etc. For those familiar with the Atlassian suite of tools, Gitlab offers roughly equivalent functionality to Jira, Confluence, and Bitbucket. 

However, Gitlab can be extremely challenging to use, especially for those who do not come from a software background. For instance, Gitlab documentation is written in markdown and tracked with Git, and while this can provide powerful functionality, it can also be daunting to those who are unfamiliar. 

### Introductory resources

For those who have never used Gitlab before, we highly recommend the excellent series on using Gitlab for project management, particularly:

1. [How to use Issues, Epics, Milestones, and Roadmaps](https://www.youtube.com/watch?v=9W4oxjdAwUs)
1. [How to use Issues, Labels, and Boards](https://www.youtube.com/watch?v=J2u7OqBA_aQ)

In addition, we have recorded a series of [Gitlab lunch and learns](https://gitlab.jatic.net/jatic/docs/presentations/-/tree/master/Gitlab_Lunch_and_Learn), which provide overviews and tutorials of Gitlab for a variety of audiences. These range from Gitlab for project managers to Gitlab for advanced developers and security engineers.

### Learning Gitlab terminology

If you are familiar with the Scrum or SAFe agile methodology, see [How to use GitLab for Agile software development](https://about.gitlab.com/blog/2018/03/05/gitlab-for-agile-software-development/) for a mapping of Agile artifacts to Gitlab features and terminology.

If you are more familiar with Github or Bitbucket for project management, see [Comparing Gitlab, Github, and Bitbucket terms](https://about.gitlab.com/blog/2017/09/11/comparing-confusing-terms-in-github-bitbucket-and-gitlab/) for a mapping of the different terminologies. 

## Gitlab instance organization

### Groups and projects

Work within the program lives in the [`jatic`](https://gitlab.jatic.net/jatic) group. 

Within this group, each team has a corresponding subgroup which houses their projects, wiki, documentation, epics, packages, etc. The members of each team are members of their corresponding subgroup, giving them the appropriate permissions and access to all of the team's projects.

Groups, subgroups, and their projects are set to "internal" visibility by default. This means that they can be discovered and cloned by any signed-in user. We recommend that teams keep visibility to internal whenever possible 

To read more, see [Groups](https://docs.gitlab.com/ee/user/group/) and [Organize work with Projects](https://docs.gitlab.com/ee/user/project/organize_work_with_projects.html) from Gitlab.

### Gitlab runners

The instance has a number of runners assigned to it which can run CI/CD jobs within a pipeline. These can be used to automatically run tests against code before merging, build artifacts, and deploy software. 

New groups and projects are able to leverage the instance-wide runners by default. However, if your project requires particular compute resources, please make a request to program support. 

To read more, see [Gitlab Runner](https://docs.gitlab.com/runner/) from Gitlab.

## Security

### Impact level

!!! warning

    The Gitlab instance is NOT approved for Controlled Unclassified Information (CUI). 
    
Please do not post CUI into Gitlab. All information which is shared on Gitlab must be below CUI level. 

For reference, our work within the program is generally below CUI, with some exceptions. 

### Sharing outside Gitlab

Unless given permission, please do not distribute other team's work from Gitlab beyond U.S. government agencies and their contractors. 

### Public visibility level

It is possible to create groups and projects in Gitlab with the "public" visibility level. This will make them accessible on the internet without logging into Gitlab. Please make sure you are only making projects public when you intend to. 

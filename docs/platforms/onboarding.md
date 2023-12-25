# Platforms Onboarding

## Gitlab

### Creating an account

An account can be created in two different ways.

- Users with a `.mil`, `.gov`, or an FFRDC/UARC-affiliated email can self-register for an account at [https://gitlab.jatic.net](https://gitlab.jatic.net).
- Users without such an email should contact program support to have an account created on their behalf. After the account is created, they will receive an email to confirm their email address and reset their password. 

After successfully logging into your account, you will be required to setup two-factor authentication (2FA). Personal devices are authorized for 2FA use.

### Getting added to groups

The program use Gitlab groups to provide team-based and role-based access contol to different projects and repositories. 

After you have logged in to Gitlab, ensure that your team admin or program support adds you to the correct groups, corresponding to your team and roles. For example, if Alex is onboarding as a scrum master with the IBM team, she will want to be added as a Developer on "TEAM - IBM" at `jatic/ibm` and "JATIC Scrum Masters" at `roles/scrummasters`.

These groups are also used for managing calendar invitations, so that invitations do not need to be updated or forwarded when new team members join. Because Alex was added to the groups "TEAM - IBM" and "JATIC Scrum Masters", she will automatically be sent meetings for their scrum meetings, as well as the scrum of scrums. 

### Getting added to the program org chart

To help others within the program contact you, please add yourself to the [TBD program org chart](../org-chart/) and open a merge request. 

### Setting up a personal access token

Since our Gitlab instance requires 2FA to login, you will need to set up a personal access token to authenticate with Git or the Gitlab API. See [Personal Access Tokens](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html) from Gitlab for more details.

### Further Gitlab info

See the [Gitlab Usage Guide](gitlab.md) for more information.

## Slack

### Getting added to the workspace

A request to the the Slack workspace can be made for yourself or made by a team member on your behalf. If you have already successfully joined Gitlab, you can make a request for yourself.

1. Create an issue ticket within [`jatic/support`](https://gitlab.jatic.net/jatic/support/-/issues/new#) using the "onboarding" template. 
1. Under the "Slack onboarding" section, add your:
    1. First name
    1. Last name
    1. Email
    1. List of the slack channels you need to be added to (keep blank if unsure)
    1. Onboarding date (set today if unsure)
1. You will receive an email asking you to create a [MITRE Partnership Network Account](https://mpn.mitre.org/), which will serve as your single sign-on for Slack.
1. After creating this account, you will be asked invited to the Slack workspace. 

After successfully logging into your account, you will be required to set up 2FA. 

### Further Slack info

See the [Slack Usage Guide](slack.md) for more information.

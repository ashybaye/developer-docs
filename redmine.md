# Redmine

Redmine is our project management tool at [pm.savalabs.com](https://pm.savaslabs.com). It is **the** authoritative location for project information. It is ideal to flow as much client communication through the tool as possible for the purposes of universally-shared documentation outside of personal mailboxes.

This document won't attempt to explain all of Redmine's features — if you haven't already done so, take a pause now and read through the [Redmine User Guide](http://www.redmine.org/projects/redmine/wiki/Guide) which will answer many of your questions.

This document is focused on the Redmine workflow that we use in-house.

## Configuring a project

- In the description field, document where important assets are like important git branches, dev/staging environments, etc
- Link Slack channel for updates to post to. If there is a lot of activity on the project, it's customary to create a `[project]-noise` channel to push to
- Set the Harvest project ID field for time-tracking purposes

## The makings of the _perfect_ task

Those who file detailed and informative issues deserve the greatest praise. A good issue will make life easier for developers, project managers, and clients. But good issues take a bit of work to create. Don't be tempted to simply add an issue title and move along. Take the extra couple of minutes to do the following:

- Be specific and detailed. A good issue is one that another developer can work on and complete without needing to ask the issue submitter any questions.
- Assign an estimate — even if it's a wild guess, it helps provide some context for the next developer who will look at the issue
- Assign a person
- Assign a due date and optionally a start date
- If applicable:
  - Include screenshots
  - Add a parent, sub, or related task (see [Linking issues](#linking-issues))
  - Set the milestone / target version (see [Target versions](#target-versions))

Note that in almost all cases, clients are members of the project and can view and participate in discussion on issues. Even if the client isn't in Redmine, assume that everything you are writing might one day be seen by the client.

## Linking issues

Redmine has helpful features for linking tasks. This is useful to developers and project managers in helping them understand how different issues are interrelated. You can specify helpful markers like `related to, blocks, blocked by, duplicates, duplicated by`.

## Target versions

The `Roadmap` tab on the project page provides an interface to assign issues to a given "target version". The target version concept in Redmine is flexible: you can use it to plan for alpha/beta/final releases of a project, or to organize tasks into two week sprints.

## Project documentation

We primarily use the wiki in each project for documentation, usually with sections for:

- Meeting notes
- Developer notes
- Environments
- Credentials

Add things like RFPs, proposals, mockups, and any other files to the `Documents` tab.

## Keeping Redmine issues up to date with pull requests

After submitting a [pull request](/git.html#creating-a-good-pull-request), make sure to update the Redmine issue with a link to your pull request, and to set the issue assignee to the reviewer of your pull request.

In general, we prefer to do code review, including commentary on the pull request, in GitHub and not in Redmine.

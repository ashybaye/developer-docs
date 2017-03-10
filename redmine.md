# Redmine

[Redmine](http://www.redmine.org) is our project management tool at [pm.savalabs.com](https://pm.savaslabs.com). It is **the** authoritative location for project information. It is ideal to flow as much client communication through the tool as possible for the purposes of universally-shared documentation outside of personal mailboxes.

This document won't attempt to explain all of Redmine's features — if you haven't already done so, take a pause now and read through the [Redmine User Guide](http://www.redmine.org/projects/redmine/wiki/Guide) which will answer many of your questions.

This document is focused on the Redmine workflow that we use in-house.

## Configuring a project

### Project organization

All projects should be organized with a project/sub-project hierarchy. For example:

> Savas Labs (client/parent project)
> - Savas Labs Maintenance (sub-project)
> - Savas Labs Phase 1 (sub-project)
> - Savas Labs Phase 2 (sub-project)

The top level project should be the client name, and _not_ have an issue tracker. Example: `https://pm.savaslabs.com/projects/client`

Each sub-project should map to a specific scope of work with its own Harvest Project ID. For example, under the same top level client project, a "Phase 1" Redmine sub-project will be linked to it's specific "Phase 1" Harvest ID, while a "Maintenance" sub-project will be linked to a separate "Maintenance" Harvest ID.

Target Versions should be configured to be shared across sub-projects. This way software releases (e.g. 1.0.0) can track issues that are filed in "Maintenance" or "Phase 1."

The top level project should have a Wiki that contains all the information for the project and it's sub-projects. It's not easy to move a Wiki across projects, so existing projects that become sub-projects can retain their wiki pages. But as of Feb 2017, all new sub-projects should _not_ have the Wiki module enabled, and all Wiki content should live in the Top Level Project.

### Set up tasks

- In the description field, document where important assets are like important git branches, dev/staging environments, etc
- Link Slack channel for updates to post to. If there is a lot of activity on the project, it's customary to create a `[project]-noise` channel to push to
- Set the Harvest project ID field for time-tracking purposes. You can configure multiple Harvest project IDs. Once a project ID has been set and time has been tracked to a project, please don't remove the project ID reference - just add a new project ID to the list.

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

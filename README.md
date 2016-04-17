# 0-Tech Kanban

## Description

The aim of this project is to show a minimalistic approach to making a kanban board available through conventions in the branching model within Git - and by doing so, get rid of the burden of needing any vendor-lockin to either Jira or Github.

## Prerequisites

 - bash
 - git
 - javascript (understanding of it for the GUI)

## Conventions

This example set of conventions define how work items are stored. A config file at the root of the repository will map what the names of the columns are and which higher order branch merging they belong to.

### Kanban Columns

The columns you are used to seeing in something like Jira's kanban board will be marked by reserved branches in your  repository. You can choose how many your team needs - some environments need staging while others go right into production.

Depending on which branch a feature was merged to, it will show up on a specific column. For example, if a feature has been merged to the Test branch, the kanban board will show that feature in the "to be tested" column instead of "in development" column.

#### Feature Branch

This is a branch where work can begin start with a specification - something to use to determine whether the work is finished or not. All feature branches that are not merged to development yet are considered to make up the backlog.

Typically a feature will be have a convention of `feature-allow-user-to-log-in` whereas a bug fix will have a `fix-deactivated-users-can-still-log-in`.

#### Dev/Integration Branch

This branch can be thought of as the continuous integration branch where uncompleted work is continually merged together to ensure that any unfinished work is not at odds with other unfinished work.

#### Test Branch

This branch may be created if you still need a separate QA set of tasks to be done on top of the work.

#### Staging Branch

Once the task/feature is finished and tested, your process may require a deploy to a staging server. If this is true, merging the feature branch into this branch can kick off some automation to deploy the solution to staging servers.

#### Master Branch

The default branch in Git is reserved for mirroring what's on production currently. If the feature is ready, it is merged to master and either manually or automatically deployed to production servers.

### Mechanics

The kanban board is a simple html page that shows how far certain features are along to being completed. This is done by running `git branch --merged` on the higher order branches and filtering out predecessor occurances (ie, no need to show the feature in dev if it is already in test as the above command will still show it as having been merged to dev)

In order for the automation of dragging a feature from one column to the next, it is required that the feature can merge smoothly into another branch. This requires some preperation when a feature required merge conflict resolution.

In order to ensure the same conflict does not get in the way of moving the feature into subsequent columns, we enable the rerere feature of git. The problem with enabling that is that it only helps locally. We need to enable rerere sharing by scripting the syncronization of the `.git/rr-cache` folder via `.gitattributes`.

TODO: fill in the script example and git attributes contents

### Contributing

#### See What's in the Backlog

Contributing to this project is done the same way as the goal of the project. No github issues are made and any outstanding work is backlogged in feature branches that contain the requirements in `specs/feature-drag-and-drop-makes-a-merge` for example.

#### No Other Dependencies

This project is about showing what is possible within reason when working with no help from any frameworks, libraries or tools. The bash http server is an example of what the limit is for the kind of 3rd party code that is permitted.

#### No Special Skill Required

Nearly all pull requests will be accepted. If there are issues with the code, they will be fixed shortly after by others. If you are not sure or don't want to intrude, a pull request can be made to the integration branch instead of master where some discussion can happen before trying in master.

The goal is to make the community feel included as soon as possible. Please see Pieter Hintjens' thoughts towards accepting pull requests immediately.

### Future Goals

#### 0-Tech Code Reviews

TODO: elaborate

#### 0-Tech Notifications

TODO: elaborate
# 0-Tech Kanban

## Description

The aim of this project is to show a minimalistic approach to making a kanban board available through conventions in the branching model within Git.

## Prerequisites

 - bash
 - git
 - javascript (understanding of it for the GUI)

## Conventions

This example set of conventions define how work items are stored.

### Kanban Columns

The columns you are used to seeing in something like Jira's kanban board will be marked by reserved branches in your  repository. You can choose how many your team needs - some environments need staging while others go right into production.

#### Feature Branch

This is a branch where work can begin start with a specification - something to use to determine whether the work is finished or not. All feature branches that are not merged to development yet are considered to make up the backlog.

#### Dev/Integration Branch

This branch can be thought of as the continuous integration branch where uncompleted work is continually merged together to ensure that any unfinished work is not at odds with other unfinished work.

#### Test Branch

This branch may be created if you still need a separate QA set of tasks to be done on top of the work
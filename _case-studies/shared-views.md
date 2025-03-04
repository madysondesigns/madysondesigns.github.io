---
layout: case-studies/page
noindex: true
title: Shared views for practice task collaboration
date: 2019-04-19
featured: true
image: "/assets/images/foo.png"
description: "TL;DR blurb here"
tags: ["foo"]
---

## The Problem

The Flatiron EHR platform includes a feature called Group Inboxes that gives users the ability to work together on a list of similar tasks. In the main EHR, the work is focused around a patient and completing different types of tasks for that patient. Group Inboxes creates a worklist for specific types of work across multiple patients -- such as scheduling appointments.

The initial version of Group Inboxes allowed individual users to filter a list of tasks and save that filtered view to return to later. However, our practices asked us for a way to share saved views across users.

The feedback from our practices mainly centered around two problems with individual-level filters and views:
1. Lack of a centralized view pattern is creating data quality issues in inbox worklists, resulting in missed tasks and errors.
1. Practices want oversight and control over what their users see and have access to to ensure their staff is working on the right things.

## The User

Saved filters were implemented as a time saver for individual users, to reduce the amount of time spent setting filters to view the same set of information. In practice, many users tend to use a similar set of filters. The practice relies on each user to set up their individual filters correctly.

Our hypothesis was that filters can provide more value by standardizing a set of work processes at a practice. If a practice can ensure that all staff are working in a similar manner, work will be more consistent and more collaborative.

Based on these needs, we identified two groups of users:
* Practice manager: A user who manages the staff responsible for inbox tasks.
* Practice staff: A user who is responsible for working through inbox tasks.

## Research

When I joined the team, I started by reviewing the existing research and customer feedback to learn more about these problems. I also conducted additional interviews with practices to ask specific questions about the existing workflow and get feedback on rough prototypes of a potential new workflow.

#### I synthesized all this research into two major needs that this feature needs to address.

**Worklist consistency is the top priority**, as every practice needs to know that users are seeing the correct tasks, that data is consistent among users, and that work isn’t being missed.
* Ensure that staff sharing workload are also sharing the same views
* Enable practices to rotate which staff works on different tasks
* Allow views to be updated universally when criteria have changed
* Enable new staff to be set up to do the correct work efficiently
* Prevent errors that occur because individual views are set up incorrectly

**Oversight is a secondary priority**, as some (but not all) practices want to be able to monitor their staff and ensure that they are working on what they are supposed to.
* Allow practice admins to see what views staff see
* Allow practice admins to set what views staff should be using

There is an additional need to improve usability of views so both admins and staff know what work each view is showing and further segment it.
* Enable all users to see what filter criteria are being applied to a view
* Allow users to modify views on the fly for more granular control (e.g. sorting, filter by date)

Based on these goals, I broke down the feature into prioritized user goals.

* Priority 0: must have for feature to be functional
* Priority 1: nice to have additional functionality
* Priority 2: additional features that may be valuable based on customer feedback

{% include figure.html src="sv-prioritized-goals.png"
    caption="I created tables showing our user goals the entire product team could refer back to as we built out the new feature."
    alt="Screenshot showing a list of prioritized user goals" %}

## Exploration

### How Group Inboxes works

Group Inboxes is a real-time worklist tool that allows practice teams to centrally view, prioritize, act on, and collaborate on outstanding tasks in real time. The purpose is to segment tasks by type of work, as opposed to by patient.

The framework is divided into three panels:

* The leftmost panel shows the inboxes or worklists the user has access to. For example, a user may specialize in appointment scheduling so they have access to the inbox that where the worklist is made up of all orders and procedures that need to be scheduled at a specific time.
* The center panel shows the actual worklist items. This list updates in real time and serves as a queue of tasks the user needs to complete, and can be sorted and filtered to segment and prioritize the tasks. As a scheduling specialist, I might be responsible for scheduling patients at a particular location.
* The rightmost panel shows a detailed view of the selected task. This includes the information and actions needed to complete the task. For the scheduler, this might include the patient's contact information to communicate with them and a link to the scheduling system at the practice.

{% include figure.html src="sv-inboxes-overview.png"
    caption="At a high level, Group inboxes is a real-time collaboration tool that helps practices manage work by type of task rather than by patient. "
    alt="Diagram showing the three panels that make up Group Inboxes" %}

### How saved views currently work

The existing workflow for saved individual views is fairly simple. Every user has the ability to filter the worklist that appears in the middle panel. The filter can be saved, in which case it appears in the left panel under the inbox it corresponds to. Any saved views only apply to the current user. Practices often require users to create a set of views that correspond to the user's task responsibilities, but this is an entirely manual process.

{% include figure.html src="sv-existing-inbox.png"
    caption="The existing filter and view system for Group Inboxes. When filtering, users have the option to save the current criteria as a view. The user's saved views appear in the left panel."
    alt="Screenshot of the existing Group Inboxes filter and view system" %}

{% include figure.html src="sv-wireframes.png"
    caption="A high level overview of steps in the new Shared Views workflow. We used this prototype to get customer feedback and plan for development."
    alt="Screenshot showing all the screens that will make up the new feature" %}

{% include figure.html src="sv-full-workflow.gif"
    caption="This animation shows the new workflow from beginning to end as the user would step through it."
    alt="Animation showing how a user would interact with the new workflow" %}

{% include figure.html src="sv-view-manager.gif"
    caption="Practice admins have access to additional features that allow them to manage which shared views appear for users on an individual and group level."
    alt="Animation showing the oversight features for practice admins" %}

## Validation

## Implementation

{% include figure.html src="sv-deliverables.png"
    caption="I like to provide the development team with annotated screenshots that correspond to the tickets they work from."
    alt="Screenshot showing how I annotate screenshots for the dev team" %}

{% include figure.html src="sv-prototype-nav.png"
    caption="I also create a high-level navigation screen in my prototypes so anyone can see how the interactions correspond to our original user goals"
    alt="Screenshot showing the navigation system for my prototypes" %}

## Iteration

{% include figure.html src="sv-separate-filters.gif"
    caption="Our first incremental improvement was to refine the filter UI so some inputs could be accessed independently from the shared views."
    alt="Screenshot showing how list sorting and date range filtering was separated out" %}

{% include figure.html src="sv-alt-save-ui.png"
    caption="The next improvement was to consolidate the saving inputs into the filter window so users can see everything at once."
    alt="Screenshot showing the improved filtering view that includes view saving inputs" %}

## Takeaways

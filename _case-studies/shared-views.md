---
layout: case-studies/page
noindex: true
title: Shared views for practice task collaboration
date: 2019-04-19
featured: true
image: "/assets/images/foo.png"
description: "My first major project at Flatiron was to improve an existing workflow of viewing and filtering user tasks to give practices a way to improve collaboration and consistency by sharing views across their staff."
tags: ["foo"]
---

## The Problem

The Flatiron Health EHR platform includes a feature called Group Inboxes that gives users the ability to work together on a list of similar tasks. In the main EHR, the work is focused around a patient and completing different types of tasks for that patient. Group Inboxes creates a worklist for specific types of work across multiple patients – such as scheduling appointments.

The initial version of Group Inboxes allowed individual users to filter a list of tasks and save that filtered view to return to later. However, our practices asked us for a way to share saved views across users.

**The feedback from our practices mainly centered around two problems with individual-level filters and views:**
1. Lack of a centralized view pattern is creating data quality issues in inbox worklists, resulting in missed tasks and errors.
1. Practices want oversight and control over what their users see and have access to to ensure their staff is working on the right things.

I joined a team that included a product manager, a tech lead and several engineers, a clinical expert, and a product operations and rollout specialist. My role was to understand the problem and the existing system, facilitate research and decision making, execute all UX/UI/prototype design, and collaborate with the entire team to advocate for a high quality user experience. [**AN: does this belong here? have considered a separate top-level section for this info but it feels thin**]

## The User

Saved filters were implemented as a time saver for individual users, to reduce the amount of time spent setting filters to view the same set of information. In practice, many users tend to use a similar set of filters. The practice relies on each user to set up their individual filters correctly.

Our hypothesis was that filters can provide more value by standardizing a set of work processes at a practice. If a practice can ensure that all staff are working in a similar manner, work will be more consistent and more collaborative.

**Based on these needs, we identified two groups of users:**
* Practice manager: A user who manages the staff responsible for inbox tasks.
* Practice staff: A user who is responsible for working through inbox tasks.


## Research

When I joined the team, I started by reviewing the existing research and customer feedback to learn more about these problems. I also conducted additional interviews with practices to ask specific questions about the existing workflow and get feedback on rough prototypes of a potential new workflow.

#### I synthesized all this research into two major needs that this feature needs to address.

**Worklist consistency is the top priority**, as every practice needs to know that users are seeing the correct tasks, that data is consistent among users, and that work isn’t being missed.
* Ensure that staff sharing workload are also sharing the same views
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

### Shared views as the next iteration

Given what we learned about the pain points in the existing workflow, my hypothesis was that we could build a small feature set that solves for the highest priority needs, and which will give us a baseline for further learning about how teams want to collaborate on these tasks.

#### Workflow 1: Practice admins have the ability to create shared views

The first Shared Views workflow was an extension of the existing saved filter view system, where we gave practice admins to share views with others by adding the following features:

1. Inbox admins can create a saved view and set it to be shared with the practice:
    1. Admin edits filters as needed and clicks 'Save as new view'
    1. Admin enters a name (required) and description (optional) for the view
    1. Admin can choose an one or more individual users who have access to the view
    1. Admin sees a success message and view shows up in left nav under ‘Shared Views’
    1. Admin is navigated to their new shared view
1. Inbox admins can edit views shared with users at the practice:
    1. Admin edits filters/settings as needed and clicks Save
    1. Admin confirms changes and sees a success message
    1. Changes are reflected for anyone who loads that view
1. Inbox admins can delete views shared with users at the practice:
    1. Admin clicks Delete button in edit filters modal
    1. Admin confirms deletion and sees a success message
    1. Admin is navigated back to All Items view
    1. View is no longer available for anyone at the practice

{% include figure.html src="sv-full-workflow.gif"
    caption="This animation shows how a practice admin would create a new shared view from beginning to end."
    alt="Animation showing how a user would interact with the new workflow" %}

#### Workflow 2: Practice admins can control who has access to shared views

The second Shared Views workflow was entirely new and gave practice admins a tool to see all shared views and change who can access them:

1. Inbox admins can manage users’ hide/show settings:
    1. Admin opens shared view manager from left nav icon (gear)
    1. Admin can choose an individual user and view their show/hide settings
    1. Admin can toggle user’s Hide and Show for each shared view
    1. Changes will be reflected in that user’s left nav

{% include figure.html src="sv-view-manager.gif"
    caption="Practice admins have access to additional features that allow them to manage which shared views appear for users on an individual and group level."
    alt="Animation showing the oversight features for practice admins" %}

## Validation

After I created a set of interactive prototypes for these new workflows, I conducted additional customer interviews to understand how well the proposed workflows addressed their needs. I chatted with several of our customers selected to cover a diverse group of practices as well as to continue to engage those practices who asked for this specific feature.

The interviews included some exploratory questions but were mainly designed to demo the proposed new feature, allowing participants to test it out and give us more feedback. With each practice, I gave them some time to explore the prototypes as well as gave them some specific tasks so I could evaluate usability.

What I learned is that these workflows did a good job of addressing all the Priority 0 goals, as well as several in the Priority 1 list. This was a good signal that we were on the right track and could start building them out.

One interesting outcome of these interviews was I learned about a few ways the new feature could solve for pain points I hadn't heard about before:
* Allowing practices to rotate which staff works on different tasks – the shared view manager would allow admins to easily change which views a user worked from over time
* Reducing the time practice admins spend when onboarding new staff members who will use the tool – which could be significant at larger practices that require many ways to segment the workload across their team

{% include figure.html src="sv-wireframes.png"
    caption="A high level overview of steps in the new Shared Views feature. We used this prototype to get customer feedback and plan for development."
    alt="Screenshot showing all the screens that will make up the new feature" %}

## Implementation

Once the interviews were complete, I regrouped with the product manager and tech lead on my team to convert the user goals and prototypes into actionable tickets for the engineering team. My role in this process was to advocate for the user-facing technical work and to flesh out those tickets with all the documentation engineers would need to complete them.

My goal is to give engineers all the links, annotations, and context they will need so the live system matches the functionality I designed as closely as possible. Since translating designs into code is always an imperfect process, I also made myself available for questions, feedback, and pairing as they needed. Our process also included a design review step once tickets were completed where I could do a final check comparing the finished product to the acceptance criteria.

{% include figure.html src="sv-deliverables.png"
    caption="I like to provide the development team with annotated screenshots that correspond to the tickets they work from."
    alt="Screenshot showing how I annotate screenshots for the dev team" %}

{% include figure.html src="sv-prototype-nav.png"
    caption="I also create a high-level navigation screen in my prototypes so anyone can see how the interactions correspond to our original user goals"
    alt="Screenshot showing the navigation system for my prototypes" %}
[**AN: where does this belong? do I need it?**]

## Iteration

During the build process, I continued to work on a couple incremental improvements to address some outstanding, lower-priority goals as well as new feedback from the interviews.

Both these improvements were helpful for existing personal views that aren't shared, so we built and rolled out two changes for all Inbox users, not just practice admins.

#### Iteration 1: Refining the filtering UI

The existing filtering UI was a single contained workflow with a couple of usability flaws for those responsible for working on tasks:
* Users need better visibility into what filters are active
* Some filters should be available independently of shared views

I refined the design so that active filters were more clearly visible at all times so that users could tell at a glance what criteria were being used to filter the list. I also added inputs to sort the list and filter by date on top of the default settings the shared view provided. These gave users the ability to better manage their own individual workload.

{% include figure.html src="sv-separate-filters.gif"
    caption="Our first incremental improvement was to refine the filter UI so some inputs could be accessed independently from the shared views."
    alt="Screenshot showing how list sorting and date range filtering was separated out" %}

#### Iteration 2: Consolidate the filter and save view UI

We initially decided that saving a view should be a separate step after filtering, but that separation introduced a couple of challenges:
* Adding or updating a name and description so users can find the right view
* Sharing a filter with the correct people responsible for a particular segment of work

I combined the save view inputs into the filtering UI with a collapsible panel so that users could see both the filters and the shared view settings at the same time.Being able to see all the information at once was important for practices that need many similar shared views or where the filtering criteria are very complex.

{% include figure.html src="sv-alt-save-ui.png"
    caption="The next improvement was to consolidate the saving inputs into the filter window so users can see everything at once."
    alt="Screenshot showing the improved filtering view that includes view saving inputs" %}

#### Future iterations

Throughout this entire project, we came up with many ideas that could improve the Shared Views feature even more, but weren't feasible within the project scope and timeline the team decided on.

I kept track of all these ideas with the rest of the project documentation so down the road if we want to address new customer feedback by improving this feature, we have some ideas to start from.

**Some ideas I thought were interesting and were worth exploring in the future:**
* The ability to duplicate an existing view with modifications
* The ability to 'fork' views or create a parent/child relationship between views with overlapping criteria
* The ability for individual users to show or hide views they have access to
* The ability for admins to decide what filters can be used when working from a shared view (restricting sorting and date filtering or enabling additional criteria)

## Takeaways

This was my first major project at Flatiron Health and I learned many things about working within a complex existing product. I will admit I was unprepared for the significant amount of risk involved in modifying heavily used workflows, and the amount of time it took to identify and mitigate those risks before moving forward.

#### Patient safety is paramount, and any negative impact to practice users could delay or compromise patient care which was absolutely unacceptable.

The workflows I updated may be mission critical at a practice, so it was also critical for me to understand how those worfklows fit in to our practices' existing process. I spent a lot more time researching and understanding the existing system than I expected, but it was incredibly valuable.

It was also critical for me to have open and transparent communication with our customers and those users who rely on the existing features. Flatiron Health is unique in that each team includes a clinical expert and a product operations and rollout specialist and I relied heavily on them to coordinate the interviews and prototype testing I did.

All of this took extra time and effort but it was absolutely worth it in the long run.


[**AN: feedback I'm interested in**]
* anything superfluous that could be cut
* anything needing more detail, confusing, or missing
* anywhere concrete examples or date would help
* consistency in things like verb tenses, terminology like tool/workflow/feature etc.
* typos, grammar, general style things -- overusing adjectives, too flowery or casual, too techincal, etc.
* formatting, visual emphasis, etc.

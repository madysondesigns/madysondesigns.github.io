---
layout: case-studies/page
noindex: true
title: Shared Views for Task Collaboration
date: 2019-04-19
featured: true
thumbnail: "thumbnail.png"
image-folder: "shared-views/"
description: "My first major project at Flatiron was to improve an existing workflow for viewing and filtering user tasks to give oncology practices a way to improve collaboration and consistency by sharing views across their staff."
tags: ["Product Strategy", "Research", "Prototyping", "Design Systems"]
---

## The Problem

The Flatiron Health electronic health record (EHR) platform includes a feature called Group Inboxes that gives users the ability to work together on a list of similar tasks. In the core EHR, workflows are focused around a patient and completing different types of tasks for that patient. Group Inboxes provides worklists for specific types of work across multiple patients – such as scheduling appointments.

The initial version of Group Inboxes allowed individual users to filter a list of tasks and save that filtered view to return to later. However, our practices asked us for a way to share saved views globally across users.

**The feedback from our practices mainly centered around two problems with individual-level filters and views:**
1. Lack of global, consistent views was creating data quality issues in inbox worklists, resulting in missed tasks and errors.
1. Practices wanted admins to be able to manage what their users could see and access to ensure their staff is working on the right things.

I joined a team that included a product manager, a tech lead and several engineers, a clinical expert, and a product operations and rollout specialist. My role was to understand the problem and the existing system, facilitate research and decision making, execute all UX/UI/prototype design, and collaborate with the entire team to advocate for a high quality user experience at every step in the process.

## The User

Saved filters were originally implemented as a time saver for individual users, to reduce the amount of time spent setting filters to create a desired view of information. We discovered that many users tended to work from a similar set of filters and the practice relied on each user to set up their individual filters correctly.

Our hypothesis was that filters could provide more value by standardizing a set of work processes at a practice. If a practice could ensure that all similar staff are working from a similar view of information, the process would be more consistent and more collaborative.

**Based on these needs, we identified two groups of users:**
* Practice manager: A user who manages the staff responsible for inbox tasks.
* Practice staff: A user who is responsible for working through inbox tasks.


## Research

When I joined the team, I started by reviewing the existing research and customer feedback to learn more about these problems and the users involved. I also conducted additional interviews with practices to ask specific questions about the existing workflow and get feedback on rough prototypes of a potential new workflow.

I synthesized all this research into two major pain points that this feature should address.

#### Worklist consistency was the top priority

Every practice needed to know that users were seeing the correct tasks, that data was consistent among users, and that work wasn’t being missed.
* Ensure that staff sharing workload are also sharing the same views
* Allow views to be updated universally when criteria have changed
* Enable new staff to be set up to do the correct work efficiently
* Prevent errors that occur because individual views are set up incorrectly

#### Oversight was a secondary priority

Many practices wanted to be able to monitor their staff to ensure that they were working on what they were supposed to.
* Allow practice admins to see what views staff see
* Allow practice admins to set what views staff should be using

#### Improved usability would also add value

I didn't consider this an explicit priority, but my hypothesis was that giving users a way to see what work each view included and further segment it would be helpful.
* Enable all users to see what filter criteria are being applied to a view
* Allow users to modify views on the fly for more granular control (e.g. sorting, filter by date)

#### Based on these needs, I broke down the feature into prioritized user goals.

* Priority 0: must-have for feature to be functional
* Priority 1: additional functionality that addresses the pain points
* Priority 2: nice to have features that may be valuable based on customer feedback

{% include figure.html src="prioritized-goals.png"
    caption="I created tables showing our user goals the entire product team could refer back to as we built out the new feature."
    alt="Screenshot showing a list of prioritized user goals" %}

## Exploration

Group Inboxes was a widely used feature when I joined the team, so I needed to work within the framework's existing design language and interaction patterns. I spent some time understanding the tool's existing workflows and how it leveraged our design system before exploring improvements I wanted to make.

### How Group Inboxes works

Group Inboxes is a real-time worklist tool that allows practice teams to globally view, prioritize, and collaborate on outstanding tasks in real time. The purpose is to segment tasks by type of work, as opposed to by patient.

The framework is divided into three panels:
* The leftmost panel shows the inboxes or worklists the user has access to. For example, a user may specialize in appointment scheduling so they have access to a list of all orders and procedures that need to be scheduled at a specific time.
* The center panel shows the actual worklist items. This is a real time queue of tasks that can be sorted and filtered to segment and prioritize the tasks. A scheduler might be responsible for setting appointments at a particular location.
* The rightmost panel shows a detailed view of the selected item. This includes the information and actions needed to complete the task. The scheduler might need the patient's contact information and a link to the practice's scheduling system.

{% include figure.html src="inboxes-overview.png"
    caption="At a high level, Group inboxes is a real-time collaboration tool that helps practices manage work by type of task rather than by patient. "
    alt="Diagram showing the three panels that make up Group Inboxes" %}

### How saved views currently work

The existing workflow for saved individual views was fairly simple. Every user had the ability to filter the worklist appearing in the middle panel. The filter could be saved, in which case it would appear in the left panel under the inbox it corresponds to. Any saved views would only apply to the current user. Practices often required users to create a set of views corresponding to the user's task responsibilities, but this was an entirely manual process.

{% include figure.html src="existing-inbox.png"
    caption="The existing filter and view system for Group Inboxes. When filtering, users have the option to save the current criteria as a view. The user's saved views appear in the left panel."
    alt="Screenshot of the existing Group Inboxes filter and view system" %}

### Shared views as the next iteration

Given what we learned about the pain points in the existing workflow, my hypothesis was that we could build a small feature set that would solve for the highest priority needs, and which will would give us a baseline for further learning about how teams want to collaborate on these tasks.

#### New workflow 1: Practice admins have the ability to create shared views

{% include figure.html src="full-workflow.gif"
    caption="This animation shows how a practice admin would create a new shared view from beginning to end."
    alt="Animation showing how a user would interact with the new workflow" %}

The first Shared Views workflow was an extension of the existing saved filter view system, where we gave practice admins the ability to share views with staff by adding the following features:

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

#### New workflow 2: Practice admins can control who has access to shared views

{% include figure.html src="view-manager.gif"
    caption="Practice admins have access to additional features that allow them to manage which shared views appear for users on an individual and group level."
    alt="Animation showing the oversight features for practice admins" %}

The second Shared Views workflow was entirely new and gave practice admins a tool to see all shared views and change who can access them:

1. Inbox admins can manage users’ hide/show settings:
    1. Admin opens shared view manager from left nav icon (gear)
    1. Admin can choose an individual user and view their show/hide settings
    1. Admin can toggle user’s Hide and Show for each shared view
    1. Changes will be reflected in that user’s left nav

## Validation

After I created a set of interactive prototypes for these new workflows, I conducted additional customer interviews to understand how well the proposed workflows addressed their needs. I chatted with several of our customers selected based on two criteria: customers from a diverse range of practice demographics; and customers who originally provided this feedback and would appreciate ongoing communication.

The interviews included some exploratory questions but were mainly designed to demonstrate the proposed new feature, allowing participants to test it out and give us more feedback. With each practice, I gave them some time to explore the prototypes as well as gave them some specific tasks so I could evaluate usability.

What I learned was that these workflows did a good job of addressing all the Priority 0 goals, as well as several in the Priority 1 list. This was a good signal that we were on the right track and could start building them out.

One interesting outcome of these interviews was that I learned about a few ways the new feature could solve for pain points I hadn't heard about before:
* Allowing practices to rotate which staff works on different tasks – the shared view manager would allow admins to easily change which views a user worked from over time
* Reducing the time practice admins spend when onboarding new staff members who will use the tool – which could be significant at larger practices that require many ways to segment the workload across their team

{% include figure.html src="wireframes.png"
    caption="A high level overview of steps in the new Shared Views feature. We used this prototype to get customer feedback and plan for development."
    alt="Screenshot showing all the screens that will make up the new feature" %}

## Implementation

Once the interviews were complete, I regrouped with the product manager and tech lead on my team to convert the user goals and prototypes into actionable tickets for the engineering team. My role in this process was to advocate for the user-facing technical work and to flesh out those tickets with all the documentation engineers would need for development.

My goal was to give engineers all the links, annotations, and context they would need so the live system would match the functionality I designed as closely as possible. Since translating designs into code is always an imperfect process, I also made myself available for questions, feedback, and pairing as they needed. Our process also included a design review step once tickets were completed where I could do a final check comparing the finished product to the acceptance criteria.

{% include figure.html src="deliverables.png"
    caption="I like to provide the development team with annotated screenshots that correspond to the tickets they work from."
    alt="Screenshot showing how I annotate screenshots for the dev team" %}

## Iteration

During the build process, I continued to work on a couple incremental improvements to address some outstanding, lower-priority goals as well as new feedback from the interviews.

Both these improvements were helpful for existing personal views that aren't shared, so we built and rolled out two changes for all Inbox users, not just practice admins.

#### Iteration 1: Refining the filtering UI

{% include figure.html src="separate-filters.gif"
    caption="Our first incremental improvement was to refine the filter UI so some inputs could be accessed independently from the shared views."
    alt="Screenshot showing how list sorting and date range filtering was separated out" %}

The existing filtering UI was a single, contained workflow with a couple of usability flaws for those responsible for working on tasks:
* Users need better visibility into what filters are active
* Some filters should be available independently of shared views

I refined the design so that active filters were more clearly visible at all times so that users could tell at a glance what criteria were being used to filter the list. I also added inputs to sort the list and filter by date on top of the default settings the shared view provided. These gave users the ability to better manage their own individual workload.

#### Iteration 2: Consolidate the filter and save view UI

{% include figure.html src="alt-save-ui.png"
    caption="The next improvement was to consolidate the saving inputs into the filter window so users can see everything at once."
    alt="Screenshot showing the improved filtering view that includes view saving inputs" %}

We initially decided that saving a view should be a second step after filtering, but that separation introduced a couple of challenges:
* Adding or updating a name and description so users can find the right view
* Sharing a filter with the correct people responsible for a particular segment of work

I combined the save view inputs into the filtering UI with a collapsible panel so that users could see both the filters and the shared view settings at the same time. Being able to see all the information at once was important for practices that need many similar shared views or where the filtering criteria are very complex.

#### Future iterations

Throughout this entire project, we came up with many ideas that could further improve the Shared Views feature, but weren't feasible within the project scope and timeline the team decided on.

I kept track of all these ideas with the rest of the project documentation so down the road if we wanted to address new customer feedback by improving this feature, we would have some ideas to start from.

**Some ideas I thought were interesting and were worth exploring in the future:**
* The ability to duplicate and modify an existing view
* A way to 'fork' views or create a parent/child relationship between views with overlapping criteria
* Enabling individual users to show or hide views they have access to
* Enabling admins to decide what filters can modify a shared view (restricting sorting and date filtering or enabling additional criteria)

## Takeaways

This was my first major project at Flatiron Health and I learned many things about working within a complex existing product. I will admit I was unprepared for the significant amount of risk involved in modifying heavily used workflows, and the amount of time it took to identify and mitigate those risks before moving forward.

#### Patient safety is paramount, and any negative impact to practice users could delay or compromise patient care which was absolutely unacceptable.

The workflows I updated were often mission critical at a practice, so it was also critical for me to understand how those worfklows fit in to our practices' existing process. I spent a lot more time researching and understanding the existing system than I expected, but it was incredibly valuable.

It was also critical for me to have open and transparent communication with our customers and the users who rely on these existing features. Flatiron Health is unique in that each team includes a clinical expert and a product operations and rollout specialist, and I relied heavily on them to coordinate the interviews and prototype testing I did.

All of this took extra effort, but I learned that it's worthwhile to invest that time when working in system that is so complex and deeply embedded in a practice's daily process. This upfront investment to understand a sensitive domain gave me the ability to experiment and iterate without compromising the existing product and user experience.

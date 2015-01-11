# Project Planning #

> The _Project Plan_ is the roadmap for the entire project
> 

## References ##

[Course Textbooks](textbooks.md)

- Chapter references (&sect;) can be matched to the JEPM textbook
- Other material is gathered from various sources

## Learning Outcomes ##

- Chapter &sect;3
- You will learn:
	- Define the basic elements of a Project Plan
	- Identify the major steps of the planning process
	
## Project Planning Basics &sect;3, pg 32 ##

![Project Initiation Step][4steps-pm-plan]

- Keep the plan as simple as possible relative to the size of the project
- Project Plans should cover the following:
	* __Project Summary__: high level summary of project origin and objectives
	* __Work Breakdown Structure (WBS)__: Numbered task list
	* __Resource Assignments__: Who is doing the work
	* __Project Schedule__: Completion dates of tasks and milestones
	* __Project Budget__: How money is allocated to the project
	* __Risk Assessment__: What can go wrong, and how to deal with it
	* __Communications__: How the team is expected to interact
	* __Change Control Process__: How change requests are handled
- Brainstorm with project team to create initial draft plan
- Project Manager refines plan with sponsor and customer
- Approved project plan forms a _baseline_

## Planning Process &sect;3, pg 33 ##

- Project Charter is the principal input to the project planning
- Project Manager should insist on signed charter before planning

Basic project planning is relatively straightforward (but hard work):

1. Break the work into manageable "chunks", forming a _Work Breakdown Structure_ (WBS)
- Identify dependencies between tasks
- Identify the duration of each task
- Assign resources to tasks
- Review, analyze, and refine the plan
- Get it approved

The documentation produced from project planning include:

- A _Project Schedule_ (what needs to be done and when)
- A _Critical Path_  (the critical tasks that can affect the delivery date)
- A _Risk Plan_ (the things that can go wrong and how they will be handled)
- A _Communication Plan_ (how to communicate with stakeholders and when)
- A _Change Control Plan_ (how to handle changes)

> The Project Plan and Project Charter pull together virtually everything that is known about the project
> 

## Time for Planning &sect;3, pg 34 ##

> If you don't spend the time planning you will spend the time reacting to negative consequences that arise from poor planning
> 

How much time should be spent on planning a project?

- Just enough time to get a clear understanding of what's required to complete the project objectives
- __Rule of Thumb__: minimum 5 percent of a project duration should be spent on planning
- Not all planning happens upfront, but rather forms part of the iterative process inherent in projects

## Planning Activities &sect;3, pg 36 ##

> The major steps of project planning are highlighted in Figure 3-1, pg 37
> 

### Review Project Requirements ###

> Don't solve the wrong problem in a perfect way
> 

- Review and analyze the requirements
- Make a plan before jumping into execution
- Validate with the customer
- Ensure you are solving the correct problem!

### Clarify Roles and Responsibilities ###

- Ensure you have the right team to solve the problem
- Balance between whom you want and who is available
- Clarify roles and responsibilities in writing to each member

### Conduct Project Kickoff Meeting ###

- Opportunity for all team members and stakeholders to learn about the project
- Project Manager responsible for calling and running the meeting:
	* Start the meeting on time
	* Achieve objectives by using an agenda (see sample Figure 3-2, pg 41)
	* Describe the project
	* Establish team identity (challenge, teamwork, collaboration)
	* Generate excitement
	* Finish the meeting on time
	* Make notes and distribute to attendees after meeting
- Review checklist in Table 3-1, pg 39

> Give the Project Sponsor opportunity to participate. They can show support for the project and explain how it fits into the overall business strategy of the organization.
> 

### Create WBS ###

> A _Work Breakdown Structure_ (WBS) is a family tree of all the project work...
> 

- Creating a WBS is a major step of detailed project planning
- A WBS is list of tasks that must be performed
- Tasks are numbered to represent an organized tree structure
- Compare graphical WBS Figure 3-3 with Outline WBS Figure 3-4

![Graphical WBS][wbs-fig3-3]

- Good judgement, which comes from experience and training, is the key to good WBS structure
- A WBS structure should include:
	- Reference number for each task (natural number) 
	- WBS hierarchy numbering using dotted notation (1.1, 1.1.1, 1.1.2, etc.)
	- Task names
	- Durations (can use PERT formula to help determine these)
	- Predecessors (use reference number field)
	- Resource assignments
	- Measurable deliverable for each task, where possible
- Organizations will develop WBS templates over time
- Project Managers will look to use templates as a basis for future projects

> __READ MORE__: See [Sample OO Project Plan][ootemplate] used as a basis for planning projects in the BIT Project Course
> 

> __READ MORE__: Microsoft Office Templates
> 
> 	- [Microsoft Word WBS Template][ms-word-wbs]
>	- [Microsoft Project WBS Template][ms-proj-wbs]

### Assigning Resources ###

- Assign resources to tasks on the WBS structure
- Consider and resolve the following issues:
	- Who and what is needed for project success?
	- Who and what is available?
	- How can we make up for resource shortfalls?
	- What consequence will resource slippage have on the schedule?
- Discuss shortfalls with project sponsor to mitigate risks
- Assign resources by name ([Fred Penner][fredpenner]) or by role (Musician) if specific details are not yet known

### Schedule the Work ###

> The only reason for time is so that everything doesn't happen at once.
> 
> 	-- Albert Einstein

- Project Manager must create a _realistic_ schedule, with assistance from the project team
- Tasks performed within reasonable time and in a reasonable sequence
- The Project Schedule is the "guts" of the project plan and is bound by time
- Six fundamental steps to creating a Project Schedule:
	1. Create WBS to the task level
	2. Specify the person who will accomplish each task
	3. Establish dependencies (order) between tasks
	4. Determine completion date for tasks in consultation with responsible team members
	5. Record completion dates on the task list
	6. Create overall Project Schedule showing projected project end date

## Project Management Software &sect;3, pg 43 ##

> Project Management Software requires training and experience to use effectively!
> 

- Can assist in developing and maintaining project plans
- Can automatically organize the WBS structure based on indenting levels
- Can generate network diagrams and calculate critical paths
- Can manage resource assignments, work schedules, and costing
- Can track project progress and compare actuals with estimates
- Can do many, many specialized things...
- Can be relatively expensive and overkill for smaller projects

> __READ MORE__: Some example Project Management Software:
> 
>	- [Microsoft Project][msproject] on Windows
>	- [OmniPlan][omniplan] on Mac
>	- [OpenProj][openproj] a free, open source, platform independent distribution

---

[4steps-pm-plan]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/4steps-pm-plan.png

[wbs-fig3-3]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/WBS-ex.png

[ootemplate]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/documents/OO_Project_Template.xlsx

[ms-word-wbs]: http://office.microsoft.com/en-ca/templates/work-breakdown-structure-TC001141726.aspx

[ms-proj-wbs]: http://office.microsoft.com/en-ca/templates/work-breakdown-structure-TC103360093.aspx

[msproject]: http://products.office.com/en-CA/project/project-professional-2013-desktop-software

[omniplan]: http://www.omnigroup.com/omniplan

[openproj]: http://sourceforge.net/projects/openproj

[fredpenner]: http://www.fredpenner.com

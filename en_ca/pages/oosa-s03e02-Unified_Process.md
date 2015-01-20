# The Unified Process in Detail

## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;2 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;2.10 of the UML 2 course textbook (UMLUP)
- You will learn to:
	- Invoke UP as a SEP
	- Define the driving factors of UP
	- Explain UP as an iterative and incremental approach
	- Identify and explain the workflows of UP
	- Identify and explain the phases of UP
	- Compare and contrast details of UP and RUP

## Instantiating UP? &sect;2.5 ##

> UP (and RUP) must be instantiated for each project
> 

- UP is a generic SEP that has to be instantiated for a project
- It is a framework and not a "one size fits all" solution
- Initiating UP involves defining and incorporating:
	* in-house standards
	* document templates
	* establishing tools - modeling, compilers, configuration and project management
	* databases - bug tracking, project tracking
	* life cycle modifications - change control process, quality control
- RUP needs a similar process, but it provides some of the elements as part of the product

## UP Axioms &sect;2.6 ##

> An [axiom][axiom-wolfram] is something declared true without proof
> 

The Unified Process is:

1. Requirements and Risk driven
2. Architecture-Centric
3. Iterative and Incremental

### Requirements and Risk ###

- __Use Cases__ are the practical means of capturing requirements
- Risk management is an active part of project planning and control
- UP supports actively attacking risks so they don't attack you

### Architecture-Centric ###

- Architecture describes how a system is expressed as components, how they interact, and how they are deployed onto hardware
- Quality system architectures lead to quality systems
- Lack of architecture leads to ad hoc collections of source code that are hacked together
- UP supports developing software based on robust system architecture

### Iterative and Incremental ###

> An iterative an incremental approach is a way of building software by a process of stepwise refinement
> 

- Iterations break a project into a series of "sub-projects" or "mini-projects"
- Increments deliver system functionality in chunks
- Eventually leads to delivering a completely functional system
- An increment might involve several iterations


## UP is Iterative & Incremental &sect;2.7 ##

> To understand UP, you must understand iterations and increments
> 

- Generally, people have an easier time solving smaller problems
- Break a large software development project into a number of smaller "more-solvable" problems
- In other words, treat a large project as a series of "mini-projects"
- Each "mini-project" is an _iteration_
- Each mini-project contains elements of a complete project:
	* planning
	* analysis & design
	* construction
	* integration & testing
	* internal & external release
- Each iteration (or a series of iterations) generates a _baseline_ that is a partially complete version of the final system
- The difference between two consecutive baselines is an _increment_
- Iterations are grouped into _phases_

### UP Iteration Workflows &sect;2.7.1 ###

> Each iteration runs through 5 core workflows that identify what needs to be done and the skills needed to do it
> 

- The five core "engineering" workflows of UP are (__RADIT__):
	1. __Requirements__: capturing what the system should do
	2. __Analysis__: understanding, refining, and structuring the requirements
	3. __Design__: realizing the requirements in system architecture
	4. __Implementation__: building the software
	5. __Test__: verifying that the implementation works to the requirements
- Other workflows can be considered, but are not explicitly addressed by UP
- For example, RUP considers these additional core disciplines (aka workflows):
	* __Business Modeling__: understanding the business strategy, problems, and how the software project can provide improvement
	* __Deployment__: dealing with the delivery of software to end users
- RUP also has three support disciplines:
	* __Configuration and Change Management__: tracking versions and dealing with changes
	* __Project Management__: dealing with project manager related tasks
	* __Environment__: dealing with the supporting resources to execute the project

### UP Baselines and Increments &sect;2.7.2 ###

> Every UP iteration can generate a baseline
> 

- A _baseline_ is an internal (or external) release of reviewed and approved artifacts
- A baseline provides an agreed basis for further review and development
- A baseline should only be changed through the formal change control process
- An increment is the difference between one baseline and the next
- Each increment is a step toward the final, delivered system

## UP Structure &sect;2.8 ##

> UP has four phases where each one ends with a major milestone
> 

The four phases and major milestone of UP are as follows:

Phase | Milestone | Reference
------|-----------|----------
Inception | Life Cycle Objectives | Table 2.1
Elaboration | Life Cycle Architecture | Table 2.2
Construction | Initial Operational Capability | Table 2.3
Transition | Product Release | Table 2.4

- Each phase consists of one or more iterations (depending on the project)
- Each iteration executes the core workflows (see Figure 2.6)
- Supporting workflows also occur per iteration where appropriate

![UP Phases and Iterations][up-phases]

- __Rule of Thumb__: an iteration should last less than 2-3 months
- The amount of work done per workflow varies per iteration
- Understanding the relationship of Phases, Workflows, and effort is key to understanding UP
- Study Figure 2.7 and chart below:

![UP Phases and Iterations Workload][up-chart]

## UP Phases &sect;2.9 ##

> __Inception__ is about initiating the project
> 

### Inception - Goals &sect;2.9.1 ###

- Get the project off the ground
- Establish feasibility - perform prototyping
- Create business case to establish business benefits
- Capture essential requirements
- Identify critical risk and ways to mitigate them

### Inception - Focus &sect;2.9.2 ###

- Primary emphasis on Requirements and Analysis workflows
- Some Design and Implementation might occur if directed at producing a prototype
- Test workflow not generally applicable since prototypes are "shelved"

---

> __Elaboration__ is about creating a partial, but working, version of the system
> 

### Elaboration - Goals &sect;2.9.4 ###

- Create an _executable architectural baseline_ (a "first cut" of the desired system)
- Capture majority of _Use Cases_ (more on this in later weeks)
- Create a detailed plan for construction
- Provide details about risk, quality, resources, and time

### Elaboration - Focus &sect;2.9.5 ###

- All 5 core workflows are invoked:
	* requirements - refine scope and requirements
	* analysis - establish _what_ to build
	* design - create stable architecture
	* implementation - build the architectural baseline
	* test - test the architectural baseline
- The amount of work per workflows varies with the iterations in this phase

---

> __Construction__ evolves the executable architectural baseline into a complete working system
> 

### Construction - Goals &sect;2.9.7 ###

- Complete Requirements, Analysis, and Design workflows
- Implement and Test to evolve the baseline from Elaboration into a completed system
- Maintain the integrity of the system architecture

### Construction - Focus &sect;2.9.8 ###

- Emphasis is on Implementation and Test workflows
- Other workflows are important and should be flushed out to completion
- Workflows are addressed as follows:
	* requirements - uncover any that have been missed
	* analysis - finish up the analysis
	* design - finish up any remaining design
	* implementation - build the Initial Operational Capability (milestone)
	* test - test the Initial Operational Capability

---

> __Transition__ is about deploying the completed system to the user location
> 

### Transition - Goals &sect;2.9.10 ###

- Fix defects from beta-testing
- Rollout software to user locations
- Create user manuals and system documentation
- Train users

### Transition - Focus &sect;2.9.11 ###

- Emphasis again on Implementation and Test workflows, but related to deployment at user locations
- Sufficient Design workflow is needed to correct errors
- Test includes acceptance testing by users at deployment location
- Very little, if any, work happens under Requirements and Analysis

---

[axiom-wolfram]: http://mathworld.wolfram.com/Axiom.html

[up-phases]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/up-linear.png
[up-chart]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/up-chart.png

# Gathering Requirements #

> _Requirements engineering_ describes the activities involved in eliciting, documenting, and maintaining a set of requirements for a system
> 

## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;3 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;3.8 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Define requirements engineering and the workflows involved
	* Define requirement in terms of software development
	* Define functional and non-functional requirements
	* Identify and explain the packages of a requirements meta-mode
	* Explain the importance of requirements engineering
	* List requirements using simple "shall" statement structure
	* List important attributes for requirements
	* Identify requirement priority using MoSCoW technique
	* List and describe the 3 filters used as part of natural language
	* Identify and describe techniques to elicit requirements

## Requirements Workflow  &sect;3.2 ##

- In this workflow, we have to find out what the project is trying to achieve
- Most of this work is done in the Inception and Elaboration phases (see Figure 3.2)

![UP Workflows][up-chart]

- Requirements engineering captures both _functional_ and _non-functional requirements_
- __Functional Requirements__: statements about _what the system will do_
- __Non-Functional Requirements__: statements about the _constraints_ on the system
- OO Analyst/Designer will:
	* discuss both types of requirements with various stakeholders
	* strive to reach agreement about _what the system will do_ and its _constraints_
	* discover and negotiate conflicting requirements from different stakeholders
	* prioritize requirements based on stakeholder needs
	* produce a formal high-level `Requirements specification`

## Requirements Meta-model &sect;3.3 ##

> Figure 3.3 is the meta-model for the requirements engineering approach in the textbook
> 

- Folder-like symbols represent UML packages (they work like folders in a filing system)
- Triangle icon in upper right corner indicate that package contains a model
- Anchor icons (a plus inside a circle) indicates which folder is the container, meaning it contains the other things connected to it

So...

- `Software requirements specification` contains a `Requirements model` and a `Use case model`
- `Requirements model` contains `Functional requirements` and `Non-functional requirements`
- `Use case model` will contain many use case packages

## Requirements Workflow Detail &sect;3.4 ##

- Figure 3.4 shows tasks for UP requirements gathering in terms of developing use cases:

![Requirements as Use Cases][act-req-uc]

- Figure 3.5 show tasks that are part of traditional requirements gathering:

![Requirements Workflow][act-req-flow]

- Picture these figures as activity diagrams with partitions being the worker icons in the figures
- The workflow is a guideline and real projects may deviate or do several tasks in parallel
- In this course, the tasks of interest will include:
    - Finding Actors and Use Cases
    - Prioritizing Use Cases
    - Detailing Use Cases
    - Structuring the Use Case Model
    - Finding Functional Requirements
    - Finding Non-Functional Requirements
    - Prioritizing Requirements
    - Tracing Requirements to Use Cases

## Importance of Requirements &sect;3.5 ##

- Requirements tell what the system must do and under what kinds of constraints
- The leading cause of project failure is missed or incomplete requirements
- The other leading cause of project failure is lack of user involvement

## Defining Requirements &sect;3.6 ##

- A requirement can be defined as a specification that should be implemented
- Two types of requirements:
    1. functional: _what_ the system should do
    2. non-functional: a _constraint_ on the system
- Requirements should NOT indicate HOW the system will do something
- In practice though, requirements are sometimes a mix of _what_ and _how_ since it can be easier to understand something in terms of a concrete implementation rather than an abstract statement

### Requirements Model &sect;3.6.1 ###

> The meta-model of Figure &sect;3.3 contains _both_ a `Requirements model` and a `Use case model`
> 

- Requirements gathering is often an informal approach
- Documents in natural language are produced giving an account of the proposed system
- the key question about ANY requirements documents is: "How useful is it?"
- UP has a formal approach to requirements gathering based on a use case model
- The textbook extends this with a formal requirements model based on the two types of requirements

### Well-formed Requirements &sect;3.6.2 ###

> Using simple "shall" statements to capture requirements
> 

- UML deals with requirements entirely through use cases
- Many analysts/designer believe that use cases are not enough
- Requirements should be clearly and consistently stated (see Figure 3.6)
- Each requirement can be stated with a simple "shall" format

		<id> The <system name> shall <function to be performed>

### Functional and Non-Functional Requirements &sect;3.6.3 ###

- To keep things simple and useful, requirements are identified as functional and non-functional
- Functional requirements state what the system should do:

		1. The ATM shall check the validity of an inserted ATM card
		2. The ATM shall validate the PIN number entered by the customer
		3. The ATM shall dispense no more that the customer's maximum registered amount

- Non-functional requirements are constraints placed on the system:

		1. The ATM shall be written in C#
		2. The ATM shall communicate with the bank central system with 256-bit encryption
		3. The ATM shall validate the PIN in under 3 seconds

### Organizing requirements &sect;3.6.4 ###

- Requirements can be organized into a _taxonomy_ (hierarchy of requirement types)
- The taxonomy categorizes requirements into smaller, more manageable groupings
- The two high-level types are `functional` and `non-functional` (see Figure 3.7)
- Other levels depend on the system you're modeling and the standards of the organizations you're working with
- To be practically useful, the taxonomy should not exceed 2 or 3 levels deep

### Requirement Attributes &sect;3.6.5 ###

> An attribute is a tagged value pair `name=value`
> 

- A requirement should have a number of attributes such as `dueDate`, `priority`, and `source`
- One simple (and useful) scheme for assigning `priority` is __MoSCoW__ (see Table 3.5)

Priority | Purpose
---------|--------
**M**ust have | Mandatory requirements that we must have for system success
**S**hould have | Important requirements that we should attempt to provide
**C**ould have | Requirements that are optional and could provide if possible
**W**ant to have | Requirements that are wanted, but can wait for later releases

- A suggested list of attributes (see Table 3.6 for more details):
	* Due date
	* Priority
	* Status
	* Benefit
	* Effort
	* Risk
	* Stability
	* Target Release

## Finding Requirements &sect;3.7 ##

> Requirements come from the context of the system you are trying to model
> 

- Requirements engineering starts from a vision document
- A vision document describes the essential (measurable) goals of a system from stakeholder perspectives
- The Project Charter can serve as a basis vision document to start gathering requirements in earnest

### Requirements elicitation &sect;3.7.1 ###

> !! The map is NOT the territory !!
> 

- When using natural language, people apply 3 filters to describe what they know
- Identify and challenge filtered statements to extract information

Filter | Purpose
-------|--------
deletion | some information is filtered out
distortion | information is modified through "creation" and "hallucination"
generalization | information is abstracted into rules, beliefs, principles, etc.

- Keywords to watch for that indicate that filtering may be at work:
	* all
	* everyone
	* always
	* never
	* nobody
	* none

### Interviews &sect;3.7.2 ###

> The most direct way of gathering requirements - best done one-on-one
> 

- Don't hallucinate a solution - set your pre-conceptions aside during the interview (hard to do!)
- Ask context-free questions - ones that don't presuppose an answer and will encourage discussion
- Listen - give the interviewee time to talk
- Don't mind-read - a form of hallucinating that we know what someone feels, wants or is thinking
- Listen
- Have patience!
- Listen

- Pen and paper (or tablets) are good, non-distracting ways of recording interviews
- Mind-maps are a graphically rich way of collecting and organizing information
- Typing on a laptop can be distracting and forms a barrier between you and interviewee

> ### READ MORE
> - [Mind Mapping][tonybuzan]
> - [List of Mind Mapping Software][mind-map-sw]
> - [Free Mind Open Source Mind Mapping Software][freemind]
 

### Questionnaires &sect;3.7.3 ###

> They are NOT substitutes for interviews!
> 

- They can be useful supplements to interviews
- You might interview a cross-section of stakeholders and then send questionnaires to validate results

### Requirements Workshop &sect;3.7.4 ###

> A focus on brainstorming and capturing key ideas as requirements
> 

- Can be a very efficient way of capturing requirements
- Key stakeholders are in a room together identifying key requirements
- Participants include:
	* facilitator
	* requirements engineer
	* key stakeholders
	* domain experts
- Capture information using notes, mind-maps, recordings, etc.
- After the meeting:
	* Turn the information into a formal requirements model
	* Circulate the results to participants for comments
	* Refine requirements model based on feedback
- Book additional workshops to be held over time as your understanding deepens

---

[up-chart]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/up-chart.png

[tonybuzan]: http://thinkbuzan.com/
[mind-map-sw]: http://en.wikipedia.org/wiki/List_of_concept-_and_mind-mapping_software
[freemind]: http://freemind.sourceforge.net/

<!--
[System Analyst]-(Find actors and use cases), [System Analyst]-(Structure use case model), [Architect]-(Prioritize use cases), [Specifier]-(Detail use case), [Interface Designer]-(Prototype user interface)
-->

[uc-req-flow]: http://yuml.me/83359ddd

<!--
(start)->(Find actors and use cases)->(Prioritize use cases)->(Detail use case)->|a|, |a|->(Structure use case model)->|b|, |a|->(Prototype user interface)->|b|->(end)
-->

[act-req-uc]: http://yuml.me/885d94eb

<!--
(start)->(Find functional requirements)->(Find non-functional requirements)->(Prioritize requirements)->(Trace requirements to use cases)->(end)
-->

[act-req-flow]: http://yuml.me/356fb2cf

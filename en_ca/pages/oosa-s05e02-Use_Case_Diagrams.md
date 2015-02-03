# Use Case Modeling (Outline)#

> Use Case Modeling is a form of requirements engineering
> 

## References ##

[Course Textbooks](textbooks.md)

- Parts of Chapter &sect;4 & Chapter &sect;5 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Sections &sect;4.8 & &sect;5.8 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Define Use Case modeling in relation to a Use Case model
	* Describe the typical process of Use Case modeling
	* Identify the main components of a Use Case model
	* Describe the activity of finding actors and use cases
	* Define the system boundary (the _subject_)
	* Give examples of what's inside a system and what's outside a system
	* Draw a simple use case diagram and identify its components
	* Define a project glossary and list it's advantages
	* Describe where use case modeling is useful
	* Describe where use case modeling is not useful

## Use Case Modeling &sect;4.2 ##

> Use Case Modeling captures functional requirements
> 

- Chapter &sect;3 discussed "traditional" ways to build the `Requirements model`
- Use Case Modeling is a different and complementary way of eliciting requirements
- Use Case Modeling builds the `Use Case model`

Typical process:

- Identify system boundary
- Find actors
- Find use cases:
	* specify the use case main flow
	* identify alternative flows
- Iterate until use cases, actors, and system boundary are stable.

The result is the `Use case model`, which has 4 components:

Component | Purpose
----------|--------
System boundary | A box drawn around the use cases to denote the edge (or boundary) of the system; called the _subject_ in UML 2.
Actors | The roles played by people or things that interact with the system.
Use cases | Things that actors can do with the system.
Relationships | The various connections between actors and use cases.

- The `Use case model` is a primary input for analysis workflow

## UP Activity: Find Actors and Use Cases &sect;4.3 ##

> Focus on activity _Find Actors and Use Cases_ from Section &sect;3.4
> 

The inputs for this activity (see Figure 4.2):

Input | Purpose
------|--------
Business model | A description of the core aspects of the business. May or may not be available.
Requirements model | Described in Chapter &sect;3.
Feature list | Information description of features, perhaps in the form of a vision document.

The outputs for this activity (see Figure 4.2):

Output | Purpose
-------|--------
Use case model | Basic outlined format of use cases; can include a use case diagram.
Project glossary | The important business language and jargon that is relevant to the project.

### The Subject (System Boundary) &sect;4.3.1 ###

> We have to decide what is part of the system and what isn't
> 

- In UML 2, the system boundary is referred to as the _subject_
- The subject is defined by:
	* __who__ or __what__ interacts with the system (i.e., the actors)
	* what __specific benefits__ the system offers to the actors (i.e. the use cases)
- The subject is drawn as a box, labeled with the system name
- Actors are drawn _outside_ the box boundary
- Use cases are drawn _inside_ the box boundary
- As you identify actors and use cases the subject becomes more precisely defined
- __Note__: Sometimes the subject is not explicitly drawn and is inferred to exist

### Actors &sect;4.3.2 ###

> An actor specifies a specific role taken by an external entity when interacting __directly__ with the system
> 

- An actor is expressed as a _role_
- An actor may be:
	* a person
	* an external system
	* a piece of hardware
	* Time
- A specific person or thing may play many roles as different actors over time
- Actors are __always__ external to the system!
- Actors are usually related to something inside the system (i.e., use cases)
- Actors may have a representation that is internal and necessary for the system:
	* E.g., Library Member is an actor, but a library system also needs an internal representation of Library Members to keep track of their books on loan, fines, etc.
- See Figure 4.3 for ways to represent actors in UML

[gimmick:yuml (type: 'usecase', style: 'scruffy')]([Customer])

[gimmick:yuml (type: 'class', style: 'scruffy')]([&laquo;actor&raquo;;Customer])

- When identifying actors, many questions have to be considered (see Section &sect;4.3.2.1)
- In general, ask: _Who or what uses or interacts with the system?_
- Time is often an actor
	* can trigger interaction with the system
	* useful to trigger functions like an automated backup every evening
	* See Figure 4.4 for a time actor example

[gimmick:yuml (type: 'usecase', style: 'scruffy')]([Time])

[gimmick:yuml (type: 'class', style: 'scruffy')]([&laquo;actor&raquo;;Time])

### Use Cases &sect;4.3.3 ###

> A use case is something an actor wants the system to do
> 

- A use case is a "case of use" of the system by a specific actor
- Use cases:
	* provide _benefit_ to actors
	* are _always_ started by an actor
	* are _always_ written from the perspective of actors
	* are _always_ expressed as a verb phrase (they do some behavior)
- See Figure 4.5 for ways to represent use cases in UML

[gimmick:yuml (type: 'usecase', style: 'scruffy')](`Place Order´,`Get Order Status´)

#### Identifying Use Cases &sect;4.3.3.1

- Start with a list of actors
- Consider how each actor will use the system
- Consider what the system will do for each actor

Some useful questions to ask when identify use cases:

- What functions will a specific actor want from the system?
- Does the system store and retrieve information? If so, which actors trigger this behavior?
- What happens when the system changes state (i.e. system start and stop)? Are any actors notified?
- Does any external event affect the system? What notifies the system about those events?
- Does the system interact with other - external - systems?
- Does the system generate any reports?

#### Use Case Diagrams &sect;4.3.3.2

> A use case diagram is a graphical representation of the subject, the use cases it provides, and the actors that interact with it
> 

- See Figure 4.6 for an example use case diagram
- the subject is a box labeled with its name
- the subject represents the boundary of the system
- the subject is sometimes not drawn and just inferred
- use cases are shown inside the subject box
- actors are shown outside the subject box
- association lines between actors and use cases indicate that they interact in some way

![][uc-example1]

In the above example:

- the subject is inferred
- there are 4 use cases
- there is 1 actor
- the actor interacts with each use case

### Project Glossary &sect;4.3.4

> The project glossary is an important artifact for the project
> 

The project glossary:

- Provides a dictionary of key business terms and definitions
- Should be understandable by everyone in the project, including all stakeholders
- Must resolve: 
	* synonyms - different words that mean the same thing
	* homonyms - same words meaning different things to different people
- Identified preferred terms and meanings from the options
- See Table 4.1 for an example
- A simple spreadsheet or table format can be used as a glossary
- Glossary must be kept consistent with the rest of the model 
- Some modeling tools provide capabilities to maintain project glossaries


### Sections &sect;4.4 - &sect;4.6 ###

> We will address these sections in upcoming weeks
> 

## When to apply Use Case modeling &sect;4.7 ##

- Use cases capture functional requirements
- They are not effective at capturing non-functional requirements
- They are the best choice when the system:
    -  is dominated by functional requirements
    -  has many types of users (there are many actors)
    -  has many external interfaces (there are many actors)
- Use cases would be a poor choice when the system:
    -  is dominated by non-functional requirements
    -  has few users
    -  has few external interfaces

---

<!--
[Customer]-(Place Order), [Customer]-(Cancel Order), [Customer]-(Check Order Status), [Customer]-(Request Catalog)
-->

[uc-example1]: http://yuml.me/1e131d58

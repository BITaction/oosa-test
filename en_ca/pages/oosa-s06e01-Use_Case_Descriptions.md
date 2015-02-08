# Use Case Modeling (Detail) #

## References ##

- [Course Textbooks](textbooks.md)
- Parts of Chapter &sect;4 of the UML 2 course textbook
- Additional references to external reading material as provided
- [Writing Effective Use Cases](http://www.amazon.ca/dp/0201702258)
- [Alistair Cockburn's resource site](http://alistair.cockburn.us/Use+Cases)

## Learning Outcomes ##

- Section &sect;4.8 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Identify and explain the parts of a reasonable use case description template
	* Identify the differences between good and bad use cases
	* Write good use case descriptions
	* Name and describe the two types of actors
	* Identify good and bad steps in a main flow
	* Explain simple and complex deviations from a main flow

## Detailing Use Cases &sect;4.4 ##

> After creating a use case diagram with actors and key use cases, we should detail each use case

The output is a more detailed use case that consists of at least a use case name and a use case specification (description). See summary diagram in Figure 4.7 (p. 78).

## Use Case Specification (Description) &sect;4.5

> There is no UML standard for use case specification. Use a template and keep things simple.
> 

Figure 4.8 details the basic parts of a simple use case specification

Part | Purpose
--------|---------------------
Use case name | Short descriptive name of the use case (matches name in diagram)
Use case identifier | Company standard identifier (pick a standard and stick with it)
Brief description | Brief sentence to describe the main purpose of the use case
Primary actors | The actor(s) that invoke the use case (they want the benefit of the use case)
Secondary actors | The actor(s) that participate in fulfilling the use case (drawn on the right side of a diagram)
Preconditions |The system state before the use case can begin
Main flow | The main steps that occur with the use case when all goes well (the happy path)
Postconditions | The system state after the use case is complete
Alternative flows | The different steps that might occur if certain conditions or events happen during the main flow

Writing a use case:

---

- Use case name: Pay Sales Tax
- ID: 001
- Purpose: Pay Sales Tax to the Tax Authority at the end of a business quarter
- Primary actors: Time
- Secondary actors: Tax Authority
- Preconditions:
	1. It is the end of a business quarter
- Main flow:
	1. The use case starts at the end of each business quarter
	2. The system determines the amount of Sales Tax owed to the Tax Authority
	3. The system prepares and sends a payment to the Tax Authority
- Postconditions:
	1. The Tax Authority receives the correct amount of Sales Tax
- Alternative flows:
	* None

---

### Good and Bad Use Case Specifications ###

> General rules summarized from [Alistair Cockburn's sampler page](http://alistair.cockburn.us/Sampler+of+good+and+bad+use+cases)
> 

Good Use Cases...

- text
- do not describe GUI
- do not describe data formats
- 3 – 9 steps in the main flow
- easy to read
- written at the user’s goal level
- record of decisions made

Bad Use Cases...

- just UML use case diagrams
- describe the GUI
- describe data formats
- multi-page main flow
- complicated to read
- written at the program-feature level
- written as a tutorial on the domain

### Use Case Name &sect;4.5.1 ###

> A unique, short verb phrase identifying the main benefit of the use case
> 

- There is no UML standard for use case name
- In the textbook they consistently write use case names in UpperCamelCase
- In the course we will include spaces between words for readability
- Use cases represent actions and their names should **always** be a _verb phrase_
- Shorter names are better, as long as they are descriptive
- Must be unique so that one use case is not confused with another

### Use Case ID &sect;4.5.2 ###

> A unique immutable identifier
> 

- Use case names may change over time
- Use case identifiers do not change (they are immutable!)
- Simple numbers are often used
- Sometimes letter prefixes representing a system component are used:
	- **IN-17** for use case **17** of the **IN**ventory system component
	- **SO-11** for use case **11** of the **S**ales **O**rder system component

### Brief description &sect;4.5.3 ###

> A short paragraph describing the benefit of the use case
> 

- Single paragraph that summarizes the goal of the use case
- Describe the business benefit it provides to the actor(s)

### Actors &sect; 4.5.4 ###

> Primary actors that trigger the use case and secondary actors that support the use case
> 

Two types of actors as seen from the perspective of the use case:

Type | Purpose
-----|--------
primary actors | they trigger the use case
secondary actors | they interact with the use case once it has been triggered

### Preconditions and Postconditions &sect;4.5.5 ###

> They constrain the system state before and after the use case
> 

1. Pre-conditions are constraints that will prevent the use case from starting
	- What is _true_ before the use case starts
	- They **MUST** all be true before the use case is allowed to start
	- They should (almost always) be verifiable by a program - not in someone's head
2. Post-conditions are constraints on the system state after the use case is complete
	- What is _true_ after the use case completes successfully

Consider:

- Specify as simple boolean statements that evaluate to _true_ or _false_
- They help you design systems that function properly
- If not relevant then write "None"
- Don't leave them blank - that is ambiguous


### Main Flow &sect;4.5.6 ###

> Represents the "perfect world" or "happy path" steps of a use case
> 

- Each use case has one main flow
- The main flow **ALWAYS** starts with a primary actor triggering the use case
- Use cases are written from an actor's perspective
- Main flow is considered the "perfect world" steps where everything goes as expected
- Main flow also known as:
	* Happy path
	* Main success scenario
	* Primary scenario
	* Typical course of events
- Use case specifications can have many diverting flows from the main flow
- Diverting flows capture errors, alternatives, and interrupts to the main flow
- Two ways to model diversions:
	1. Simple - create simple branches in the main flow (see &sect;4.5.6.1)
	2. Complex - write alternative flows (see &sect;4.5.7)
- Steps should be written as simple declarative statements of something doing some action
- Steps should address the _who_, _what_, _when_, and _where_ of the use case

A way to start each use case main flow:

		1. The use case starts when <actor> <function>

- Recall that `Time` can be an actor
- Additional steps of the main flow are a time-ordered sequence
- Format of additional steps can be:

		<number> The <something> <some action>

---

Excerpt of good main flow:

	1. The use case starts when the Customer selects "Place Order"
	2. The system presents a blank order request to the Customer
	3. The Customer provides her name and address on the order request

- Good, well formed statements
- Clear who, what, when, where

---

Excerpt of bad main flow:

	1. The use case starts by clicking "Place Order"
	2. Customer Details are entered

- Expressing GUI by stating _clicking_
- Who does the clicking?
- Who enters the customer details?
- Into what are the customer details entered?
- What specifically are the "customer details"?

---

#### Simple deviation: branching within a flow &sect;4.5.6.1 ####

- UML does not specify and standard for showing branching in a flow
- Some modelers use simple `if <condition>` statements within the main flow
- Some modelers insist that branching is a diversion and must be in the alternative flows
- Adding branches in the main flow means it is no longer strictly "the happy path"
- See Figure 4.9 for an example of branching within the main flow

---

Figure 4.9 excerpt:

	1. The use case starts when the Customer selects an item in the basket
	2. If the Customer select "delete item"
		2.1 The system removes the item from the basket
	3. If the Customer types in a new quantity
		3.1 The system updates the quantity of the item in the basket

---

Compare with using alternative flows:

Main Flow:

	1. The use case starts when the Customer selects an item in the basket
	2. The Customer provides a new quantity for the selected item
	3. The System updates the quantity of the item in the basket
	
Alternative Flows:

	2a. The Customer chooses to "delete item"
		2a.1 The system removes the item from the basket
		This completes the use case
	2b. The Customer provides a quantity of 0 for the selected item
		2b.1 The system removes the item from the basket
		This completes the use case

#### Simple deviations: Keyword IF &sect; 4.5.6.2

Use the keyword IF to indicate a branch in the flow. It has to be associated with a Boolean expression such as 'If the user types in a new quantity', which is either true or false. See sample in Figure 4.9 (p.83).

#### Simple deviations: repetition within a flow &sect; 4.5.6.3

Sometimes we have to document the repetition of an action within a flow of events. It is rare, when when required, we need a strategy to deal with it.

#### Simple deviations: Repetitions 1: Keyword FOR &sect; 4.5.6.4

The keyword For can be used to indicate repetition - see Figure 4.10 (p.84) for an example.

#### Simple deviations: Repetitions 2: Keyword WHILE &sect; 4.5.6.5

The keyword While can be used to document a sequence of events that must be repeated while a Boolean expression is true. See Figure 4.11 (p.85) for an example.

### Alternative flows &sect; 4.5.7

Each use case MUST have a main flow and may have many alternative flows. 

These alternative paths typically capture errors, branches and interrupts to the main flow. See the diagram in Figure 4.12 (p.86).

Alternative flows can be documented separately or be appended to the main flow.

In this course, we will document them separately. See Figures 4.13 and 4.14 (p.87) for an example.

#### Finding alternative flows &sect; 4.5.7.1

While inspecting the main flow, look for:

- possible alternatives to the main flow.
- errors that might be raised in the main flow.
- interrupts that might occur at a particular point in the main flow.
- interrupts that might occur at *any* point in the main flow.

#### How many alternative flows? &sect; 4.5.7.2

Even though there may be *many* alternative flows, they should be limited to the necessary minimum. This can be done through the following 2 strategies:

1. pick the most important alternative flows and document them.
2. Where there are groups of alternative flows that are all very similar, document one of them and add notes describing how the others differ from that one.

## Requirements Tracing &sect;4.6 ##

> Links the `requirements model` to the `use case model`
> 

- `requirements model` and `use case model` are essentially two _databases_ of information
- Requirements tracing relates the two models to one another
- Requirement `<id>` and use case identifiers become important in linking the two models
- Can help identify missed requirements in one model or the other
- The relationship between the models is many-to-many, which can be complicated
	* One use case can cover many requirements
	* One requirement can manifest itself in several use cases
- CASE tools often provide support with _requirements traceability matrix_
- Can be done manually using spreadsheets (see Table 4.2)

| Requirement | UC01 | UC02 | UC03 | UC04 |
|:-----------:|:----:|:----:|:----:|:----:|
| R001 | x |  |  |  |
| R002 |  | x | x |  |
| R003 |  |  | x |  |
| R004 |  |  |  | x |
| R005 |  |  |  |  |

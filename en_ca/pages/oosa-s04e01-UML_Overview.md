# Introduction to UML #

> UML is a general-purpose visual modeling language - it is not a methodology
> 

> UP is a methodology
> 

## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;1 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;1.11 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Identify UML as a language and not a methodology
	* Describe the history of UML
	* Explain the concept of Model Driven Architecture (MDA)
	* Identify how UML supports MDA
	* Define UML structure and basic building blocks
	* Illustrate the hierarchy of UML diagrams and abstract categories
	* Identify and explain the four common mechanisms of UML
	* Illustrate and explain the 4+1 Architecture
	* Identify how UML supports the 4+1 Architecture

## What is UML? &sect;1.2 ##

> UML is an acronym for _Unified Modeling Language_

- A general-purpose visual modeling language for systems
- An open industry standard approved by the [Object Management Group (OMG)][omg]
- Can be used with ALL existing methodologies
- It is very well suited to be used with UP
- 'Unified' because it unifies the previous attempts at visual modeling languages and software engineering processes (SEPs)

## The birth of UML &sect;1.3 ##

- Started in 1994 as an attempt to fix the existing OO methods mess
- Booch and Rumbaugh joined Rational in 1994 to work on UML
- Jacobson came on board with Rational in 1995 (and also worked on UML)
- UML 1.0 was approved in 1997 by OMG
- UML 2.0 was finalized in 2005
- See Figure 1.2 for a visual summary

> __READ MORE__: [The original publication by the inventors][uml-1-book]
> 

> __READ MORE__: [The updated version incorporating UML 2][uml-2-book]
> 

> __READ MORE__: [OMG Formal Versions Of UML&reg;][uml-spec] provides the latest information
> 

Year | Event | Significance
-----|-------|-------------
1994 | Booch | Joins Rational to work on UML
1994 | Rumbaugh | Joins Rational to work on UML
1995 | Jacobson | Joins Rational thru acquisition of Objectory AB
1997 | UML 1.0 | First approved version by OMG
2000 | UML 1.x | Significant improvements to the initial version
2005 | UML 2.0 | Introduced a lot of new visual syntax

## The Future of UML &sect;1.4 ##

- Defined by a recent OMG initiative called [Model Driven Architecture (MDA)][mda]
- Ultimately, MDA sees the model drive the production of - and generate - code directly
- Model transformations guide the process (see Figure 1.3)
	* Computer Independent Model (CIM) transformed to Platform Independent Model (PIM)
	* PIM mapped to Platform Specific Model (PSM)
	* PSM used to generate Code
	* Code deployed to Hardware
- MDA Modeling tools assist with the process

> __READ MORE__: [Eclipse Modeling Framework][emf], an open source MDA
> 

## Why Unified? &sect;1.5 ##

> UML is unified across several domains
> 

Domain | Unification
-------|------------
Development life cycle | Provides visual syntax thru entire life cycle
Application domains | Useful for a large variety of applications
Implementation languages & platforms | Language neural; Platform neutral
Development processes | Supports a variety of SEPs
Its own internal concepts | Consistent and uniform within itself

## Objects and UML &sect;1.6 ##

> UML models a system as a _collection of interacting objects_
> 

Two aspects of UML models:

1. Static Structure
	* defines the types of objects in a system
	* defines how the objects are related
2. Dynamic Behavior
	* describes the life cycles of the objects
	* describes how objects interact to deliver system functionality

## UML Structure &sect;1.7 ##

UML Structure consists of:

1. __Building Blocks__: basic elements (things), relationships, diagrams
2. __Common Mechanisms__: ways of achieving specific goals
3. __Architecture__: UML view of system architecture

## UML Building Blocks &sect;1.8 ##

> UML is composed of three building blocks: Things, Relationships, Diagrams
> 

### Things &sect;1.8.1 ###

> The modeling elements themselves
> 

UML Thing | Example
----------|--------
Structural | class, interface, use case, etc.
Behavioral | interactions, activities, etc.
Grouping | packages
Annotational | notes

### Relationships &sect;1.8.2 ###

> They tie things together
> 

- They show how 2 or more things relate to each other
- They capture meaningful (semantic) connections between things
- See Table 1.1 for relationships between structural and grouping things
- Table 1.1 is important throughout this course and the next one

### Diagrams &sect;1.8.3 ###

> The views into a model that help visualize _what_ the system will do and _how_ it will do it
> 

- 13 different types of diagrams (see Figure 1.6)
- No particular order in which UML diagrams must be created
- Often end up working on several kinds in parallel

For diagram below:

- _White_: with _italics text_ are abstract categories
- __Green__: with __bold text__ are diagrams we study in this course
- Yellow: with plain text are diagrams we study in OO Systems Design course
- Grey: with plain text are diagrams we don't directly study

![UML Diagrams Types][uml-diags]

## Sample Diagrams ##

> Visually presenting a view of some _Things_ and their _Relationships_
> 

### Class Diagrams ###

[gimmick:yuml (type: 'class', style: 'scruffy')]([Student]-[IdCard])

- Students are associated to an IdCard

---

[gimmick:yuml (type: 'class', style: 'scruffy')]([Student]-[IdCard], [IdCard]-[Instructor])

- Instructors are also associated to an IdCard

---

[gimmick:yuml (type: 'class', style: 'scruffy')]([Student]-[StudentCard], [Instructor]-[StaffCard], [IdCard]^-[StudentCard], [IdCard]^-[StaffCard])

- Instructors are associated to a specialized version of IdCard called StaffCard
- Students are associated to a specialized version of IdCard called StudentCard

### Object Diagrams ###

[gimmick:yuml (type: 'class', style: 'scruffy')]([joe:Student]-[123:IdCard], [mary:Student]-[456:IdCard])

- The Student joe (object) is linked to IdCard 123 (object)
- The Student mary (object) is linked to IdCard 456 (object)

### Activity Diagrams ###

![][activity-replaceid]

- Have your IdCard replaced

---

![][activity-addpic]

- If picture missing, take a picture, then replace the IdCard
- If picture on file, then just replace the IdCard

## UML Common Mechanisms &sect;1.9 ##

> Four common mechanisms of UML describe four strategies for approaching object modeling
> 

1. Specifications
2. Adornments
3. Common Divisions
4. Extensibility Mechanisms

### Specifications &sect;1.9.1 ###

> The textual descriptions of the semantics of an element
> 

UML Models can be perceived along two dimensions:

Dimension | Purpose
----------|--------
Graphical | Visualize the model
Textual | Specify the semantics of model elements

- The graphical dimension can visually represent a class
- The textual dimension would capture the _real_ semantics behind the class 
- Without the specifications, you can only guess what the visual element represents
- Diagrams are visual projections of the semantics
- UML modeling tools are used to help maintain the semantic specifications
- Typically start with diagrams and add more specifications with time
- Novices often over-diagram and under-specify

[gimmick:yuml (type: 'class', style: 'scruffy')]([ | | ])

---

[gimmick:yuml (type: 'class', style: 'scruffy')]([Student||])

---

![][class-student]

---

![][class-student-full]

### Adornments &sect;1.9.2
- They are added to make visible aspects of the element's specification - as needed. See fig. 1.11 (p.18).

### Common Divisions &sect;1.9.3

#### Classifier and instance &sect;1.9.3.1
- There are 33 classifiers in UML.
- See Table 1.2 (p.19) for the 7 more common classifiers.

#### Interface and implementation &sect;1.9.3.2
- Need to separate WHAT something does from HOW it actually does it.
- Interfaces specify WHAT must be done.
- Implementation specifies HOW it will be done.

### Extensibility Mechanisms &sect;1.9.4

#### Constraints &sect;1.9.4.1
-  A constraint specifies some condition or rule about the modeling element that MUST be maintained as true.

#### Stereotypes &sect;1.9.4.2
- Represents a variation of an existing element with the same form but a modified intent.
- Can be shown as an icon or as text enclosed in &laquo; &raquo;.

#### Tagged values &sect;1.9.4.3
- Allow to indicate properties of new modeling elements defined by the stereotype.

#### UML Profiles &sect;1.9.4.4
- Profiles are collections of constraints, stereotypes and tagged values. See Table 1.4 (p. 22)

## Architecture &sect;1.10 ##

> Architecture captures the strategic aspects of the high-level structure of a system
> 

- The [4+1 View by Krutchen][krutchen95] captures strategic aspects in four different views, plus one more
- See Figure 1.13 for a representation of the 4+1 views

View | Purpose in a System
-----|--------------------
Logical | Captures the vocabulary of the problem domain as a set of classes and objects
Process | Models the executable threads and processes in classes
Implementation | Models the files and components that make up the physical code base
Deployment | Models the physical deployment of artifacts onto hardware
[+1] Use Case | Captures the requirements as a set of use cases

- UML provides excellent support for creating the 4+1 views
- Creating 4+1 views explores all key aspects of a system architecture
- Used with UP, a 4+1 architecture evolves along with the iterations

> __READ MORE__: [The 4+1 View Model of architecture][krutchen95-pdf]
> 

---

[omg]: http://www.omg.org
[uml-1-book]: http://www.amazon.ca/dp/020130998X
[uml-2-book]: http://www.amazon.ca/dp/0321245628
[uml-spec]: http://www.omg.org/spec/UML/
[mda]: http://www.omg.org/mda
[emf]: http://www.eclipse.org/modeling/emf/

[uml-diags]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/uml-diags.png

[krutchen95]: http://ieeexplore.ieee.org/xpl/articleDetails.jsp?arnumber=469759
[krutchen95-pdf]: https://www.cs.ubc.ca/~gregor/teaching/papers/4+1view-architecture.pdf

<!--
(start)->(Replace IdCard)->(end)
-->
[activity-replaceid]: http://yuml.me/63e10674

<!--
(start)-><a>[picture missing]->(Take Picture)-><b>->(Replace IdCard)->(end), <a>[picture onfile]-><b>
-->
[activity-addpic]: http://yuml.me/56ae0bb7

<!--
[Student|firstName;lastName|FullName()]
-->
[class-student]: http://yuml.me/031d7b92

<!--
[Student|-firstName:string;-lastName:string;-birthDate:date|+FullName():string;+Age():integer]
-->
[class-student-full]: http://yuml.me/1fa662fd

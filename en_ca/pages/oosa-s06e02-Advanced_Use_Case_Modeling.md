# Use Case Modeling (Advanced) #

## References ##

- [Course Textbooks](textbooks.md)
- Parts of Chapter &sect;5 of the UML 2 course textbook
- Additional references to external reading material as provided
- [Writing Effective Use Cases](http://www.amazon.ca/dp/0201702258)
- [Alistair Cockburn's resource site](http://alistair.cockburn.us/Use+Cases)

## Learning Outcomes ##

- Section &sect;5.8 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Explain generalization of actors in a use case diagram
	* Explain generalization of use cases in a use case diagram
	* Draw and interpret generalization in a use case diagrams
	* Explain &laquo;include&raquo; and &laquo;extend&raquo; relationships in a use case diagram
	* Draw and interpret &laquo;include&raquo; and &laquo;extend&raquo; relationships in a use case diagram
	* Write use case descriptions to incorporate &laquo;include&raquo; and &laquo;extend&raquo; relationships
	* List and define general tips for using advanced features of use cases
	* Identify and explain the difficulty with functional decomposition in a use case diagram

## Actor Generalization &sect;5.2 ##

> When two or more actors interact with the same use cases - or with most of them - we can simplify the diagram by using generalization. 

- Use actor generalization if it simplifies the use case model and makes it more understandable
- See Figure 5.2 and simplification in Figure 5.3

![][uc-share]

- There is commonality of actor goals between `Customer` and `Sales Agent`
- Common use cases can be factored out to a more general actor
- A new &laquo;abstract&raquo; `Purchaser` actor can be inserted as in Figure 5.3

![][uc-general1]

- Purchaser is an &laquo;abstract&raquo; actor to hold common functions
- Abstract actors do not trigger use cases
- Purchaser does not trigger the use cases related to it
- Any concrete descendent of Purchaser can trigger use cases related to Purchaser
- Customer and Sales Agent are concrete descendants of Purchaser
- Customer and Sales Agent can trigger use cases related to Purchaser

![][uc-general2]

- The more general actor can be a concrete actor that does trigger use cases
- Customer is a concrete actor
- Customer can trigger the use cases related to it
- Concrete descendants of Customer can trigger the use cases related to Customer
- Sales Agent is a concrete descendent of Customer
- Sales Agent can trigger the use cases related to Customer

## Use Case Generalization &sect;5.3 ##

> Use case generalization is used when one or more use cases are a specialization of a more general use case.

- Use case generalization can be used if it simplifies the use case model
- A descendent (child) use case represents more specific forms of a parent use case
- A child use case automatically inherits *all* features from its parent!
- A child use case may:
	* add new features
	* override (change) inherited features
- See Table 5.1 for restrictions to overriding parent features
- UML does not specify a standard for dealing with generalization in use case descriptions
- Organizations will introduce standards to fit their needs
- Any standard must identify syntax how to handle inheritance
- See Table 5.2 and Figure 5.5 for examples on handling features that are:
	* Inherited without change
	* Inherited and overridden
	* Added as a new feature

## &laquo;include&raquo; Relationship &sect;5.4 ##

> Factors out common steps of one or more use cases into a separate use case that is included
> 

- &laquo;include&raquo; indicates that a **base** use case **MUST always** include the functionality of the **inclusion** use case pointed to by the arrow
- Inclusion use cases can be _incomplete_ or _complete_
- Incomplete inclusion use case:
	* not directly connected to an actor
	* not directly triggered by an actor
	* partial flow of events
	* makes sense only as part of some other base use case
- Complete inclusion use case:
	* directly connected to an actor
	* can be directly triggered by an actor
	* makes sense as a fully functional self-contained use case
	* makes sense as part of some other base use case
- See Figure 5.7 as an example

![][uc-include1]

- Manager can trigger any of the base use cases:
	* `Change Employee Details`
	* `View Employee Details`
	* `Delete Employee Details`
- Each base use case will include the functionality of inclusion use case `Find Employee Details`
- Execution between base and inclusion use cases proceeds as follows:
	* Base use case will execute until the point of inclusion is reached
	* Then execution passes to the included use case
	* Upon completion, execution passes back to the base use case again

> A base use case is **NOT** complete without its inclusion use cases!
> 

- See Figure 5.8 and Figure 5.9 for an example of how to write these into use case specifications
- Note the explicit `include`

---

- Use case: Change Employee Details
- ID: 001
- Purpose: The Manager changes the employee details
- Primary actors: Manager
- Secondary actors: None
- Preconditions:
	1. The Manager is logged onto the system
- Main flow:
	1. The use case starts when the Manager chooses to Change Employee Details
	2. `include(004, Find Employee Details)`
	3. The system displays the employee details
	4. The Manager changes the employee details
	5. The Manager submits the changes
	6. The System makes the changes persistent
- Postconditions:
	1. The employee details have been changed
- Alternative flows:
	* None

---

- Use case: Find Employee Details
- ID: 004
- Purpose: The Manager finds the employee details
- Primary actors: Manager
- Secondary actors: None
- Preconditions:
	1. The Manager is logged onto the system
- Main flow:
	1. The use case starts when a base use case includes this use case
	2. The Manager enters the employee ID
	3. The system finds the employee details
- Postconditions:
	1. The system has found the employee details
- Alternative flows:
	* None

---

> ### In Class Activity
> - The job of a Librarian consists of using an electronic library system to find books, lend out books, return books, and put books on reserve
> - When a book is lent out or put on reserve, the library card must be validated
> - Draw a use case diagram to represent these functional requirements

## &laquo;extend&raquo; Relationship &sect;5.5 ##

> Provides a way to add optional behavior to an existing use case
> 

The &laquo;extend&raquo; relationship implies that:

- the base use case may optionally trigger the extension use case
- the base case does not know *anything* about the extension use cases - it only provides hooks for them
- the base use case is perfectly complete without the extension use cases

See Figure 5.10 for an example

![][uc-extend1]

<!--
place use case descriptions here
-->



### The extension use case &sect;5.5.1

Extension use cases are *generally* not complete use cases, but just consist of one or more behaviour fragments known as *insertion segments*.

Some rules apply:

- the &laquo;extend&raquo; relationship must specify one or more extension points in the base use case.
- The extension use case must have the same number of insertion segments as there are extension points in the &laquo;extend&raquo; relationship.
- It is legal for two extension use cases to &laquo;extend&raquo; the same base use case at the same extension point. If it happens, the order in which the extensions execute is indeterminate.

See Figure 5.12 (p.107) for an example.

### Multiple insertion segments &sect;5.5.2

There can be multiple extension segments in an extension use case.

They require clear labels. See Figure 5.13 (p.108).

### Conditional extensions &sect;5.5.3

Extentions can be subject to a condition such as issuing a warning but not a fine if this is a first offence. See Figures 5.14 & 5.15 (p.109/110).

## When to use Advanced Features &sect;5.6 ##

> Use advanced features when you need to simplify the use case model
> 

Some observations from real projects:

- Generally, stakeholders can easily understand actors and use cases with little education / training
- Stakeholders find generalization on actors more difficult, but they can be explained
- Stakeholders find generalization on use cases very difficult to grasp
- Use case generalization should be avoided - unless abstract use case parents are used
- Heavy use of &laquo;include&raquo; can make use case diagrams difficult to understand (hard to get the whole picture without looking at multiple use cases)
- Stakeholders have great difficulties with &laquo;extend&raquo; - even with careful explanations

## Hints and Tips &sect;5.7 ##

### Keep use cases short and simple &sect;5.7.1 ###

- include only enough detail to capture the requirements
- ensure main flow fits on a single piece of paper (keep under 10 steps)
- Use a short declarative sentence for each step
- Exclude design detail like interface and data formats
- Review and rewrite several times!

### Focus on *what*, not *how* &sect;5.7.2 ###

- Describe *what* the actors want to accomplish, not *how* they will do it
- Keep the details of the design out of the use case
- Including the *how* is like the analyst hallucinating a design solution much too early

Consider the fragment of a use case:

	4 The System asks the Customer to confirm the order
	5 The Customer clicks the OK button

The analyst has imagined some kind of user interface (with an OK button).

A better way to write this use case would be:

	4 The System asks the Customer to confirm the order
	5 The Customer accepts the order

### Avoid Functional Decomposition &sect;5.7.3 ###

- **DO NOT** apply use cases as a way to decompose the system into levels of functionality
- See Figure 5.16
- The following is _functional decomposition_ and it is **BAD** analysis!
- Don't get caught in this trap

![][uc-func-decomp]

> The use of a functional decomposition approach is often an indication that the analyst is trained in more traditional procedural programming techniques and hasn't yet grasped the OO paradigm. In that case, use an experienced analyst to provide guidance and mentorship.

- Note that the whole model is **never** rooted in a single use case!


---

<!-- Showing shared use cases
[Customer]-(List Products)
[Customer]-(Order Products)
[Customer]-(Accept Payment)
[Sales Agent]-(List Products)
[Sales Agent]-(Order Products)
[Sales Agent]-(Accept Payment)
[Sales Agent]-(Calculate Commission)
-->

[uc-share]: http://yuml.me/23dcfc28

<!-- Showing generalization with abstract Purchaser
[Customer]-(List Products)
[Customer]-(Order Products)
[Customer]-(Accept Payment)
[Sales Agent]-(List Products)
[Sales Agent]-(Order Products)
[Sales Agent]-(Accept Payment)
[Sales Agent]-(Calculate Commission)
-->

[uc-general1]: http://yuml.me/4ec9f3c9

<!-- Showing generalization with concrete actors
[Customer]-(List Products)
[Customer]-(Order Products)
[Customer]-(Accept Payment)
[Sales Agent]^[Customer]
[Sales Agent]-(Calculate Commission)
-->

[uc-general2]: http://yuml.me/5d783794

<!-- Showing include
[Manager]-(Change Employee Details)
[Manager]-(View Employee Details)
[Manager]-(Delete Employee Details)
(Change Employee Details)>(Find Employee Details)
(View Employee Details)>(Find Employee Details)
(Delete Employee Details)>(Find Employee Details)
-->

[uc-include1]: http://yuml.me/53e0d000

<!-- Functional decomposition
[Librarian]-(Run Library)
(Run Library)>(Maintain Books)
(Run Library)>(Maintain Fines)
(Run Library)>(Maintain Loans)
(Maintain Books)>(Add Book)
(Maintain Books)>(Remove Book)
(Maintain Fines)>(Add Fine)
(Maintain Fines)>(Remove Fine)
(Maintain Loans)>(Lend Book)
(Maintain Loans)>(Return Book)
-->

[uc-func-decomp]: http://yuml.me/b5f0dea7

<!-- Extend use case example
[Librarian]-(Return Book)
(Return Book)<(Issue Fine)
-->

[uc-extend1]: http://yuml.me/ef04d29c

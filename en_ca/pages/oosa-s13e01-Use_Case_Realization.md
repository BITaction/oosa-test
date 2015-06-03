# Use Case Realization #

## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;12 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;12.12 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Explain use case realizations in the context of analysis models
	* List and describe analysis class diagrams as use case realizations
	* List and describe interaction diagrams as use case realizations
	* Describe lifelines and express them in UML
	* List the describe the various messages that occur in interaction diagrams
	* List and describe the four basic interaction diagrams
	* Draw basic sequence diagrams from use case description main flows

## Analyze a Use Case &sect;12.2 ##

- Analysis classes on their own represent the static structure of a system
- Use case realizations show how instances of analysis classes can dynamically interact
- See Figure 12.2

![][ac-analyze-uc]


## Use Case Realizations &sect;12.3 & &sect;12.4 ##

- Adding associations between analysis classes is a start to use case realization
- Representing messages sent between instances provides more detailed discovery

Goals of use case realization:

- intend to gain a high-level perspective of the dynamic behavior of a system
- discover the classes that collaborate to realize the behavior of a use case
- show how classes collaborate by the messages they send to one another
- discover additional key attributes and operations of analysis classes

Use case realizations implicitly form part of the model by adding other elements as shown in Table 12.1

Element | Purpose
--------|--------
Analysis class diagrams | Show associations between classes, giving a clue on how they will collaborate to realize system behavior
Interaction diagrams | Show interactions between instances of classes, giving a "snapshot" of the running system
Special requirements | New requirements can be discovered and must be documented
Use case refinement | Newly information may require updates to the use cases themselves

- OO modeling is an iterative process
- Developing analysis class diagrams and interaction diagrams leads to discovery of new information (requirements)
- This information is documented and further analyzed leading to updates of the analysis model
- and so on, iteratively, until the analyst is comfortable in the knowledge of "what" the system should do

## Interactions &sect;12.5 ##

- For the purposes of this course, an interaction is a unit of behavior within the context of a use case
- We create one or more interactions to illustrate how instances of analysis classes achieve the functionality of a use case
- Interactions are represented on interaction diagrams
- Developing interactions helps discover more operations (and attributes) of analysis classes
- Two key elements of interactions are _Lifelines_ and _Messages_

## Lifelines &sect;12.6 ##

- A lifeline is a single participant in an interaction
- It can be an instance of a class or a representation of an actor
- It is used to represent how an instance participates in an interaction
- Lifelines have a name and/or classifier type (separated by a colon)
- See Figure 12.5 for examples

## Messages &sect;12.7 ##

- A message is a communication between lifelines
- A message can:
	- call an operation - call messages
	- create new lifelines
	- destroy lifelines
	- other kinds of things
- A call message sent to a lifeline invokes an operation of the classifier of that lifeline
- For example, a call message sent to an object lifeline invokes an operation from the class of that object
- The lifeline executing a message has the _focus of control_ or _activation_
- An _activation_ is an indication that a lifeline has the focus of control
- Messages are drawn as arrows between lifelines (the arrow points to the receiver of the message)

### 7 types of messages - See Table 12.2

Name | Meaning
-----|--------
Synchronous message | Sender waits for receiver to return from executing the message
Asynchronous message | Sender continues executing after sending the message - it does not wait
Return message | The receiver returns focus of control to the sender
Create message | Sender creates a new lifeline as an instance of the classifier specified by the receiver
Destroy message | Sender destroys the receiver lifeline
Found message | Sender of the message is outside the scope of the interaction
Lost message | The message never reaches its destination

### Synchronous and Asynchronous Messages &sect;12.7.1 ###

- In analysis, the distinction between synchronous and asynchronous is too much detail
- Analysis is more concerned with just discovering the messages sent between lifelines
- Most all messages are just shown as synchronous

**NOTE**: Asynchronous messages identify areas of potential concurrent operations executing in a system.

- In design, the distinction between synchronous and asynchronous messages becomes much more important

### Return Messages &sect;12.7.1 ###

- Return messages are usually not shown in analysis-level diagrams
- Focus of control implicitly returns to the sender at the end of an activation
- Add them if they add to the understanding without cluttering up diagrams

### Creation Messages &sect;12.7.2 ###

- A create message creates an instance of the classifier identified by the receiver
- We will use create messages to create instances of objects
- You can send a create message with the stereotype &laquo;create&raquo;
- You can send a create message using a class constructor as the message name
- For example, to create an new account send the create message called `Account()`
- Using the stereotype is more general since not all OO languages might support constructor syntax

### Destruction Messages &sect;12.7.2 ###

- A destroy message makes a lifeline no longer available for subsequent interactions
- You can send a destroy message with the stereotype &laquo;destroy&raquo;
- OO languages can have different approaches to object destruction
- In C++, destruction is explicitly handled by the programmer
- In Java and C#, destruction is handled via automatic garbage collection
- Garbage collection mechanisms offer a `finalize()` operation that is called when the object is actually destroyed
- Programmers can write cleanup code in `finalize()` for each class

### Found and Lost Messages &sect;12.7.3 ###

- We will ignore these within this course
- Generally, they are safely ignored during analysis and become more relevant during design

## Interaction Diagrams &sect;12.8 ##

- Interaction diagrams are used to model interactions between instances of classifiers

### 4 types of Interaction Diagrams

Diagram | Purpose
--------|--------
Sequence diagrams | emphasize time-ordered sequence of messages between lifelines
Communication diagrams | emphasize the structure of collaboration among instances
Interaction overview diagrams | special case of activity diagram where nodes can show other interactions
Timing diagrams | emphasize real-time control aspects of interactions

- We will consider only **Sequence Diagrams** within this course

## Sequence Diagrams &sect;12.9 ##

> Sequence diagrams show interactions between lifelines as a time-ordered sequence of events.
> 

Sequence diagrams:

- have a time dimension that goes from left to right starting at the top and progressing downward
- provide a rich and flexible way to represent interactions
- are most useful when focusing on actual sequencing of events between objects

Refer to Figures 12.8 & 12.10:

- Actors are shown as lifelines at the top
- Instances of classes (objects) are shown as lifelines at the top
- Messages are sent between lifelines
- Call messages pass the focus of control to another activation
- Activations can issue a return message to the original sender
- Call messages can be reflexive by sending from a lifeline to itself (self-message)
- Messages can create new lifelines (within the diagram)
- Messages can destroy lifelines (within the diagram)

> ### In Class Activity
> - Refer to use case Figure 12.6
> - Recreate sequence diagram of Figure 12.8 with the modeling tool
> - Incorporate &laquo;boundary&raquo; class aspects of the use case into the sequence diagram

> ### In Class Activity
> - Refer to use case Figure 12.9
> - Recreate sequence diagram of Figure 12.10 with the modeling tool
> - Incorporate &laquo;boundary&raquo; class aspects of the use case into the sequence diagram


---

[ac-analyze-uc]: http://yuml.me/1b67a50e
<!-- UP Activity: Analyze a Use Case
[Business Model]->(Analyze a use case)
[Requirements Model]->(Analyze a use case)
[Use Case Model]->(Analyze a use case)
[Architecture Description]->(Analyze a use case)
(Analyze a use case)->[Analysis Classes]
(Analyze a use case)->[Use Case Realizations]
-->

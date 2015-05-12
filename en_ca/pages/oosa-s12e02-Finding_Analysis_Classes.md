# Finding Analysis Classes #

## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;8 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;8.6 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Describe the process of noun/verb analysis
	* Apply the process of noun/verb analysis to discover analysis classes
	* Apply the process of noun/verb analysis to discover analysis class attributes and responsibilities 
	* Describe the process of CRC analysis to discover analysis classes, their responsibilities, and collaborations
	* List and define the RUP stereotypes
	* Explain the purpose of the RUP stereotypes in an analysis model
	* Describe the process of finding RUP stereotyped classes
	* Create a first cut analysis model using the techniques in this chapter

## Finding Classes &sect;8.4 ##

> Finding the right analysis classes is a key to OO analysis (and a basis for future design).
> 

- There is no simple algorithm for finding the right analysis classes (see Meyer in *Object Oriented Software Construction*)
- Such an algorithm would give an infallible way to design 00 software
- It's existence is tantamount to finding an infallible way to prove any mathematical theorem
- Instead, there are tried and tested techniques that lead toward a good analysis classes
- They involve analyzing text and interviewing users and domain experts

> Finding the right analysis classes depends greatly on the perspective, skill, and experience of the OO analyst!
> 

### Noun/Verb Analysis &sect;8.4.1 ###

> Noun/Verb Analysis is generally known as Textual Analysis and is supported directly in some modeling tools.
> 

- Noun/verb analysis is a simple way of analyzing text to find classes, attributes, and responsibilities
	* _nouns_ and _noun phrases_ in text indicate classes or attributes of classes
	* _verbs_ and _verb phrases_ indicate responsibilities or operations of a class
- Noun/verb analysis works well as a direct analysis of the language of the problem domain
- Must be aware of synonyms and homonyms as these can give rise to spurious classes &rArr; examine project glossary
- Trickiest aspect of noun/verb analysis is finding any "hidden" classes
- _Hidden classes_ are intrinsic to the problem domain but might never be mentioned explicitly

For example, in a reservation system for a holiday company: 

![][cls-holiday]

- stakeholders talk about customers, reservations, bookings, and so on
- how do we capture that a booking and reservation are more tightly related 
- the single most important abstraction, Order, may never be mentioned explicitly by stakeholders
- it may not even exist in current business system
- if you have trouble with an analysis model, go on a search for hidden classes
- this results in asking some penetrating questions and improves understanding of the problem domain

![][cls-holiday-order]

#### Noun/Verb Analysis Procedure &sect;8.4.1.1

1. Collect input sources of information:
	- Business model
	- the requirements model
	- the use case model
	- the project glossary
	- anything else (architecture, vision documents, etc.)
2. Analyze text by highlighting (or recording in some other way) the following:
	- nouns - for example, flight, student, course, product, order, etc.
	- noun phrases - for example, flight number, student identifier, produce code, etc.
	- verbs - for example, allocate, add, insert, delete, checkout
	- verb phrases - for example, verify credit card, calculate order total
3. Organize results into a table of candidates:
	- Nouns and noun phrases may indicate classes or class attributes
	- Verbs and verb phrases may indicate responsibilities of classes

Term | Candidate | Classifier | Keep/Discard | Reason
-----|-----------|------------|--------------|-------
flight | class | Flight | Keep | possible analysis class
flight number | attribute | Flight | Keep | possible attribute
system | class | none | Discard | too general to be useful
check status | responsibility | Flight | Keep | possible operation to gain status of a flight
flight info | attribute | Flight | Discard | too general and likely a summary of data returned by check status
allocate | responsibility | Flight | Keep | possible operation to allocate a flight to a leg of a trip

- New terms discovered should be clarified with domain expert and added project glossary
- Use project glossary to resolve any synonyms and homonyms
- Create a first cut set of UML analysis classes with attributes and responsibilities 
- You may have gained some idea of relationships between certain classes
- Add these as candidate associations

> ### In Class Activity
> - Read use case provided by Instructor
> - Highlight nouns, noun phrases, verbs, verb phrases
> - Organize results into a table of candidates
> - Submit work as directed by Instructor

### Finding Classes with CRC Analysis &sect; 8.4.2 ###

> In the hands of a skilled facilitator, CRC can be a very good (and fun) way to get user involvement in finding analysis classes.
> 

- CRC stands for Class, Responsibilities, Collaborators
- Uses the world's most powerful analysis tool - the sticky note! (sometimes index cards)

> One company actually marketed sticky notes already sectioned out with class name, responsibilities, and collaborators.
> 

See Figure 8.4

- A note is divided into three compartments
- Top compartment holds the name of the candidate class
- Left compartment holds the responsibilities, which become potential operations in design
- Right compartment holds the collaborators, which are other classes that collaborate with this class
- The collaborators compartment provides a way of recording relationships between classes
- Another way to capture relationships is to stick the notes on a whiteboard and draw lines between collaborating classes

#### Phase 1: Brainstorm &sect;8.4.2.2 ####

Book a meeting with participants that include:

- facilitator
- OO analysts
- stakeholders
- domain experts

The procedure includes steps:

1. Explain that this is a true brainstorm.
	- All ideas are accepted as good ideas
	- Ideas are recorded but not debated
	- Never argue at this stage, just write it down and then move on
	- Everything will be analyzed later
2. Ask the team members to name the "things" that operate in their business domain
	- For example, customer, product, student, course, etc.
	- Write each thing on a sticky note - it is a candidate class, or attribute of a class
	- Stick the note on a wall or whiteboard
3. Ask the team to state responsibilities that those things might have
	- Record these in the responsibilities compartment of the note
	- Limit each class to 3 to 5 responsibilities
4. Identify classes that might work together
	- Rearrange the notes on the whiteboard to reflect the organization
	- Have team members play the role of different classes
	- Get them to discuss their responsibilities and discover ways to collaborate
	- Have everyone be pessimistic to argue away responsibilities
	- Have everyone be optimistic and argue for taking responsibilities
	- Draw lines between classes to represent collaborations
	- Alternatively, record collaborators in the collaborators compartment of the note

#### Phase 2: Analyze &sect;8.4.2.3 ####

Book a meeting with participants that include:

- OO analysts
- domain experts

Analyze the CRC Cards (sticky notes): 

- decide which sticky notes are classes
- decide which sticky notes are attributes of classes
- recall that analysis classes must represent a crisp abstraction within the problem domain
- if a note logically seems to be a part of another note, it may be an attribute instead of a class
- if a note doesn't seem to be particularly important, it may an attribute of another class
- if a note has very little interesting behavior, it may be an attribute on another class
- if in doubt about a note just make it a class
- make a best guess and drive this process to closure; you can always refine the model later
- don't get caught up in *analysis paralysis*

### Finding Classes with RUP Stereotypes &sect;8.4.3 ###

- Determine three distinct kinds of analysis class during analysis activity
- Three distinct stereotypes represent these classes
- The technique is a way of focusing analysis on specific aspects of the system
- The technique complements noun/verb and CRC analysis

See Table 8.1 for stereotypes:

Stereotype | Purpose | Example
-----------|---------|--------
&laquo;boundary&raquo; | mediates interaction between the system and its environment | CourseRegistrationInterface
&laquo;control&raquo; | encapsulates use case specific behavior such as business flow | RegistrationManager
&laquo;entity&raquo; | models persistent information about some business aspect | Student, Course, Registration

#### Finding &laquo;boundary&raquo; classses &sect;8.4.3.1 ####

- they exist on the boundary of your system
- they communicate with external actors
- consider the subject (system boundary) and identify classes that mediate between the subject and its environment

According to RUP, there are three types of &laquo;boundary&raquo; class:

Type | Purpose
-----|--------
user interface class | classes that interface between the system and humans
system interface class | classes that interface with other external systems
device interface classes | classes that interface with external hardware

- Consider actors outside the subject to determine proper boundary types
- A boundary class can service several actors
- When a boundary class services more than one actor, they should generally be of the same type
- Bad design may result if a boundary class services actors of different types!
- Model boundary classes at an analysis level of abstraction


If modeling a GUI boundary:

- just model the top-level window
- leave out all fields, buttons, and fancy widgets that make interfaces exciting to the end user
- sometimes just introduce a dummyUI class that represents the whole user interface for a given use case
- for example, an InventoryUI class can represent a human actor's way of interacting with the inventory

If modeling an external System boundary:

- just model the whole API as a class
- leave out the details about API calls, parameters, protocols, callbacks, etc.
- just introduce a dummyAPI class that represents the interface to the external system
- for example, a PaymentAPI class can represent a way for the system to interact with an external payment system

#### Finding &laquo;control&raquo; classes &sect;8.4.3.2 ####

- These stereotyped classes are controllers
- Their instances coordinate system behavior that corresponds to one or more use cases
- They include business workflow that is independent of a boundary
- Find control classes by considering the behavior of the system as described by the use cases
- Determine how that behavior should be partitioned among analysis classes
- Localize the behavior into suitable controller class (e.g., OrderManager)
- Modelers often indicate control classes by appending a suffix to the class name like "Manager" or "Controller"
- Control classes should arise naturally from the problem domain analysis
- Controllers arising directly from the problem domain tend to cut across several use cases
- For example, a controller such as a RegistrarManager may cut across several use cases in a course registration system
- Similarly, a single use case may require the participation of many control classes
- The analyst must examine and refine control classes into structures that model the problem domain

#### Finding &laquo;entity&raquo; classes &sect;8.4.3.3 ####

- These are classes that represent persistent information about the problem domain:
	- Student, Address, Course
	- Order, Product, ShoppingCart, Invoice
	- SalesQuote, Vehicle, Accessory
- Entity classes express the logical data structure of the system
- If you have a data model, then entity classes are intimately related to entities or tables in this model

Entity class rules of thumb:

- they cut across many use cases
- they are manipulated by control classes
- they provide information to, and can accept messages from, boundary classes
- they represent key business concepts managed by the system (like Customer, Product, Invoice, etc.)
- they are often persistent

<!-- This was skipped as part of first run of OOSA in 2015-Jan term

### Finding classes from other sources &sect;8.4.4 ###

Along with noun/verb analysis, CRC analysis, and RUP stereotypes, it is worth  remembering that there are many other potential sources of classes that should be considered. As you are looking for crisp abstractions that map to real-world things in the problem domain then, obviously, you can look to the real world for classes.

 - Physical objects such as aircraft, people, and hotels may all indicate classes to you.
 - Paperwork is another rich source of classes. Things like invoices, orders, and bankbooks may all indicate possible classes. However, you must be very careful when looking at paperwork. In many companies the paper-work has evolved over the years to support exactly the redundant business processes that the new system might be trying to replace! The last thing you want to do as an OO analyst/designer is to automate obsolete and pathological paper-based systems.
 - Known interfaces to the outside world such as screens, keyboards, peripherals, and other systems can also be a source of candidate classes, especially for embedded systems.
 - Conceptual entities are things that are crucial to the operation of the business but are not manifest as concrete things. An example of this might be a LoyaltyProgram such as a reward card. Clearly, the program itself is not a concrete thing (you can't kick it!), but it is still a cohesive abstraction and so may warrant modeling as a class.

#### Archetype patterns &sect; 8.4.4.1

In our book *Enterprise Patterns and MDA* we describe a set of what we call *archetype patterns*. These are patterns of business concepts that are so pervasive in business systems that we believe that they are truly archetypal in nature. As such, they can be modeled once and then reused, rather than modeled over and over again in each new business system. The idea of the book is that you can use these patterns as-is, or modify them, to construct your analysis model from *model components*. We call this technique *component-based modeling*.

We provide the following archetype patterns:

 - Customer Relationship Management;
 - Inventory;
 - Money;
 - Order;
 - Party;
 - Party relationship;
 - Product;
 - Quantity;
 - Rule.

Each of these patterns is very detailed and inclusive. If you can reuse one of these patterns, you can save yourself many man-days or even man-months of work. Even if the pattern isn't completely appropriate for what you are trying to model, it may give you useful ideas for your own analysis classes rather than starting from a blank page.

This is probably the most efficient way of finding classes for your models &rArr; just take them off the shelf!

-->

## Creating a First-Cut Analysis Model &sect;8.5 ##

To create a first-cut analysis model:

1. Compare all sources of classes (noun/verb analysis, CRC, RUP stereotypes)
2. Consolidate the analysis classes, attributes, and responsibilities and enter them into a modeling tool
3. Use the project glossary to resolve synonyms and homonyms
4. Look for differences in the results
	- differences indicate areas where there is uncertainty
	- resolve these differences now, or highlight for later work
5. Collaborators represent relationships between classes
6. Improve the naming of classes, attributes, and responsibilities
	- follow some standard naming convention
	- standards may be provided by the company
	- you may follow the simple naming conventions described in Chapter &sect;7

The output of this process will be:

- a set of analysis classes
- each class may have some key attributes
- each class should have between three to five responsibilities
- collaborating classes have associations among them

---

[cls-holiday]: http://yuml.me/bd7f2e13
<!--
// Holiday Booking no Order
[Customer]1-*[Booking]
[Customer]1-*[Reservation]
-->

[cls-holiday-order]: http://yuml.me/2a535a41
<!--
// Holiday Booking with Order
[Customer]1-0..*>[Order]
[Order]1-*[Booking]
[Order]1-*[Reservation]
-->
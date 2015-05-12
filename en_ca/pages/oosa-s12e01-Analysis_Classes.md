# Analysis Classes #

> Analysis classes model important concepts of problem domain in the vocabulary of the business stakeholders
> 

## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;8 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;8.6 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Explain the overall process of analyzing a use case, including inputs and outputs
	* Define the anatomy of an analysis class
	* List and explain characteristics of good analysis classes
	* List and explain characteristics of bad analysis classes
	* Explain general rules of thumb for creating well-formed analysis classes

## UP Activity: Analyze Use Case &sect;8.2 ##

- "Analyze a use case" is a process of UP within the Analysis workflow
- The inputs can include:
	* Business Model (you may or may not have this)
	* Requirement Model (discussed in Chapter &sect;3)
	* Use Case Model (discussed in Chapters &sect;4 and &sect;5)
	* Architecture Description (provided by architects with input from analysts)
- The output will generate:
	* Analysis Classes
	* Use Case Realizations

See Figure 8.2

![][ac-analyze-uc]

- This chapter will focus on discovering analysis classes
- Chapter &sect;12 will consider use case realizations

## Analysis Classes &sect;8.3 ##

> They represent important concepts of the problem domain in the vocabulary of the business stakeholders
> 

Analysis classes are classes that:

- represent a crisp abstraction in the problem domain
- should map to real-world business concepts (and be carefully named to match)

The problem domain is:

- the domain in which the need for a software system first arises
- usually a specific area of the business such as online selling or customer relationship management
- sometimes a piece of physical hardware that needs software to operate it

> Ultimately, all commercial software development serves some business need within a problem domain
> 

- An analysis class should map to some real-world business concept:
	* Customer, Product, Order, Account, etc.
	* Student, Instructor, Course, Grade, etc.
	* Shape, Circle, Square, Canvas, etc.
	* User, Tweet, Profile, etc.
- The job of the OO analyst is to clarify confused or inappropriate business concepts
- They must discover something that can form the basis of an analysis class
- If the classes are not right in analysis, then the rest of the SEP workflows will be in jeopardy
- Spend sufficient time in the analysis workflow to ensure that the right set of analysis classes are identified
- Your time will be well spent, as it will most certainly save time later
- This is why 00 analysis can be difficult!

> Finding the right analysis classes is a key factor in good OO analysis (and future design)
> 

- *All* classes in the analysis model must be analysis classes rather than classes arising from design considerations
- When you get to detailed design, analysis classes will be refined into design classes

### Anatomy of Analysis Classes &sect;8.3.1 ###

Analysis class attributes:

- present a very "high level" set of attributes
- include attributes that the resultant design classes will *probably* have
- capture candidate attributes for the design classes

Analysis class operations:

- specify, at a high level, the key services that the class must offer
- will become actual, implementable operations at design level
- will often break down into more than one design-level operations

Analysis class syntax:

- uses a small subset of the class syntax covered so far
- tries to avoid implementation details
- captures the big picture information

Adornment | Add? | Advice
----------|------|-------
Name | mandatory | All classes must have a name.
Attributes | attribute names are mandatory, if given | Only an important subset of candidate attributes may be modeled and attribute types are considered optional.
Operations | operation names and parenthesis are mandatory, if given | Operation parameters and return types are only shown where they are important for understanding.
Visibility | generally not shown | Added if they enhance understanding.
Stereotypes | shown if they enhance the model | Stereotypes to separate problem domain from user interface classes are the first to be identified.
Tagged values | shown if they enhance the model | They offer a flexible way to add specification and understanding where needed, but use sparingly.

See Figure 8.3

![][cls-bank]

> The general idea of an analysis class is that you try to capture the essence of the abstraction and leave the implementation details until you come to design.
> 

### Good Analysis Classes &sect;8.3.2 ###

Characteristics of a good analysis class:

- it is a crisp abstraction that models one specific element of the problem domain
- its name reflects its intent
- it maps on to a clearly identifiable feature of the problem domain
- it has a small, well-defined set of responsibilities
- it has high cohesion
- it has low coupling

#### Abstraction ####

- If you model a customer in a banking system,  you would want to capture the customer's name, address, financial goals, and so on
- You would not capture their preference for window or aisle seats on an aircraft, or their favorite dessert
- Focus on the aspects of real-world things that are important from the perspective of the system you are building

#### Analysis Class Name ####

- You can get a first idea as to whether or not a class is "good" from its name
- For an e-commerce system, Customer would be quite precise in the real world and a good candidate for a class
- ShoppingBasket would also be a good candidate since its semantics are quite clear from the name
- WebSiteVisitor seems to have vague semantics, and in fact sounds like a role that a Customer would play
- You should always be looking for a "crisp abstraction" — something that has clear and obvious semantics

#### Analysis Class Responsibilities (Cohesion) ####

- A responsibility is a contract or obligation that a class has to its clients
- It is a service that a class offers to other classes
- Each responsibility must go hand in hand with the intent of the class
- A ShoppingBasket class would have responsibilities such as:
	- add item to basket
	- remove item from basket
	- show items in basket
	- calculate basket total
	- and so on, responsibilities related to eCommerce shopping basket objects
- Consider the following responsibilities for ShoppingBasket:
	- validate credit card
	- accept payment
	- print receipt
- These responsibilities do not fit well with the intent of shopping baskets
- They are not cohesive and clearly should be assigned elsewhere, perhaps to:
	- a CreditCard class
	- a Checkout class
	- a Receipt class
- It is important to distribute responsibilities over analysis classes to maximize cohesion within each class

#### Analysis Class Relationships (Coupling) ####

- Good classes have a minimum amount of coupling to other classes
- Coupling is measured by the number of other classes with which a given class has relationships
- Coupling is also related to the type of relationship (e.g., Generalization is a stronger coupling than a simple Association)
- An even distribution of responsibilities among classes will tend to reduce coupling
- Localization of control (or too many responsibilities in a single class) tends to increase coupling

### Analysis Class: Rules of Thumb &sect;8.3.3 ###

Rules of thumb for creating well-formed analysis classes:

- About three to five responsibilities per class
	- classes should be kept as simple as possible
	- responsibilities become formal class operations in design
- No class stands alone (coupling is a necessity)
	- classes collaborate with each other (the object instances send messages to one another)
	- associate a class with a small number of other classes with which it collaborates
	- classes may delegate some responsibilities to other 'helper" classes
- Beware of many very small classes
	- can be difficult to get right balance
	- watch for lots and lots of very small classes with just one or two responsibilities each
	- you may consolidate some of the small classes into larger ones
- Beware of few, but very large classes
	- the converse problem of the above
	- few classes, where many of them have a large number (> 5) of responsibilities
	- look at these classes and decompose into two or more smaller classes with fewer responsibilities
- Beware of "functoids"
	- a "functoid" is a normal procedural function disguised as a class
	- functoids are a danger when analysts are accustomed to top-down functional decomposition
	- functional decomposition in use cases could lead to functoids in the classes
	- Grady Booch tells an amusing anecdote of a model of a very simple system that had thousands of classes. On closer inspection, each class had exactly one operation called doIt(). Each class was serving as a "functoid"
- Beware of omnipotent classes - these are classes that seem to do everything
 	- look for classes with "system" or 'controller" in their name
 	- check if the responsibilities of the omnipotent class fall into cohesive subsets
 	- cohesive sets of responsibilities can be factored out into a separate classes
 	- these smaller classes would collaborate to implement the behavior offered by the original omnipotent class
- Avoid deep inheritance trees
	- each level of abstraction in a class hierarchy should have a well-defined purpose
	- it counter-productive to add many levels that don't really serve any useful purpose
	- a common mistake is to use inheritance to implement a functional decomposition where each level has only one responsibility
	- leads to a complex, difficult to understand model
	- inheritance is used where there is a clear inheritance hierarchy arising directly from the problem domain
	- in analysis, "deep" would be three levels of inheritance or more
	- in design, inheritance trees can be much deeper because of frameworks being utilized

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

[cls-bank]: http://yuml.me/fe4e6434
<!--
// Bank Account example from Figure 8.3
[BankAccount|accountNumber;owner;balance|withdraw();calculateInterest();deposit()]
-->
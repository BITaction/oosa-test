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
	* Explain the process of analyzing a use case, including inputs and outputs
	* Define the anatomy of an analysis class
	* List and explain characteristics of good analysis classes
	* List and explain characteristics of bad analysis classes
	* Describe and use the process of noun/verb analysis to discover analysis classes
	* Describe the process of CRC analysis to discover analysis classes
	* List and define the RUP stereotypes
	* Explain the purpose of the RUP stereotypes in an analysis model
	* Create a first cut analysis model using the techniques in this chapter

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

We can summarize what makes a good analysis class in the following points:

- its name reflects its intent;
- it is a crisp abstraction that models one specific element of the problem domain;
- it maps on to a clearly identifiable feature of the problem domain; • it has a small, well-defined set of responsibilities;
- it has high cohesion;
- it has low coupling.


In analysis you are trying to model one aspect of the problem domain accurately and concisely from the perspective of the system you are trying to construct. For example, if you are modeling a customer in a banking system,  you would want to capture the customer's name, address, and so on, but you would be unlikely to be interested in his preference for window or aisle seats on an aircraft. You need to focus on the aspects of real-world things that are important from the perspective of the system you are building.

You can often get a first idea as to whether or not a class is a "good" class simply from its name. If you consider an e-commerce system, Customer would seem to refer to something quite precise in the real world and would be a good candidate for a class. ShoppingBasket would also seem to be a good abstraction - we know, almost intuitively, what its semantics will be. However, something like WebSiteVisitor seems to have rather vague semantics, and in fact really sounds like a role that a Customer plays in relation to the e-commerce system. You should always be looking for a "crisp abstraction"— something that has clear and obvious semantics.

A responsibility is a contract or obligation that a class has to its clients.

Essentially, a responsibility is a service that a class offers to other classes. It is crucial that your analysis classes have a cohesive set of responsibilities that directly accord with the intent of the class (as expressed by its name) and with the real-world "thing" that the class is modeling. Going back to the ShoppingBasket example, you would expect this class to have responsibilities such as 
 - add item to basket;
 - remove item from basket;
 - show items in basket.

This is a cohesive set of responsibilities, all about maintaining a collection of items that the customer has chosen. It is cohesive because all the responsibilities are working toward the same goal—maintaining the customer's shopping basket. In fact, we could summarize these three responsibilities as a very high-level responsibility called "maintain basket".
Now, you could also add the following responsibilities to the ShoppingBasket:


 - validate credit card;
 - accept payment;
 - print receipt.

But these responsibilities do not seem to fit with the intent or intuitive semantics of shopping baskets. They are not cohesive and clearly should be assigned elsewhere—perhaps to a CreditCardCompany class, a Checkout class, and a ReceiptPrinter class. It is important to distribute responsibilities appropriately over analysis classes to maximize cohesion within each class. 

Finally, good classes have the minimum amount of coupling to other classes. We measure coupling between classes by the number of other classes with which a given class has relationships. An even distribution of responsibilities between classes will tend to result in low coupling. Localization of control or of many responsibilities in a single class tends to increase coupling to that class. We consider ways of maximizing cohesion and minimizing coupling in Chapter 15.


### Analysis Class: Rules of Thumb &sect;8.3.3 ###

Here are some rules of thumb for creating well-formed analysis classes.

 - About three to five responsibilities per class - typically, classes should be kept as simple as possible, and this usually limits the number of responsibilities that they can support to between three and five. Our previous example of a ShoppingBasket is a good example of a focused class with a small and manageable number of responsibilities.
 - No class stands alone - the essence of good OO analysis and design is that classes collaborate with each other to deliver benefit to users. As such, each class should be associated with a small number of other classes with which it collaborates to deliver the desired benefit. Classes may delegate some of their responsibilities to other 'helper" classes that are dedicated to that specific function.
 - Beware of many very small classes - it can sometimes be hard to get the balance right. If the model seems to have lots and lots of very small classes with just one or two responsibilities each, then you should look at this very carefully with a view to consolidating some of the small classes into larger ones.
 - Beware of few but very large classes - the converse of the above is a model that has few classes, where many of them have a large number (> 5) of responsibilities. The strategy here is to look at these classes in turn and see if each can be decomposed into two or more smaller classes with the right number of responsibilities.
 - Beware of "functoids" - a functoid is really a normal procedural function disguised as a class. Grady Booch tells the amusing anecdote of a model of a very simple system that had thousands of classes. On closer inspection, each class had exactly one operation called doltO. Functoids are always a danger when analysts accustomed to the technique of top-down functional decomposition approach OO analysis and design for the first time.
 - Beware of omnipotent classes - these are classes that seem to do every¬thing. Look for classes with "system" or 'controller" in their name! The strategy for dealing with this problem is to see if the responsibilities of the omnipotent class fall into cohesive subsets. If so, perhaps each of these cohesive sets of responsibilities can be factored out into a separate class. These smaller classes would then collaborate to implement the behavior offered by the original omnipotent class.
 - Avoid deep inheritance trees - the essence of designing a good inheritance hierarchy is that each level of abstraction in the hierarchy should have a well- defined purpose. It is easy to add many levels that don't really serve any useful purpose. In fact, a common mistake is to use inheritance to implement a kind of functional decomposition where each level of abstraction has only one responsibility. This is, in every respect, pointless and just leads to a complex, difficult to understand model. In analysis, inheritance is only used where there is a clear, and obvious, inheritance hierarchy arising directly from the problem domain.


In the last bullet, we need to clarify what we mean by a "deep" inheritance tree. In analysis, where the classes represent business things, "deep" would be three levels of inheritance or more. This is because business things tend to form inheritance hierarchies that are broad rather than deep.
In design, where the tree consists of classes from the solution domain, the definition of "deep" depends on the implementation language you are targeting. In Java, C++, C#, Python, and Visual Basic, we still consider three or more levels to be deep. In Smalltalk, however, inheritance trees can go much deeper than this, due to the structure of the Smalltalk system.


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
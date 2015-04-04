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


## Finding Classes &sect; 8.4 ##

> Finding the right analysis classes is a key to OO analysis (and a basis for future design)
> 


In the rest of this chapter we consider the core issue of OO analysis and design, finding the analysis classes.

As Meyer points out in *Object Oriented Software Construction*, there is no simple algorithm for finding the right analysis classes. If such an algorithm did exist, then it would amount to an infallible way to design 00 software and this is just as unlikely as finding an infallible way to prove mathematical theorems.

Still, there are tried and tested techniques that lead toward a good answer, and we present them here. They involve analyzing text and interviewing users and domain experts. But ultimately, despite all the techniques, finding the "right" classes depends on the perspective, skill, and experience of the individual analyst.

### Finding classes by using noun/verb analysis &sect; 8.4.1


Noun/verb analysis is a very simple way of analyzing text to try to find classes, attributes, and responsibilities. In essence, nouns and noun phrases in the text indicate classes or attributes of classes, and verbs and verb phrases indicate responsibilities or operations of a class. Noun/verb analysis has been used for many years and works well as it is based on a direct analysis of the language of the problem domain. However, you have to be very aware of synonyms and homonyms as these can give rise to spurious classes.

You also have to be very careful if the problem domain is poorly understood and defined. In this case, try to collect as much information about the domain from as many people as possible. Look for similar problem domains outside your organization.

Perhaps the trickiest aspect of noun/verb analysis is finding the "hidden" classes. These are classes that are intrinsic to the problem domain but that might never be mentioned explicitly. For example, in a reservation system for a holiday company, you will hear the stakeholders talk about reservations, bookings, and so on, but the single most important abstraction, Order, may never be mentioned explicitly if it does not exist in current business systems. You generally know when you have found a hidden class because the whole model seems to gel suddenly with the introduction of this single, new abstraction. This happens surprisingly often — in fact, if we're ever having trouble with an analysis model and it just doesn't seem to be making sense, we go on a search for hidden classes. If nothing else, this makes us ask some penetrating questions and improves our understanding of the problem domain.

#### Noun/verb analysis procedure &sect; 8.4.1.1

The first step in noun/verb analysis is to collect as much relevant information as possible. Suitable sources of information are 

 - the requirements model;
 - the use case model;
 - the project glossary;
 - anything else (architecture, vision documents, etc.).


After collecting the documentation, analyze it in a very simple way by highlighting (or recording in some other way) the following:

 - nouns - for example, flight;
 - noun phrases - for example, flight number; • verbs - for example, allocate;
 - verb phrases - for example, verify credit card.

Nouns and noun phrases may indicate classes or class attributes. Verbs and verb phrases may indicate responsibilities of classes.

If you come across any terms that you don't understand during this process, seek immediate clarification from a domain expert and add the term to the project glossary. Take the list of nouns, noun phrases, verbs, and verb phrases and use the project glossary to resolve any synonyms and homonyms. This creates a list of candidate classes, attributes, and responsibilities.

Once you have this list of candidate classes, attributes, and responsibilities, you make a tentative allocation of the attributes and responsibilities to the classes. You can do this by entering the classes into a modeling tool and adding the responsibilities as operations to the classes. If you have found any candidate attributes, then you can tentatively assign these to classes as well. You might also have gained some idea of relationships between certain classes (the use cases are a good source of these), so you can add some candidate associations. This gives you a first-cut class model that you can refine by further analysis.

### Finding classes by using CRC analysis &sect; 8.4.2 

A very good (and fun) way to get user involvement in finding classes is to use CRC analysis—CRC stands for class, responsibilities, and collaborators. This technique uses the world's most powerful analysis tool, the sticky note! So popular is the CRC method that there is a (possibly apocryphal) story that at one point a company actually marketed sticky notes already marked out with class name, responsibilities, and collaborators.
You begin by marking up some sticky notes as shown in Figure 8.4 (p.165). The note is divided into three compartments. In the top compartment you record the name of the candidate class; in the left compartment, the responsibilities; and in the right, the collaborators. Collaborators are other classes that may collaborate with this class to realize a piece of system functionality. The collaborators compartment provides a way of recording relationships between classes. Another way to capture relationships (which we prefer) is to stick the notes on a whiteboard and draw lines between the collaborating classes.

#### CRC analysis procedure &sect; 8.4.2.1 

CRC analysis should always be used in conjunction with noun/verb analysis of use cases, requirements, glossary, and other relevant documentation, unless the system is very simple. The CRC analysis procedure is straightforward and the key is to separate information gathering from information analysis. CRC is therefore best run as a two-phase activity.

#### Phase 1: Brainstorm - gather the information &sect; 8.4.2.2

The participants are OO analysts, stakeholders, and domain experts. You also need a facilitator. The procedure is as follows.

- 1. Explain that this is a true brainstorm.
- 1.1. All ideas are accepted as good ideas.
- 1.2. Ideas are recorded but not debated- never argue about something, just write it down and then move on. Everything will be analyzed later.
- 2. Ask the team members to name the "things" that operate in their business domain - for example, customer, product.
- 2.1. Write each thing on a sticky note - it is a candidate class, or attribute of a class.
- 2.2. Stick the note on a wall or whiteboard.
- 3.	Ask the team to state responsibilities that those things might have - record these in the responsibilities compartment of the note.
- 4.	Working with the team, try to identify classes that might work together. Rearrange the notes on the whiteboard to reflect this organization and draw lines between them. Alternatively, record collaborators in the collaborators compartment of the note.

#### Phase 2: Analyze information &sect; 8.4.2.3

The participants are OO analysts and domain experts. How do you decide which sticky notes should become classes and which should become attributes?
Go back and look at section 8.3.2 - analysis classes must represent a crisp abstraction in the problem domain. Certain sticky notes will represent key business concepts and clearly need to become classes. Other notes may become classes or attributes. If a note logically seems to be a part of another note, this is a good indication that it represents an attribute. Also, if a note doesn't seem to be particularly important or has very little interesting behavior, see if it can be made an attribute of another class.

If in doubt about a note just make it a class. The important point is to make a best guess and then drive this process to closure; you can always refine the model later.

### Finding classes by using the RUP stereotypes &sect; 8.4.3


A useful technique comes from RUP in the form of RUP stereotypes. The idea is that you consider three distinct types of analysis class during your analysis activity. This is a way of focusing your analysis on specific aspects of the system. We consider this an optional technique that you can use to complement the core noun/verb and CRC card analysis techniques presented earlier.

Three distinct types of analysis class can be distinguished by the stereo types shown in Table 8.1 (p. 167).

< insert Table 8.1 here>

We look at how to find each of these types of analysis class in the next three subsections.

#### Finding classes by using the RUP stereotypes &sect; 8.4.3.1

These classes exist on the boundary of your system and communicate with external actors.
You find these classes by considering the subject (system boundary) and discovering what classes mediate between the subject and its environment. According to RUP there are three types of boundary> class:

1.	user interface classes - classes that interface between the system and humans;
2.	system interface classes	classes that interface with other systems;

3.	device interface classes - classes that interface with external devices such as sensors.
Each communication between an actor and a use case in your model must be enabled by some object in your system. These objects are instances of boundary classes. You can work out what type of boundary class is indicated by considering what the actor represents (Table 8.2).

<insert TABLE 8.2 here>

When a boundary class services more than one actor, these actors should generally be of the same kind (representing a human, system, or device). It can be an indication of bad design if a boundary class services actors of different types!

Because you are still in analysis, it is important to keep these classes at the right level of abstraction. For example, when modeling a «boundary» class that represents a GUI, Just model the top-level window and leave all the details of the widgets that compose the window to design. Alternatively, you can introduce a dummy class that represents the whole user interface.

Similarly, with system interface classes and device interface classes, you are concerned with capturing the fact that there is a class that mediates between your system and something else, but not with the specific details of that class. You will decide on these details later in design.

For example, if you are writing an e-commerce system that needs to interface to an Inventory system, you can represent the interface to the Inventory system by a class called InventoryInterface that is stereotyped «boundary». This is sufficient detail for an analysis model.

#### Finding «control» classes &sect; 8.4.3.2

These classes are controllers—their instances coordinate system behavior that corresponds to one or more use cases.

You find control classes by considering the behavior of the system as described by the use cases and working out how that behavior should be partitioned among the analysis classes. Simple behavior can often be distributed between boundary or entity classes, but more complex behavior, such as order processing, is generally best localized by introducing a suitable controller class such as an OrderManager. Some modelers (ourselves included!) often indicate control classes by appending Manager or Controller to the name of the class.

The key point when working with control classes is to let the classes arise naturally from the problem domain itself. Some modelers artificially introduce a control class for each use case to control or execute that use case. This is a dangerous approximation that leads to a model that looks more like a top-down functional decomposition than a true 00 analysis model. In fact, this is one of the reasons that we consider using the RUP stereotypes as optional—they can lead novice modelers astray!

In the real world, controllers arising directly from the problem domain (rather than as a by-product of a specific analysis technique) tend to cut across several use cases. A good example might be a controller such as a Registrar class that is involved in many of the use cases that describe a course registration system. Similarly, a single use case may require the participation of many control classes.

If you find that a controller class has a very complicated behavior, this indicates that you may be able to break it down into two or more simpler controllers that each implement a cohesive subset of that behavior. Each of the simpler classes that you identify must still be something that naturally occurs in the problem domain. For example, when designing a course regis¬tration system, you might originally introduce a control class called 
CourseRegistrationController that coordinates the whole process. But such a class has a complex behavior, and so you might decide to break it up into a set of collaborating classes with each class handling one or two aspects of that behavior. The CourseRegistrationControUer might be decomposed into Registrar, CourseManager, and PersonnelManager classes. Notice that each of these classes represents a thing that exists in the problem domain.

A good way to explore controller classes is to imagine yourself in the role of the class. What would you have to do in that situation?

#### Finding «entity» classes &sect; 8.4.3.3

These classes model information about something and usually have very simple  ehavior that amounts to little more than getting and setting values. Classes that represent persistent information such as addresses (an Address class) and people (a Person class) are entity classes.

Entity classes 

 - cut across many use cases;
 - are manipulated by control classes;
 - provide information to, and accept information from, boundary classes;
 - represent key things managed by the system (e.g., Customer);
 - are often persistent.

Entity classes express the logical data structure of the system. If you have a data model, then entity classes are intimately related to entities or tables in this model.

### Finding classes from other sources &sect; 8.4.4

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

This is probably the most efficient way of finding classes for your models—just take them off the shelf!


## Creating a first-cut analysis model &sect; 8.5

To create a first-cut analysis model, you need to consolidate the outputs of noun/verb analysis, CRC analysis, RUP stereotypes, and a consideration of other sources of classes (especially archetype patterns) into a single UML model in a modeling tool. Perform consolidation as follows.

- 1. Compare all sources of classes.
- 2. Consolidate the analysis classes, attributes, and responsibilities from the different sources and enter them into a modeling tool.
- 2.1. Use the project glossary to resolve synonyms and homonyms.
- 2.2. Look for differences in the results of the three techniques - differences indicate areas where there is uncertainty or where more work might be done. Resolve these differences now, or highlight for later work.
- 3. Collaborators (or lines between sticky notes on the whiteboard) represent relationships between classes. You will see how to model these in Chapter 9.
- 4. Improve the naming of classes, attributes, and responsibilities to follow any standard naming conventions that your company has, or follow the simple naming conventions described in Chapter 7.

The output from this activity is a set of analysis classes where each class may have some key attributes and should have between three to five responsibilities. This is your first-cut analysis model.

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
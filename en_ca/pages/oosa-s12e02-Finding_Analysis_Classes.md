# Finding Analysis Classes #

## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;8 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;8.6 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Describe and use the process of noun/verb analysis to discover analysis classes
	* Describe the process of CRC analysis to discover analysis classes
	* List and define the RUP stereotypes
	* Explain the purpose of the RUP stereotypes in an analysis model
	* Create a first cut analysis model using the techniques in this chapter

## Finding Classes &sect;8.4 ##

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

# Relationships #

> In UML, relationships connect things.
> 

## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;9 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;9.6 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Define and give examples of links as relationships among objects
	* Draw and interpret object diagrams for a problem domain
	* Define and give examples of associations as relationships among classes
	* Define and give examples of multiplicity on associations
	* Define and give examples of navigability on associations
	* Express association equivalence with class attributes in OO programming languages
	* Define and give examples of association classes
	* Define and give examples of &laquo;stereotype&raquo; dependency relationships among objects and classes

## What is a Relationship? &sect;9.2 ##

- Relationships are meaningful connections between modeling elements
- They are a UML way of connecting things together
- Some familiar relationships:
	*  between actors and use cases (associations)
	*  between use cases and use cases (include, extend)
	*  between actors and actors (generalization)
	*  between objects and classes (instantiate)
-In Chapter &sect;9, we further explore:
	* relationships between objects (called _links_)
	* relationships between classes (called _associations_)

> Links between objects are actually instances of the associations between their classes.
> 

## What is a Link? &sect;9.3 ##

> An executing OO application is a harmonious collective of collaborating objects.
> 

In OO applications:

- Objects get created
- Objects have connections to one other via links
- Object send messages to one another along these links
- Objects execute a corresponding operation when they receive a message on a link
- Object get destroyed
- Java implements links as object references

### Object Diagrams &sect;9.3.1 ###

> An object diagram is a snapshot of a collective of collaborating objects
> 

- An object diagram shows **Objects** and the **Links** between them
- Objects that are connected by links may adopt various roles relative to each other
- See Figure 9.2 

![Book Club object diagram][od-bookclub]

The diagram contains 4 objects with the following links:

- between `bookClub` and `ila`, who is playing the role of `chairperson`
- between `bookClub` and `erica`, who is playing the role of `secretary`
- between `bookClub` and `naomi`, who is playing the role of `member`

> Links are *dynamic* connections between objects and they can change over time as objects send messages to one another.
> 

![In class activity - objects and links][od-sections]

> ### In Class Activity
> - What are the objects in the above diagram?
> - Describe the links and their roles?

- In Figure 9.2, the links are bidirectional (messages can be sent in both directions across the link)
- If a link is unidirectional, use a navigability arrow to specify the direction messages may pass over the link
- Navigability is like a one-way street (messages should only flow in the direction indicated by the arrowhead)

We will follow these common idioms for representing navigation:

- all crosses are suppressed (non-navigability not shown)
- bidirectional associations have *no* arrows (use a straight line between objects)
- unidirectional associations have a single arrow (show the arrow in the direction messages flow)

![Unidirectional link][od-unidir]

- the link between `:Person` and `:Address` is unidirectional
- the `:Person` object has a reference to the `:Address` object, but **not** vice versa
- messages are sent from `:Person` to `:Address`

Lines used to represent links can be of three styles for drawing paths:

- **orthogonal**: where the path consists of a series of horizontal and vertical segments;
- **oblique**: where the path is a series of one or more sloping lines;
- **curved**: where the path is a curve.

> ### In Class Activity
> - Consider a shopping application like Amazon
> - Represent the classes and objects (with state and links) of a typical shopping experience
> - There are various categories of products for sale
> - One needs an account to purchase products
> - One needs a payment method to purchase products
> - Products are placed in a shopping cart to be considered for purchase
> - Wish lists can be created and products placed in them if one wants to purchase them later
> 
> Draw on object diagram to represent the objects needed to for a typical shopping experience on Amazon.
>


## Association &sect;9.4 ##

Associations are relationships between classes. The key point is that an association between classes *will* result in a link between instances of these classes.

Figure 9.56 shows the relationship between classes and objects, and between links and associations. Because you *can't* have a link without an association, it is clear that *links* depend on *associations*; you can model this with a dependency relationship (the dashed arrow). To make this representation explicit, you stereotype the dependency &laquo;instantiate&raquo;

### Association Syntax &sect;9.4.1 ###

An association may have:

- an association name;
- role names;
- multiplicity;
- navigability.

Association names should be verb phrases because they indicate an action that the source object is performing on the target object. The name may also be pre- or post-fixed with a small black arrowhead to indicate the direction in which the association should be read. Association names are in lowerCamelCase.

In the example in Figure 9.6 you read the association as follows: "a Company employs many persons". Even though the arrow indicates the direction in which the association should be read, you cal always read the association in the other direction. So, in Figure 9.6 you can say "Each Person is employed by exactly one Company" at any point in time.

### Multiplicity &sect;9.4.2 ###

Constraints are one of the three UML extensibility mechanisms, and multiplicity is the first type of constraint that we have seen. It is also by far the most common type of constraint.
Multiplicity constrains the number of objects of a class that can be involved in a particular relationship *at any point in time*.
The phrase "at any point in time" is vital to understanding multiplicities. In Figure 9.8 you can see that at any point in time a Person object is employed by exactly one Company object. However, *over time* a Person object might be employed by a series of Company objects (one after the other).

Looking at Figure 9.8, you can see something else that is interesting. A Person can never be unemployed - it is always employed by exactly one Company object. The constraint therefore embodies two business rules of this model:

- Person objects can only be employed by one Company objects at a time.
- Person objects *must* always be employed.

Whether or not these are reasonable constraints depends entirely on the requirements of the system you are modeling, but it is what this model actually says.
Multiplicity is specified as a comma-separated list of intervals, where each interval is of the form:

minimum..maximum

minimum and maximum may be integers or any expression that yields an integer result.
If multiplicity is not explicitly stated, then it is undecided - there is no "default" multiplicity in UML.

Table 9.1 provides some examples of multiplicity syntax.

The example given in Figure 9.9 illustrates that multiplicity is actually a powerful constraint that has a big effect on the business semantics of the model. If you read the example carefully, you will see that:

- a Company can have exactly 7 employees (no more, no fewer).
- a Person can be employed by exactly one Company (meaning that in this model, a Person can't have more than one job at a time);
- a BankAccount can have exactly one owner (no more, no fewer);
- a BankAccount can have one or many operators;
- a Person may have between zero and many BankAccount;
- a Person may operate between zero and many BankAccounts.

When reading a UML model, it is vital to figure out exactly what the model actually says, rather than making many assumptions or hallucinating semantics.

When a class has an association to itself, it is called a reflexive association. In Figure 9.10, each Directory can have links to zero or more Directory objects that play the role of **subdirectory**, and to zero or one **Directory** that plays the role of parent. In addition, each directory is associated with zero or more **File** objects. The top half of Figure 9.10 shows the class diagram, and the bottom half shows an example object diagram that accords with the class diagram.

When modeling, you'll find that objects often organize themselves into hierarchies or networks. 

A hierarchy has one root object, and every other node in the hierarchy has exactly one object above it. Directory trees naturally form hierarchies. So do part breakdowns in engineering, and elements in XML and HTML documents. The hierarchy is a very ordered, structured and sometime rigid way of organizing objects. An example is given in Figure 9.11.

In a network, however, there is often no root object (although that is not precluded). In networks, each object may have many objects directly connected to it. There is no concept of "above" or "below" in a network. It is a much more flexible structure in which it is possible that no node has primacy over another. The World Wide Web forms a complex network of nodes, as illustrated in a simple way in Figure 9.12.

### Navigability &sect;9.4.3 ###

Navigability shows us that is it possible to traverse from an object of the source class to one or more objects of the target class, depending on the multiplicity. In Figure 9.13, Order objects can send messages to Product objects, but not vice versa.

One of the goals of good OO analysis & design is to minimize coupling between classes, and using navigability is a good way to do this. By making the association between Order and Product unidirectional, you can navigate from Order objects to Product objects, but there is no navigability back from Product objects to Order objects. So Product objects *do not know* that they may be participating in a particular Order, and therefore there have **no** coupling to Order. 

From a programming standpoint, this means that coding an Order will require knowledge of Product methods available for calling (the message that will be passed from Order objects to Product objects). On the other hand, the programmer working on Product doesn't need to know anything about the Order methods, as Product objects will **never** need to invoke them.

The UML 2.0 specification suggests three idioms for using navigability on your diagrams:

1. Make navigability completely explicit. All arrows and crosses are shown.
2. Make navigability completely invisible. No arrow or crosses are shown.
3. Suppress all crosses. Bidirectional associations have no arrows. Unidirectional association have a single arrow.

- Idiom 1 tends to clutter diagrams.
- Idiom 2 should be avoided as it hides far too much important information.
- Idiom 3 is a reasonable compromise and is used almost exclusively in practice.

There are summarized in Figure 9.14.

### Associations and Attributes &sect;9.4.4 ###

When an object needs to send a message to another object, it needs to have the target object's reference - which is stored in the class attributes.

The reference is of type 'address of object'.
For example, if a House object were to hold the address of an Address object, the following Java code would represent the situation:

	public class House
	{
	   private Address oAddress;
	}

where oAddress is the reference of an external Address object.

When multiplicities greater than 1 are present, they are implemented as either:

- an attribute of type array (a construct that is supported by most languages);
- an attribute of some type that is a collection.

Collections are just classes whose instances have the specialized behaviour of being able to store and retrieve references to other objects.

### Association Classes &sect;9.4.5 ###

If we consider Figure 9.18, at first glance, it seems like a fairly innocuous model:

- each Person object can work for many Company objects;
- each Company object can employ many Person objects.

However, what happens if we add a rule saying that each Person has a salary with each Company they are employed by?

You can't really make the Person salary an attribute of the Person class as each Person can work for many Companies, and may have a different salary with each Company. Similarly, you can't really make the Person salary an attribute of Company, as each Company instance employs many Persons, all with potentially different salaries.

The answer is that the Salary is actually a property of the association itself.
For each employment association that a Person object has with a Company object, there is a specific salary.

UL allows you to model this situation with an association class as shows in Figure 9.19.

Note that an association class is an association that is *also* a class. Not only does it connect two classes like an association, it defines a set of features that belong to the association itself. Association classes can have attributes, operations, and other associations.

Instances if association classes are really *links* that have attributes and operations. The unique identity of these links is determined *exclusively* by the identities of the objects at either end. This factor constrains the semantics of the association class - you can only use it when there is a *single unique link* between two objects at any point in time. This is simply because each link, which is an instance of the association class, must have its own unique identity.
In Figure 9.19, using the association class means that you constrain the model such that for a given Person object and a given Company object, there can only be *one* Job object. In other words, each Person can only have one Job with a given Company.
However, you have the situation where a given Person object can have more than one Job with a given Company object, then you **can't** use an association class-the semantics just don't match!

But you still need somewhere to put the salary for each Company/Job/Person combination, so you reify (make real) the relationship by expressing it as a normal class.
In Figure 9.20, Job is now an ordinary class, and you can see that a Person may have many Jobs where each Job is for exactly one company.

### Qualified Associations &sect; 9.4.6 ###

You can use a qualified association to reduce an n-to-many association to an n-to-one association by specifying a unique object (or group of objects) from the target set. They are very useful modeling element as they illustrate how you can look up, or navigate to, specific objects in a collection.

Consider the model in Figure 9.21. A Club object is linked to a set of Member objects, and a Member object is likewise linked to exactly one Club object.
The following question arises: given a Club object that is linked to a set of Member objects, how could you navigate to one specific Member object?

Clearly you need some unique key that you can use to look up a particular Member object from the set. This is known as a qualifier. Many qualifiers are possible (name, credit card number, social security number), but in the example above, every Member object has a memberID attribute value that is unique to that object. This, then, is the look-up key in this model.

You can show this look-up on the model by appending a qualifier to the Club end of the association. It is important to recognize that the qualifier belongs to the *association end* and **not** to the Club class.

## Dependency &sect;9.5 ##

A dependency indicates a relationship between two or more model elements whereby a change to one element (the supplier) may affect or supply information needed by the other element (the client). In other words, the client depends in some way on the supplier.

For ecxample, you may pass an object of one class (actually its reference, the object doesn't move) as a parameter to an operation of an object of a different class.There clearly is some sort of relationship between the classes of those objects, but it is not really an association.

UML 2 specifies three basic types of dependency, shown in Table 9.2.

Dependencies also occur between:

- packages and packages
- objects and classes

Most of the time, you just use an unadorned dotted arrow to indicate a dependency and don't worry about what type of dependency it is.

---

[od-bookclub]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Ch09-ObjectRoles-Club.png

[od-sections]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Ch09-ObjectRoles-RRC.png

[od-unidir]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Ch09-unidir.png


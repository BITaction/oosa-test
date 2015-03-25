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
- In Chapter &sect;9, we further explore:
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
> Consider a shopping application like Amazon online. Draw an object diagram to represent the objects and links of a typical shopping experience based on the following general statements. In the modeling tool you will need to create classes to instantiate the objects.
>
> - Products are placed in a shopping cart to be considered for purchase
> - There are various categories of products for sale
> - Consumers can purchase multiple quantities of different products
> - One needs an account to purchase products
> - One needs a payment method to purchase products
> - Wish lists can be created and products placed in them if one wants to purchase them later
> 

## Association &sect;9.4 ##

> Associations are relationships between classes, just as links are relationships between objects.
> 

- An association between classes *will* result in a link between instances of these classes
- See Figure 9.5

![][od-relations1]

- An object diagram showing the relationships among objects and classes, and between links and associations
- `bookClub:Club` is an object that is an instance of class `Club`
- bookClub is instantiated from Club and hence depends on Club (as a template)
- `ila:Person` is an object that is an instance of class `Person`
- ila is instantiated from Person and hence depends on Person (as a template)
- bookClub has a link to ila who is in the role of chairperson
- the link between bookClub and ila is instantiated from the association between Club and Person
- Hence, the link between the objects depends on the association between the classes
- The objects and link are a representation of reality (at a certain time)
- The classes and association are an abstraction (template) of this reality

### Association Syntax &sect;9.4.1 ###

An association may have:

- an association name
- role names
- multiplicity
- navigability

Association name:

- should be a verb phrase
- may be pre- or post-fixed with a small black arrowhead to indicate the direction in which to read the association
- should express the active relationship made by the association
- should not be used in conjunction with role names (use one or the other)
- is written in lowerCamelCase

See Figure 9.6:

![Association name][cls-assoc-name]

- `employs` is an association name
- The direction indicates the normal way of considering the association
- Normally, read the association as: "a Company employs many persons"
- However, can be read in the other direction as: "each Person is employed by exactly by one Company"

Role name:

- should be a noun or noun phrase
- can be on one or both ends of the association
- should express the role that the linked instances play in the relationship
- should not be used in conjunction with an association name (use one or the other)
- are written in lowerCamelCase

See Figure 9.7:

![Role names][cls-role-name]

- `employee` is a role name stating that Person instances play the role of employee
- `employer` is a role name stating that Company instances play the role of employer

### Multiplicity &sect;9.4.2 ###

> Multiplicity constrains the number of objects of a class that can be involved in a particular relationship *at any point in time*.
> 

- Multiplicity is a common type of constraint expressed in UML
- The phrase "at any point in time" is vital to understanding multiplicities

See Figure 9.8:

![Multiplicity][cls-multiplicity]

- At any point in time a Person object is employed by exactly one Company object
- However, *over time* a Person object might be employed by a series of Company objects (one after the other)
- A Person can never be unemployed - it is always employed by exactly one Company object
- The constraint embodies two business rules of this model:
	* Person objects can only be employed by one Company objects at a time
	* Person objects *must* always be employed
- Whether or not these are reasonable constraints depends entirely on the requirements of the system being modeled
- Multiplicity is specified as a comma-separated list of intervals, where each interval is of the form:

		minimum..maximum

- `minimum` and `maximum` may be integers or any expression that yields an integer result
- If multiplicity is not explicitly stated, then it is undecided
- There is no "default" multiplicity in UML

See Table 9.1 for examples of multiplicity syntax.

Multiplicity | Meaning
-------------|--------
0..1 | zero or one
1 | exactly one
0..* | zero or more
* | zero or more
1..* | one or more
3..5 | three to five

> ### In Class Activity
> Multiplicity is a powerful constraint that has a big effect on the business semantics of the model. Always read a model exactly as it is written (or develop it exactly as the requirements read).
>
> Create a class diagram (model) that represents the following:
> 
> - a Company can have exactly 7 employees (no more, no fewer)
> - a Person can be employed by exactly one Company (meaning that a Person can't have more than one job at a time)
> - a BankAccount can have exactly one Person as an owner (no more, no fewer)
> - a BankAccount can have one or many Persons as an operator
> - a Person may have between zero and many BankAccounts
> - a Person may be the operator of zero or many BankAccounts
>

#### Reflexive Associations &sect;9.4.2.1 ####

> A _reflexive association_ is when a class has an association to itself.
> 

- Objects of the class have links to other objects of the same class

![Self association][cls-assoc-self]

- Instances of `Company` as a holding company can have links to other instances of `Company` as subsidiary companies

> ### In Class Activity
> The file system on your computer can be modeled with a reflexive association. Consider the following general statements about a typical file directory structure.
>
> Create a class diagram (model) of a file directory structure, along with an object diagram showing a specific example of directories and files (perhaps some of the files and directories on your computer).
>
> - A Directory object can be linked to zero or more Directory objects that play the role of **subdirectory**
> - A Directory is normally linked to one other Directory that plays the role of **parent**
> - The root Directory has no parent
> - Each Directory object can be linked to zero or more File objects
> - Each File must exist in only one Directory
>

#### Hierarchies and Networks &sect;9.4.2.2 ####

> When modeling, you'll find that objects often organize themselves into hierarchies or networks.
> 

Hierarchy:

- has one root object
- the root has zero objects above it
- every other object in the hierarchy has exactly one object above it
- very ordered, structured, and somewhat rigid way of organizing objects
- directory trees naturally form hierarchies
- See Figure 9.11 for UML representation

Network:

- often no root object (although it may have one)
- each object may have many objects directly connected to it
- no concept of "above" or "below"
- flexible structure in which it is possible that no node has primacy over another
- The World Wide Web forms a complex network of nodes
- See Figure 9.12 for UML representation

### Navigability &sect;9.4.3 ###

> Navigation expresses there should be an efficient way for objects of a source class to send messages to objects of a target class.
> 

![][cls-source-target]

- Traverse from an object of the source class to one or more objects of the target class
- Given a source object, one can efficiently send a message to a target object
- Messages cannot necessarily be sent from target to source
- Good OO analysis will minimize coupling between classes
- Navigability can do this by making unidirectional associations
- Target objects *do not know* that they may be participating with source objects, and therefore have **no** coupling to them

![][cls-order-product]

- `Order` objects should easily navigate to `Product` objects, so Orders are coupled to Products
- There is no navigability from `Product` objects to `Order` objects, so Products have no coupling to Orders

From a programming perspective:

- The programmer working on Order will require knowledge of Product operations available for calling
- On the other hand, the programmer working on Product doesn't need to know anything about the Order methods

The UML 2.0 specification suggests three idioms for navigability:

1. Make navigability completely explicit. All arrows and crosses are shown.
	* Make navigability fully visible
	* Tends to clutter diagrams
2. Make navigability completely invisible. No arrow or crosses are shown.
	* hides valuable navigation information
	* should be avoided
3. Suppress all crosses. Bidirectional associations have no arrows. Unidirectional association have a single arrow.
	* reasonable compromise
	* used almost exclusively in practice

See Figure 9.14 for summary of these idioms

> If an association is not navigable it may still be traversed, but the cost will be high.
> 

### Associations and Attributes &sect;9.4.4 ###

> Associations can ultimately be represented as class attributes.
> 

- To send a message an object reference is needed
- A class attribute can store an object reference

![][cls-house-assoc]

- Consider a House associated to an Address
- A House could have an attribute with a reference to an Address

![][cls-house-attr]

- The Java code to represent this model could be:

		public class Address {

		}

		public class House
		{
		   private Address location;
		}

When multiplicities greater than 1 are present, they are implemented as either:

- an attribute of type array (a construct that is supported by most languages)
- an attribute of some type that is a collection

> Collections are just classes whose instances have the specialized behavior of being able to store and retrieve references to other objects.
> Many OO programming languages (like Java) support a collection framework.
> 
> ### READ MORE
> - [Java Collections Framework][java-coll-over]
> - [Java Docs Collection Interface][java-coll-docs]
> - [Java Collections Tutorial][java-coll-tut]

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

- Qualified associations can reduce a "many" side of an association to a "1" side, with additional specification
- They can illustrate how you to look up, or navigate to, specific objects in a collection
- This is leaning towards design and will be addressed in the design course

## Dependency &sect;9.5 ##

> A dependency indicates a relationship between a client and a supplier.
> 

![][cls-client-supplier]

- A change to the supplier may affect or supply information needed by the client
- In other words, the client depends in some way on the supplier


UML 2 specifies three basic types of dependency (see Table 9.2 for details):

Type | Purpose
-----|--------
Usage | client uses some services of the supplier
Abstraction | supplier is more abstract than the client
Permission | supplier grants some sort of permission to the client

Dependencies occur between lots of elements in UML like:

- classes and other classes
- packages and other packages
- objects and classes
- use cases and other use cases

> ### READ MORE
> - &sect;9.5.1 Usage dependencies
> - &sect;9.5.2 Abstraction dependencies
> - &sect;9.5.3 Permission dependencies
>
> Under which type does the &laquo;instantiate&raquo; dependency fit?
> 

---

[od-bookclub]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Ch09-ObjectRoles-Club.png

[od-sections]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Ch09-ObjectRoles-RRC.png

[od-unidir]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Ch09-unidir.png

[od-relations1]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Ch09-relations1.png

[cls-assoc-name]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Ch09-assoc-name.png

[cls-role-name]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Ch09-assoc-role.png

[cls-multiplicity]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Ch09-assoc-role.png

[cls-assoc-self]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Ch09-assoc-self.png

[cls-source-target]: http://yuml.me/33dc1a5c
<!-- 
// General source to target navigation
[Source]->[Target]
-->

[cls-order-product]: http://yuml.me/2ecb2e7d
<!--
// Order and Product navigation
[Order]0..*-1..*>[Product]
-->

[cls-house-assoc]: http://yuml.me/9a39aa66
<!--
// House and Address association
[House]1-1 location >[Address]
-->

[cls-house-attr]: http://yuml.me/faa698b8
<!--
// House and Address attribute
[House|location:Address]1-1>[Address]
-->

[java-coll-over]: https://docs.oracle.com/javase/8/docs/technotes/guides/collections/overview.html

[java-coll-docs]: https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html

[java-coll-tut]: http://docs.oracle.com/javase/tutorial/collections/intro/index.html

[cls-client-supplier]: http://yuml.me/25c24769
<!--
// Client and Supplier dependency 
[Client]-.->[Supplier]
-->
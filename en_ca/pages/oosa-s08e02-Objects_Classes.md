# Objects and Classes #

> Objects and Classes are the basic building blocks of OO systems
> 

## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;7 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;7.8 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Define an object in terms of identity, state, and behavior
	* Define object principles of encapsulation and messaging
	* Identify and explain object notation in UML
	* Define a class and its relation to objects through instantiation
	* Explain class instantiation
	* Identify and explain class notation in UML
	* Explain instance scope versus class scope
	* Describe the use and purpose of constructors and destructors in OO languages

## What are Objects?  &sect;7.2 ##

> Objects combine data and function into a cohesive unit.
> 

- The UML reference manual defines an object as "A discrete entity with a well-defined boundary that encapsulates state and behavior; an instance of a class"

Objects have identity, state and behavior.

Property | Purpose | Qualification
---------|---------|--------------
Identity | makes an object distinct from all other objects | comes from something outside of the object itself
State | the value of the object's attributes at a given time | object state can change over time
Behavior | what the object can do | can varying depending on object state and can change object state

For example, in a running Java program, at any given time, for any given object:

- its identity can be represented by the object's address in memory
- its state by the values of the object's attributes 
- its behavior by the instance scope operations defined in the object's class

> ### In Class Activity
> - Look around the classroom
> - Identify some objects
> - What could express their identity?
> - How can you define their current state? What is changeable about their state?
> - How can you define their behavior? So, then what could express their _class_?

### Encapsulation  &sect;7.2.1 ###

> Encapsulation is data-hiding and a primary benefit of OO programming.
> 

Encapsulation:

- hides data structures and values inside objects
- provides the only access to the outside world by means of public operations

Outside world:

- need **not** be concerned about an object's internal structure
- need **only** be concerned with what the object can do - the public _services_ offered by the object

See Figure 7.2 for account object example

### Messaging  &sect;7.2.2 ###

> OO systems function by objects sending messages to one another - this is collaboration.
> 

- A message consists of a call to one of an object's methods
- Consider the following fragment of code

		dArea = oMyShape.calcArea()

- This code would exist as the behavior of some object in an OO System
- `oMyShape` is a reference to identify some collaborating object
- `calcArea()` is a message being sent to object `oMyShape`
- `dArea` is a variable to hold the value returned by `oMyShape` performing the operation (service) `calcArea()`

An OO system is a collaborating set of objects where:

- objects are created
- objects send messages to one another to invoke their services
- objects respond to messages by running a method that was called in a message
- objects finish up by being destroyed (i.e., removed from memory)

See Figure 7.3 for account object example

## UML Object Notation  &sect;7.3 ##

> Objects of the same class have the same operations and the same attributes, but usually have different attribute values.
> 

- A UML object icon is a 2-compartment shape
- See example in Figure 7.4

![Object syntax in UML][object-syntax]

- Top compartment is the object name and represents the object identifier, which is **always** underlined
- Underlining is important to avoid confusion between an object or a class
- Naming an object in UML is quite flexible

Name Using | Example | Qualification
-----------|---------|--------------
Class name alone | <span style="text-decoration:underline">:Student</span> | signifies an anonymous object
Object name alone | <span style="text-decoration:underline">tonySmith</span> | identifies a specific object, but not its class
Object name : Class name | <span style="text-decoration:underline">tonySmith:Student</span> | fully qualified object

- Bottom compartment contains a list of attributes for the object
- Each attribute can show:

		name : type = value

- The only mandatory part is the `name`
- You may choose to show all, some, or none of the attribute values, depending on the purpose of the diagram
- Some example attribute specifications:

		firstName : String = "Tony"
		lastName : String = "Smith"
		studentID = 43299524
		birthDate : Date
		interests

## What are Classes? &sect;7.4 ##

> A class is a template that describes the common features of a set of objects.
> 

- Every object is an instance of exactly one class
- A class is a template, like a cookie cutter, from which an object is created
- Classes allow us to describe the set of features that every object of a class *must* have
- Objects made from a class have the same attributes, but the values of these attributes can vary among the objects
- Objects made from a class respond to the same messages, but the behavior exhibited from these messages can vary among the objects

Bank Account example:

- two back account objects
- one has a thousand dollars, the other is overdrawn
- the message `withdraw(100)` can be sent to both bank account objects
- each object will likely respond differently because of their state

> Classification is possibly the single most important way that human beings have of ordering information about the world. It is also one of the most important OO concepts.
> 

- Given a set of objects, there are many ways to classify them
- See Figure 7.5 and textbook discussion
- Finding a workable classification scheme is a key goal of OO analysis

> ### In Class Activity
> - Consider the objects identified in a previous in class activity
> - How can these objects be classified?
> - Are there variations to the initial classification you gave?

### Classes and Objects &sect;7.4.1 ###

- A relationship in UML is defined as a "connection among model elements"
- A dependency relationship is between a supplier and a client
- In UML it is represented by a dotted line with an open arrowhead
- In a dependency relationship a change to the supplier can result in a change to the client

![Client and supplier dependency][client-supplier]

- Dependency relationships can be stereotyped
- The relationship between a class and objects of that class is an &laquo;instantiate&raquo; relationship
- See Figure 7.6

![Object instantiation dependency][object-instantiate]

> ### In Class Activity
> - Name a supplier in Figure 7.6
> - Name a client in Figure 7.6
> - Recreate Figure 7.6 in the visual modeling tool

### Class Instantiation &sect;7.4.2 ###

> Class instantiation creates a new object using a class as a template
> 

- In general, _instantiation_ means to create an instance of something from a given template
- We instantiate objects from a class
- We create new instances (objects) from a class
- The class comes first
- OO programming languages have special class operations called _constructors_ that perform instantiation
- Constructors allocate memory for the object, give it an identity, sets default values, and sets default links to other objects

## UML Class Notation &sect;7.5 ##

- UML syntax for a class is very rich
- apply the UML notion of optional adornments to a class
- only mandatory is the name compartment with the class name listed
- apply other adornments as necessary to enhance the understanding of the analysis model
- See Figure 7.7 

![Class adornments][class-adorn]

In analysis, you typically only need to show the following:

- class name
- key attributes
- key operations
- stereotypes (if they have business significance)

You typically **do not** show the following:

- tagged values
- operation parameters
- visibility
- initialization values (unless they have business significance)

### Name Compartment &sect;7.5.1 ###

- UML does not mandate any naming convention for classes
- There is a convention that is almost universally followed
- Class name is in UpperCamelCase
	* begins with an uppercase letter
	* Special symbols such as punctuation marks, dashes, underscores, ampersands, hashes and slashes are *always* avoided
- Avoid abbreviations *at all cost*
	* Call a class FlightSegment instead of FltSgmt
	* DepositAccount is preferable to DpstAcct
	* and so on...
	* Abbreviations make the model hard to read and can lead to costly misunderstandings
- Domain specific acronyms may be use if understood by all stakeholders
	* CRM may be used instead of CustomerRelationshipManagement if it is clear to all
	* The long form may still be more preferable for the long run if it avoids confusion
- Classes represent things, so a class name should be a *noun* or *noun phrase*

### Attribute Compartment &sect;7.5.2 ###

The only mandatory part of the UML attribute syntax is the attribute name. Attribute are in lowerCamelCase with a lowercase first letter. Again, do *not* use special symbols or abbreviations.

**Visibility**: the visibility adornment applies to attributes and operations within the class.

- See Table 7.3 for visibility adornments and their meaning

| Adornment |  Purpose  |
|:---------:|:---------:|
|     +     |   Public  |
|     -     |  Private  |
|     #     | Protected |
|     ~     |  Package  |


- See Table 7.4 for a comparison of visibility across 00 programming languages

**Type**: the type of an attribute can be a primitive type or another class.

- UML defines 4 primitive types (see Table 7.5)
- If your project targets Java, you may use Java data types, but then your model will be tied to that language
- Visual modeling tools typically provide a set of primitive types that can be mapped to OO programming language types
- This approach allows you to create a *platform independent model* (PIM) during analysis that can be translated to a *platform specific model* (PSM) during design

**Multiplicity**: Multiplicity is widely used in design but may also be used in analysis models as it can be used to  express certain business constraints relating to the "number of things" participating in a relationship.

- Collections - if the multiplicity expression results in an integer greater than 1, then you are specifying a collection of the type. For example, **colors: Color[7]** would model an attribute that is a collection of seven Color objects.
- Null values: Null can mean that we don't have a value yet (same as NULL in SQL databases). It may also mean that the address of an object is null because the object it points to hasn't been created yet, or that it has ceased to exist. It is essential to distinguish between the 2 situations.

**Initial value** The Initial value allows you to specify the value an attribute will take when the object is created. In design, it is good style to use initial values whenever possible - it helps to ensure that objects of the class are created in a valid and useful state.

### Operation Compartment &sect;7.5.3 ###

- Operations are functions that are bound to a particular class
- Every operation of a class **must** have a unique signature
- See Figure 7.10 for details
- Operations are named in lowerCamelCase
- The usually start with or contain a verb (as verbs indicate action and an operation *does* somethhing)

**Parameter direction**: Operation parameters can be given a direction - that is, you can indicate if the parameter brings a value into the operation, carries a value (a result) out of the operation, or both.

- operation(in p1: integer, inout p2:integer, out p3:integer, return p4:integer).
- See Table 7.6 for details

**Parameter default values**: You can give a default value to an operation parameter. When the operation is called, if no value has been given for the parameter, its default value will be used.

**Query operations**: Each operation has a property called *isQuery*. If you set that property to true in your modeling tool, the operation is a query operation. This means that it *has no side-effects* and doesn't change the state of the object it is called on. An operation that returns the value of an attribute is a query operation and should have its *isQuery* set to true.

### Class Stereotype Syntax &sect;7.5.4 ###

- There is a lot of flexibility in how stereotypes can be displayed
- See Figure 7.14 for options
- It is common to use the name in guillemets (&laquo;stereotypeName&raquo;) or just the UML icon
- Not all stereotypes have an equivalent icon representation

![Class stereotype common options][class-stereo]

## Scope &sect;7.6 ##

> Attributes and operations can be _instance scope_ or _class scope_.
> 

### Instance Scope and Class Scope &sect;7.6.1 ###

Up to now, you have seen that objects have their own copies of the attributes defined in their class. Similarly, the operations that you have seen so far all act on specific objects. This is the normal case, and we say that these attributes & operations have *instance scope*.

However, sometimes you need to define attributes that have a single shared value for *every* object of the class, and you need operations (such as constructors) that don't operate on any particular class instance. We say that these attributes and operations have *class scope*. Class scope features provide a set of global features for an entire class of objects.

### Scope Determines Access &sect;7.6.2 ###

Class scope operations can **only** access other class scope operations and attributes. Class scope operations can't access instance scope attributes & operations because:

- there might not be any objects of that class yet
- even if there are some, you don't know which one to use

## Object Construction and Destruction &sect;7.7 ##

### Constructors &sect;7.7.1 ###

- Constructors are special operations that create new instances of classes
- Constructors **must** be class scope
- Constructors are typically named the same as a class in modern OO programming languages
- A class can have many constructors, each with different parameters
- The constructor with no parameters is the _default constructor_ of a class

![Class with two constructors][customer-construct]

- Constructors are design considerations and are generally *not* shown on analysis models
- You could include a generic <span style="text-decoration:underline">+create()</span> as a placeholder during analysis
- Include parameters in constructors during analysis only if they are important from a business perspective

### Destructors &sect;7.7.2 ###

- Destructors are special operations that are called to dispose of an objects when it is no longer needed
- Some OO languages introduce a destructor named as `~Classname(parameterList)`
- Java provides a `finalize()` operation for each class, which is automatically called when the object is finally destroyed

---

[object-syntax]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Figure_7dot4.PNG

[object-instantiate]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Figure_7dot6.PNG

[client-supplier]: http://yuml.me/0d9e6137
<!-- client and supplier dependency
[Client]-.->[Supplier]
-->

[class-adorn]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Figure_7dot7.PNG

[customer-construct]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/Customer_Constructors.png

[class-stereo]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/class_stereo.png

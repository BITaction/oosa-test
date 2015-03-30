# Inheritance & Polymorphism #

> Inheritance and polymorphism are features that OO programming languages provide to support class generalization hierarchies.
> 

## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;10 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;10.6 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Define the concepts and generalization and specialization in relation to one another
	* Write concrete example of generalization of elements in UML
	* Define *Liskov Substitution Principle* and provide concrete examples of its use
	* Draw and describe the semantics of class generalization hierarchies
	* Define inheritance in class generalization hierarchies and identify what is inherited
	* Define overriding of operations in class generalization hierarchies
	* Describe the difference between concrete and abstract operations and classes in UML
	* List and explain advantages of abstract operations and classes in modeling
	* Identify and define the 3 main pillars of Object Oriented systems

## Generalization &sect;10.2

- *Generalization* is a relationship between a more general element and a more specific element
- The more specific element is *entirely consistent* with the more general element, but can contain more information
- The more specific element is said to be a *specialization* of the more general element
- The more specific element obeys the rule of *substitutability*

> **Substitutability**: one can use (substitute) the more specific element anywhere the more general element is expected.
> 
> This is known as the *Liskov Substitution Principle*
>

- Generalization requires a high degree of coupling between elements
 
### Class Generalization &sect;10.2.1 ###

- There are general things such as a tree
- There are more specific things such as an oak tree, a specific kind of tree
- Tree is a generalization of Oak Tree
- Generalization applies to all classifiers
- We've seen it applied to use cases and actors
- Now we'll see how it is applied to classes

See Figure 10.2

![][cls-shape-gen]

- the relationships from Square, Circle, and Triangle to Shape is know in UML as *generalization*
- there is a "general" class called Shape
- we consider variations of Shape that are like Shapes, but a more specialized form
- Square, Circle, and Triangle are subclasses (specializations) of Shape
- Shape is a superclass (generalization) of Square, Circle, and Triangle
- By the substitutability principle, we can use an instance of any subclass *anywhere* an instance of the Shape superclass is expected
- The above hierarchy can be obtained through a process of specialization or a process of generalization

In **specialization**, we would:

- first identify the general concept of Shape in analysis
- then specialize this into specific types of shapes as subclasses

In **generalization**, we would:

- first identify the more specialized Square, Circle and Triangle in analysis
- then notice that they all have common features that we could factor out into a more general superclass Shape

## Class Inheritance &sect;10.3 ##

- OO programming languages provide inheritance to support generalization hierarchies
- Subclasses inherit all the features of their superclass
- To be more specific, subclasses inherit:
	- attributes
	- operations
	- relationships
	- constraints

> Subclasses can also add new features and override superclass operations.
> 

### Overriding &sect;10.3.1 ###

> Overriding allows subclasses to provide a specialized implementation for inherited operations.
> 

See Figure 10.3

![][cls-shape-inher]

- Subclasses Square and Circle inherit all of the attributes, operations and constraints from the Shape superclass
- We don't explicitly show them, they are implicitly there (inherited)
- We say that Square and Circle are "types of Shape"
- Notice that operations `draw()` and `getArea()` defined in Shape can in no way be appropriate for the subclasses
- The default `draw()` operation that both subclasses have inherited from their parent clearly won't do
- In fact, this operation may not draw anything at all - it may be an empty operation at the Shape level
- The same applies to getArea() - how do you calculate the area of a general shape?
- Subclasses need to change superclass behavior
- Square and Circle need to implement their own (specialized) `draw()` and `getArea()` operations
- These will *override* the default operations supplied by their parent and provide a more appropriate behavior

See Figure 10.4

![][cls-shape-override]

- Subclasses Square and Circle will provide their own draw() and gerArea() operations
- When we show inherited operations in a subclass we are specifying that these will be overridden
- To override an operation, a subclass **MUST** provide an operation with *exactly* the same signature as the superclass operation
- UML defines operation signature as the operation name, its return type, and the types of all the parameters
- This becomes much more important during design when all types need to be specified

### Abstract Operations and Classes &sect;10.3.2 ###

> Abstract operations have no implementation. Abstract classes cannot be instantiated with objects.
> 

- The draw() operation in class Shape has no sensible implementation
- The concept of "drawing a shape" is too abstract to have any concrete implementation at the level of Shape
- Specify that an operation lacks implementation by making it an *abstract* operation
- In UML, you write the operation name in italics to indicate that it is abstract

![][cls-shape-abstract]

Abstract operations and classes: 

- Operations *draw()* and *getArea()* in Shape are abstract - they have no implementation (no code)
- A class with one or more abstract operations is incomplete as there are operations that don't have implementation
- This means that you can't instantiate such classes, they are known as abstract classes
- You write the class name in italics to show that it is abstract
- Superclass *Shape* is therefore an abstract class

Concrete operations and classes:

- Subclasses Square and Circle provide their own implementations of draw() and getArea()
- Operations `draw()` and `getArea()` in these subclasses are concrete operations
- This makes the subclasses complete classes that can instantiated
- Classes that can be instantiated are called concrete classes
- Square and Circle subclasses are concrete classes

**NOTE**: Operation `getBoundingArea()` is a concrete operation of Shape because the bounding area of every kind of Shape is calculated in exactly the same way - it is the width of a shape multiplied by its height.

Advantages of abstract classes and operations:

- You can define a set of abstract operations in the abstract superclass that **must** be implemented by all Shape subclasses. You can think of this as defining a 'contract' that all kinds of Shape subclasses *must* implement.
- You can write code to manipulate Shapes and then substitute Circle, Square, and other Shape subclasses as appropriate. According to the substitutability principle, code written to manipulate Shapes should work for all Shape subclasses.

### Level of Abstraction &sect;10.3.3 ###

> Classes at the same level in a generalization hierarchy should be at the same level of abstraction.
> 

See Figure 10.6

![][cls-abs-wrong]

- maintain a uniform level of abstraction at each level of the generalization hierarchy
- JaguarXJS is a *type* of car, which is a lower level of abstraction than Truck
- Fix this model quite easily by inserting a Car superclass between Vehicle and JaguarXJS

![][cls-abs-right]

- Adding a Ford F150 truck you would have consistent levels of abstraction

![][cls-abs-right2]

### Multiple Inheritance &sect;10.3.4 ###

- UML allows a class to have more than one direct superclass, called *multiple inheritance*
- The subclass inherits from *all* its direct superclasses
- Multiple inheritance is usually considered to be a design issue
- Most modern OO programming languages do not even support multiple inheritance



## Polymorphism &sect;10.4 ##

Polymorphism means "many forms". A polymorphic operation is one that has meny implementations. You have already seen two polymmorphic operations in the Shape example. The abstract operations sraw() and getArea() in the Shape class have two different implementations - an implementation in the Square class and one in the Circle class.

Figure 10.7 (p. 212) illustrates polymorphism perfectly.
We define an abstract *Shape* class with abstract operations *draw()* and *getArea()*.
Square and Circle inherit from *Shape* and provide implementation for the polymorphic operations *Shape::draw()* and *Shape::getArea()*. All concrete subclasses *must* provide concrete draw() and getArea() operations, because they are abstract in the superclass.
A set of abstract operations is therefore a way to define a set of operations that *all* concrete subclasses **must** implement. This is known as a contract.

Clearly, the implementation of draw() and getArea() will be different for Square and for Circle. This is the essence of polymorphism - objects of different classes have operations with the *same* signature, but different implementations (different code).

Three main pillars of Object Oriented systems and OO programming languages:

1. Encapsulation
2. Inheritance
3. Polymorphism

Polymorphism allows you to send to objects of *different* classes the *same* message (a call to an operation) and have the objects respond appropriately.

If you send a message draw() to objects of the Square class, they will each draw a square, and if you send that same message to objects of class Circle, they will each draw a circle. The objects seem to exhibit some kind of intelligence.

### Polymorphism Example &sect; 10.4.1 ###

Here is an example of polymorphism in action. Suppose that you have a Canvas class that maintains a collection of Shapes. Although this is a somewhat simplified picture, many graphics systems actually work very much in this way. 
The model for this simplified system is shown in Figure 10.8 (p. 213).

Now, you know that you can;t create an instance of Shape because it is abstract - but, according to the substitutability principle, you can create instances of its concrete classes and substitute these anywhere a Shape is called for.

So, although Figure 10.8 shows that objects of type Canvas contain collections of many Shape objects, the only objects that you can actually put in the collection are instances of concrete classes of Shape because Shape itself is abstract and **can't** be instantiated. In this case, there are two concrete subclasses, Circle and Square, so the collection may contain Circle objects and Square objects.

In Figure 10.9 (p. 214), we have created an object model from the class diagram in Figure 10.8. This object model shows that a :Canvas object holds a collection of four *Shape* objects s1, s2, s3 and s4, where s1, s3 and s4 and circles and s2 is an object of class Square.

What happens when the :Canvas object iterates over this collection and sends each object in the collection the message draw()? Well, not surprisingly, each object does the right thing - Square objects draw squares and Circle objects draw circles. It is the object's class that determines *what* the object draws.

All objects of the same class will react the same way when the same operation is invoked, but the results may be different: this is because even though all Circle objects will draw themselves the same way (the meaning of the operation remains the same), the actual output depends on the value of each circle's radius - circles of different radii will cause the drawing of circles of different sizes to be drawn. 

## Advanced Generalization &sect;10.5 ##

In this section, we look at two advanced aspects of generalization: generalization sets and powertypes. The notion of generalization sets can be quite useful. However, you will use powertypes rarely, if at all.

### Generalization Sets &sect;10.5.1 ###

You can organize the subclasses of any superclass into one or more generalization sets.

A generalization set groups subclasses according to a particular rule, or basis of specialization. Here's an example.
Figure 10.11 (p. 216) illustrates that the superclass *Shape* has many subclasses. On examination of these subclasses, you can see that there are two distinctly different groups of *Shapes*: two-dimensional shapes and three-dimentional shapes. 

You can indicate the partitioning of subclasses on a class diagram by associating each group of shapes with a different generalization set as illustrated in Figure 10.12 (p. 216). 

Generalization sets can have constraints applied to them. These constraints determine whether the sets are:

- {complete} - the subclasses in the generalization set cover *all* the possibilities. 
- {incomplete} - there may be subclasses other than those in the generalization set. The generalization set twoDShapes is clearly {incomplete} as there are potentially very many twoDShapes.
- {disjoint} - an object can be an instance of *one and only one* of the members of the generalization set. This is by far the most common case.
- {overlapping} - an object can be an instance of more than one of the members of the generalization set. This is quite uncommon as it requires multiple inheritance.


---

[cls-shape-gen]: http://yuml.me/f83ebfc6
<!--
// Shape Generalization
[Shape]^-[Triangle]
[Shape]^-[Circle]
[Shape]^-[Square]
-->

[cls-shape-inher]: http://yuml.me/043de243
<!--
// Shape inheritance
[Shape|origin;width;height|draw();getArea();getBoundingArea()]^-[Circle|radius|]
[Shape]^-[Square]
-->

[cls-shape-override]: http://yuml.me/e05cff2a
<!--
// Shape overriding
[Shape|origin;width;height|draw();getArea();getBoundingArea()]^-[Circle|radius|draw();getArea()]
[Shape]^-[Square||draw();getArea()]
-->

[cls-abs-wrong]: http://yuml.me/26e26d55
<!--
// Abstraction wrong
[Vehicle]^-[JaguarXJS]
[Vehicle]^-[Truck]
-->

[cls-abs-right]: http://yuml.me/adcab304
<!--
// Abstraction correct
[Vehicle]^-[Car]
[Car]^-[JaguarXJS]
[Vehicle]^-[Truck]
-->

[cls-abs-right2]: http://yuml.me/ae9f45d4
<!--
// Abstraction correct
[Vehicle]^-[Car]
[Car]^-[JaguarXJS]
[Vehicle]^-[Truck]
[Truck]^-[FordF150]
-->

[cls-shape-abstract]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/class-shape-abstract.png

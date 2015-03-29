# COMP 1215 - Object Oriented Systems Analysis #
**Week 8 Notes - Essential OO Concepts**

**References**

* Course Textbook

Book Chapters 6, 7, 9, 10



## Generalization &sect; 10.2

Generalization is a relationship between a more general element and a more specific element, where the more specific element is *entirely consistent* with the more general element, but contains more information.

### Class generalization &sect; 10.2.1
You are already familiar with the notion of general things such as a tree, and then more specific things such as an oak tree, which is a specific type of tree.

Generalization applies to all classifiers - we've seen it applied to use cases and actors, and now you'll see how it is applied to classes.

In Figure 10.2 (p.207), we have a class called Shape - this is clearly a very general notion! From that, we derive children, subclasses, descendants (all these terms are in common use) that are more specific variants of the general idea of Shape. By the substitutability principle, we can use an instance of any of these subclasses *anywhere* an instance of the Shape superclass is expected.

As you will see when we look at the detailed attributes and operations of these classes, we could arrive at the above hierarchy in one of two ways: through either a process of specialization or a process of generalization.

In specialization, we would first identify the general concept of Shape in analysis, then specialize this into specific types of shapes.

In generalization, we would identify the more specialized Square, Circle and Triangle in analysis and then notice that they all have common features that we could factor out into a more general superclass.

In out experience, it is wise to train oneself to see the more general casse as early in the analysis process as possible.

## Class inheritance &sect; 10.3
When you arrange classes into a generalization hierarchy as shown in Figure 10.2  (p. 207)you implicitly have inheritance between whereby the subclasses inherit all the features of their superclass. To be more specific, subclasses inherit

- attributes
- operations
- relationships
- constraints

Subclasses can also add new features and override superclass operations.

### Overriding &sect; 10.3.1
In the example in Figure 10.3 (p.208), the Shape subclasses Square and Circle inherit all of the attributes, operations and constraints from the Shape superclass. It means that although you don;t see thesse features in the subclass representations, they are implicitly there. We say that Square and Circle are 'types of Shape'.

Notice that the operations draw() and getArea() defined in Shape can in no way be appropriate for the subclasses. The default draw() operation that both subclasses have inherited from their parent clearly won't do. In fact, this operation may not draw anything at all as, after all, what should a Shape look like? The same applies to getArea(). How do you calculate the area of a shape?

This clearly points to the need for the subclasses to be able to change superclass behaviour. Square and Circle need to implement their own draw() and getArea() operations that override the default operations supplied by their parent and provide a more appropriate behaviour.

Figure 10.4 (p. 209) shows this in action: the subclasses Square and Circle have provided their own draw() and gerArea() operations that have the appropriate behaviours.

Square::draw(g: Graphic) - draws a square.
Square::getArea(): int - calculates and returns the area of the square.
Circle::draw(g: Graphics) - draws a circle.
Circle::getArea(g: Graphics) - calculates and returns the area of the circle.

To override a superclass operation, a subclass **MUST** provide an operation with *exactly* the same signature as the superclass operation it wishes to override. UML defines operation signature as the operation name, its return type the types of all the parameters, listed in order. Note that Java has a slightly different definition of operation signature where the return type is *not* part of the signature. 

### Abstract operations and classes &sect; 10.3.2

The draw() operation in class Shape can't possibly have a sensible implementation that can be coded as we don't know how "shapes" should be drawn - the concept of "drawing a shape" is too abstract to have any concrete implementation. In this situation, you can specify that an operation lacks implementation (in the superclass) by making it an abstract operation. In UML, you simply write the operation name in italics.

When you think about it, a class with one or more abstract operations is incomplete as there are operations that don;t have implementation (i.e. no code). This means that you can't instantiate such classes, and they are therefore known as abstract classes. You write the class name in italics to show that it is abstract.

Both our subclasses provide the missing information - their own implementation of the two methods draw() and getArea() - this makes them complete classes that can instantiated. Classes that can be instantiated are called concrete classes.

The operation getBoundingArea() in Figure 10.5 (p. 210) is a *concrete* operation of Shape because the bounding area of every kind of Shape is calculated in exactly the same way - it is the width of the shape multiplied by its height.

There are a couple of big advantages of using abstract classes and operations:

- You can define a set of abstract operations in the abstract superclass that **must** be implemented by all Shape subclasses. You can think of this as defining a 'contract' that all kinds of Shape subclasses *must* implement.
- You can write code to manipulate Shapes and then substitute Circle, Square, and other Shape subclasses as appropriate. According the the substutitability principle, code written to manipulate Shapes should work for all Shape subclasses.

### Level of abstraction &sect; 10.3.3

Before we get to Polymorphism, it is a good ides to understand something about levels of abstraction. What's wrong with the model in Figure 10.6 (p. 211)?

The answer is "levels of abstraction". A generalization hierarchy defines a set of levels of abstraction from the most general at the top to the most specific at the bottom. You should always try to maintain a uniform level of abstraction at each level of the generalization hierarchy. In the example in Figure 10.6, we have *not* achieved this. A Jaguar XJS is a *type* of car. Clearly this is a lower level of abstraction than Truck. You can fix this model quite easily by inserting a Car superclass between Vehicle and Jaguar XJS.

### Multiple inheritance &sect; 10.3.4

UML allows a class to have more than one direct superclass. Thsi is called *multiple inheritance*. The subclass inherits from *all* its direct superclasses.

Multiple inheritance is usually considered to be a design issue - we defer this until Section 17.6.2.

## Polymorphism &sect; 10.4

Polymorphism means "many forms". A polymorphic operation is one that has meny implementations. You have already seen two polymmorphic operations in the Shape example. The abstract operations sraw() and getArea() in the Shape class have two different implementations - an implementation in the Square class and one in the Circle class.

Figure 10.7 (p. 212) illustrates polymorphism perfectly.
We define an abstract *Shape* class with abstract operations *draw()* and *getArea()*.
Square and Circle inherit from *Shape* and provide implementation for the polymorphic operations *Shape::draw()* and *Shape::getArea()*. All concrete subclasses *must* provide concrete draw() and getArea() operations, because they are abstract in the superclass.
A set of abstract operations is therefore a way to define a set of operations that *all* concrete subclasses **must** implement. This is known as a contract.

Clearly, the implementation of draw() and getArea() will be different for Square and for Circle. This is the essence of polymorphism - objects of different classes have operations with the *same* signature, but different implementations (different code).

Encapsulation, inheritance and polymorphims are the "three pillars" of OO.

Polymorphism allows you to send to objects of *different* classes the *same* message (a call to an operation) and have the objects respond appropriately.

If you send a message draw() to objects of the Square class, they will each draw a square, and if you send that same message to objects of class Circle, they will each draw a circle. The objects seem to exhibit some kind of intelligence.

### Polymorphism example &sect; 10.4.1
Here is an example of polymorphism in action. Suppose that you have a Canvas class that maintains a collection of Shapes. Although this is a somewhat simplified picture, many graphics systems actually work very much in this way. 
The model for this simplified system is shown in Figure 10.8 (p. 213).

Now, you know that you can;t create an instance of Shape because it is abstract - but, according to the substitutability principle, you can create instances of its concrete classes and substitute these anywhere a Shape is called for.

So, although Figure 10.8 shows that objects of type Canvas contain collections of many Shape objects, the only objects that you can actually put in the collection are instances of concrete classes of Shape because Shape itself is abstract and **can't** be instantiated. In this case, there are two concrete subclasses, Circle and Square, so the collection may contain Circle objects and Square objects.

In Figure 10.9 (p. 214), we have created an object model from the class diagram in Figure 10.8. This object model shows that a :Canvas object holds a collection of four *Shape* objects s1, s2, s3 and s4, where s1, s3 and s4 and circles and s2 is an object of class Square.

What happens when the :Canvas object iterates over this collection and sends each object in the collection the message draw()? Well, not surprisingly, each object does the right thing - Square objects draw squares and Circle objects draw circles. It is the object's class that determines *what* the object draws.

All objects of the same class will react the same way when the same operation is invoked, but the results may be different: this is because even though all Circle objects will draw themselves the same way (the meaning of the operation remains the same), the actual output depends on the value of each circle's radius - circles of different radii will cause the drawing of circles of different sizes to be drawn. 

## Advanced generalization &sect; 10.5

In this section, we look at two advanced aspects of generalization: generalization sets and powertypes. The notion of generalization sets can be quite useful. However, you will use powertypes rarely, if at all.

###Generalization sets &sect; 10.5.1

You can organize the subclasses of any superclass into one or more generalization sets.

A generalization set groups subclasses according to a particular rule, or basis of specialization. Here's an example.
Figure 10.11 (p. 216) illustrates that the superclass *Shape* has many subclasses. On examination of these subclasses, you can see that there are two distinctly different groups of *Shapes*: two-dimensional shapes and three-dimentional shapes. 

You can indicate the partitioning of subclasses on a class diagram by associating each group of shapes with a different generalization set as illustrated in Figure 10.12 (p. 216). 

Generalization sets can have constraints applied to them. These constraints determine whether the sets are:

- {complete} - the subclasses in the generalization set cover *all* the possibilities. 
- {incomplete} - there may be subclasses other than those in the generalization set. The generalization set twoDShapes is clearly {incomplete} as there are potentially very many twoDShapes.
- {disjoint} - an object can be an instance of *one and only one* of the members of the generalization set. This is by far the most common case.
- {overlapping} - an object can be an instance of more than one of the members of the generalization set. This is quite uncommon as it requires multiple inheritance.






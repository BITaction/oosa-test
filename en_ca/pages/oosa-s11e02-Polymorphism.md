# Generalization & Polymorphism #

> Inheritance with polymorphism is a feature that OO programming languages provide to support class generalization hierarchies.
> 

## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;10 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;10.6 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Define polymorphism
	* Draw and interpret class models with polymorphic operations
	* Draw and interpret related object models and explain the use of polymorphic operations on objects
	* Identify and define the 3 main pillars of Object Oriented systems

## Polymorphism &sect;10.4 ##

- Polymorphism means "many forms"
- A polymorphic operation is one that has many implementations
- We have seen polymorphic operations in the Shape example
- The abstract operations *draw()* and *getArea()*a in the Shape class have two different implementations
- An implementation in the Square class and an implementation in the Circle class

**NOTE**: Study Figure 10.7 and examples provided in the notes.

- We define an abstract *Shape* class with abstract operations *draw()* and *getArea()*
- Square and Circle inherit from *Shape* and provide implementations for polymorphic operations *Shape::draw()* and *Shape::getArea()*
- All concrete subclasses *must* provide concrete draw() and getArea() operations
- Square and Circle are concrete classes, thus provide implementations for these operations

**NOTE**: You can also override concrete operations instead of abstract operations to provide polymorphism. One must be careful with this since you are changing the implementation of an inherited operation.

Essence of Polymorphism: 

- Clearly, the implementation of draw() and getArea() will be different for Square and for Circle
- Objects of different classes have operations with the *same* signature, but different implementations (different code)
- Substitutability principle allows us to consider abstract Shapes and substitute concrete Squares and Circles
- All Shapes support draw() and getArea() and all substitutes will have concrete implementations for these operations
- Polymorphism allows you to send the *same* message to objects of *different* classes and have each respond appropriately

Three main pillars of OO systems and OO programming languages are:

1. Encapsulation
2. Inheritance
3. Polymorphism

### Polymorphism Example &sect; 10.4.1 ###

- A Canvas maintains a collection of Shapes

See Figure 10.8

![][cls-shape-canvas]

- You cannot create an instance of Shape because it is abstract
- You can create instances of its concrete classes and substitute these anywhere a Shape is expected
- A Canvas contains a collection of many Shape objects
- Shape itself is abstract and **can't** be instantiated
- Thus, the only objects you can link to a Canvas are instances of concrete classes of Shape
- That is, Circle and Square concrete classes, so the collection may contain Circle objects and Square objects

See Figure 10.9

![][obj-canvas-shapes]

- This is an object model from the class diagram in Figure 10.8
- This object model shows that a :Canvas object holds a collection of four *Shape* objects s1, s2, s3 and s4
- s1, s3 and s4 are Circle objects
- s2 is a Square object
- the :Canvas object can iterate over its collection and send each object the message draw()
- each object does the right thing - Square objects draw squares and Circle objects draw circles
- the object's class determines *what* the object draws (by the implementation in its class)

---

[cls-shape-canvas]: https://dl.dropboxusercontent.com/u/698657/oosa-wiki/uploads/images/class-shape-canvas.png

[obj-canvas-shapes]: https://dl.dropboxusercontent.com/u/698657/oosa-wiki/uploads/images/obj-canvas-shape.png

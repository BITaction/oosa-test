# Polymorphism #

> Inheritance with polymorphism are features that OO programming languages provide to support class generalization hierarchies.
> 

## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;10 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;10.6 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* 
	* Identify and define the 3 main pillars of Object Oriented systems

## Polymorphism &sect;10.4 ##

Polymorphism means "many forms". A polymorphic operation is one that has many implementations. You have already seen two polymorphic  operations in the Shape example. The abstract operations draw() and getArea() in the Shape class have two different implementations - an implementation in the Square class and one in the Circle class.

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

---


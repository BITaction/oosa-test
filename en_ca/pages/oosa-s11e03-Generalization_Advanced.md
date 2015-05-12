# Generalization Advanced Constructs #


## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;10 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;10.6 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* 

## Advanced Generalization &sect;10.5 ##

In this section, we look at two advanced aspects of generalization: generalization sets and powertypes. The notion of generalization sets can be quite useful. However, you will use powertypes rarely, if at all.

### Generalization Sets &sect;10.5.1 ###

You can organize the subclasses of any superclass into one or more generalization sets.

A generalization set groups subclasses according to a particular rule, or basis of specialization. Here's an example.
Figure 10.11 (p. 216) illustrates that the superclass *Shape* has many subclasses. On examination of these subclasses, you can see that there are two distinctly different groups of *Shapes*: two-dimensional shapes and three-dimensional shapes. 

You can indicate the partitioning of subclasses on a class diagram by associating each group of shapes with a different generalization set as illustrated in Figure 10.12 (p. 216). 

Generalization sets can have constraints applied to them. These constraints determine whether the sets are:

- {complete} - the subclasses in the generalization set cover *all* the possibilities. 
- {incomplete} - there may be subclasses other than those in the generalization set. The generalization set twoDShapes is clearly {incomplete} as there are potentially very many twoDShapes.
- {disjoint} - an object can be an instance of *one and only one* of the members of the generalization set. This is by far the most common case.
- {overlapping} - an object can be an instance of more than one of the members of the generalization set. This is quite uncommon as it requires multiple inheritance.


---


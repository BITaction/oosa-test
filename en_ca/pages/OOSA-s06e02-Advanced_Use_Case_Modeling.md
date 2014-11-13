# COMP XXXX - Object Oriented Systems Analysis #

---

## Week 6 Notes - Advanced Use Case Modeling

## References

- [Course Textbook][textbook]

---

# Chapter 5

## Actor generalization &sect;5.2

When two or more actors interact with the same use cases - or with most of them - we can simplify the diagram by using the generalization symbol. See Figure 5.3 (p.97) and Figure 5.3 (p.98) for an example.

Note that the parent actor (purchaser) is abstract because it represents behaviour common to both children; there is no actual 'purchaser' actor. The name of an abstract actor is written in *italics*.

## Use case generalization &sect;5.3

Use case generalization is used when you have one or more use cases that are really specializations of a more general use case.

The child use case represents more specific forms of the parent. 

The child use case automatically inherit *all* features from its parent!

The child use case may:

- add new features.
- override (change) inherited features.

See Table 5.1 (p.99) for restrictions to overriding parent features. 

## &laquo;include&raquo; &sect;5.4

This relationship indicates that the **base** use case ***MUST always*** include the functionality of the **inclusion** use case pointed to by the arrow. See Figure 5.7.

The base use case will execute until the point of inclusion is reached, then execution passes to the included use case. Upon completion, execution passes back to the base use case again.

The base use cases are **NOT** complete without the inclusion use case!

See Figure 5.8 (p.104) and Figure 5.9 (p. 105) for an example of how to write this into use case specifications.


## &laquo;extend&raquo; &sect;5.5

This relationship provides a way to add new behaviour to an existing use case.

The &laquo;extend&raquo; relationship implies that the base use case may optionally use the extension use case. See Figure 5.10 (p.105) for an example.

With the &laquo;extend&raquo; relationship, the base case does not know *anything* about the extension use cases. It only provides hooks for them.

The base use case is perfectly complete without the extension use cases.

### The extension use case &sect;5.5.1

Extension use cases are *generally* not complete use cases, but just consist of one or more behaviour fragments known as *insertion segments*.

Some rules apply:

- the &laquo;extend&raquo; relationship must specify one or more extension points in the base use case.
- The extension use case must have the same number of insertion segments as there are extension points in the &laquo;extend&raquo; relationship.
- It is legal for two extension use cases to &laquo;extend&raquo; the same base use case at the same extension point. If it happens, the order in which the extensions execute is indeterminate.

See Figure 5.12 (p.107) for an example.

### Multiple insertion segments &sect;5.5.2

There can be multiple extension segments in an extension use case.

They require clear labels. See Figure 5.13 (p.108).

### Conditional extensions &sect;5.5.3

Exten

## When to use advanced features &sect;5.6

## Hints and tips for writing use cases &sect;5.7

### Keep use cases short and simple &sect;5.7.1

### Focus on the *what*, not the *how* &sect;5.7.2

### Avoid functional decomposition &sect;5.7.3



[textbook]: http://www.amazon.ca/UML-Unified-Process-Object-Oriented-Addison-Wesley/dp/B00E286B8G/ref=sr_1_3?ie=UTF8&qid=1403202307&sr=8-3&keywords=uml+2+and+unified+process "Text book"
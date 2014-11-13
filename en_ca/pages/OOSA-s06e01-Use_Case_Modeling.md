# COMP XXXX - Object Oriented Systems Analysis #

---

## Week 6 Notes - Use Case Modeling

## References

- [Course Textbook][textbook]

---

# Chapter 4


## Use Case Modeling &sect;4.2
This is a form of requirements engineering.
It is a way of eliciting requirements that is different from - and complementary to - the traditional way presented in the previous chapter.

Typical process:

- Find a candidate system boundary.
- Find the actors.
- Find the use cases:
    - specify the use case.
    - identify key alternative flows. 
- Iterate until use cases, actors and system boundary are stable.

The result is the use case model which has 4 components:

1. **System boundary** - a box drawn around the use cases to denote the edge (or boundary) of the system. This is called the ***subject*** in UML 2.
- **Actors**
- **Use cases**
- **Relationships**

## UP Activity: Find Actors and Use Cases &sect;4.3
This focuses on the activity *Find Actors and Use Cases* from section &sect;3.2.

Look at the inputs. See Figure 4.2 (p.70):

- the Business model
- the Requirements model
- the Feature list

### The subject (system boundary) &sect;4.3.1
We have to decide what is part of the system and what isn't.

The subject is defined by:

- **who** or **what** uses the system.
- what **specific benefits** the system offers to those actors (i.e. the use cases)

### What are actors? &sect;4.3.2
An actor specifies a specific role taken by an external entity when interacting ***directly*** with your system.

An actor may be a person, an external system, or a piece of hardware that touches the boundary of your system.

Actors are **always** external to the system!

When identifying actors, many questions have to be considered - see section &sect;4.3.2.1 for details

Time is often an actor - such as when a system performs an automated backup every evening.

### What are use cases? &sect;4.3.3

A use case is something an actor wants the system to do. It is a "case of use" of the system by a specific actor. 

#### Identifying use cases &sect;4.3.3.1

Start with a list of actors then consider how each actor is going to use the system.

List of some useful questions you can ask when trying to identify use cases:

- What functions will a specific actor want from the system?
- Does the system store and retrieve information? If so, which actors trigger this behaviour?
- What happens when the system changes state (i.e. system start and stop)? Are any actors notified?
- Does any external event affect the system? What notifies the system about those events?
- Does the system interact with other - external - systems?
- Does the system generate any reports?

#### The use cases diagram &sect;4.3.3.2

See Figure 4.6 (p.75)

The use case diagram is a graphical representation that includes:

- the subject, represented by a box labeled with the name of the subject. It represents the boundary of the system.
- the use cases shown inside the subject box.
- actors shown outside the subject box. 
- association lines between actors and use cases that indicate that they interact in some way.

### The project glossary &sect;4.3.4

The project glossary may be on of the most important project artifacts.

The project glossary:

- provides a dictionary of key business terms and definitions.
- should be understandable by everyone in the project - including all stakeholders.
- must resolve: 
    - synonyms - different words that mean the same thing.
    - homonyms - same words meaning different things to different people.

## UP Activity: Detail a Use Case &sect;4.4

After having created a use case diagram with actors and key use cases, we need to detail each use case in turn.

The output is a more detailed use case that consists of at least a use case name and a use case specification (description). See summary diagram in Figure 4.7 (p. 78).

## Use Case Specification &sect;4.5

There is NO UML standard for use case specification.

Figure 4.8 (p. 78) details the basic parts of a simple use case specification.

### Use case name &sect; 4.5.1

- There is no UML standard for use case name.
- In this course we always write use case names in UpperCamelCase.
- Use cases represent actions and their names should **always** start with or include a verb - such as PaySalesTax. 
- Shorter names are better, as long as they are descriptive.

### Use case ID &sect; 4.5.2

Use case names should all be unique, but they may change over time. 

Use case IDs often consist of letters representing the sub-system of components they document - i.e. **IS-17** for use case **17** of the **I**nventory **S**ystem.

For that reason, each use case must have a unique ID that will not change over time.

### Brief description &sect; 4.5.3

A single paragraph that summarizes the goal of the use case.

### Actors &sect; 4.5.4

Actors seen from the perspective of the use case. 

This includes 2 types of actors:

1. **primary actors** - they actually trigger the use case.
2. **secondary actors** - they interact with the use case once it has been triggered.

### Pre-conditions and post-conditions &sect; 4.5.5

1. Pre-conditions are constraints that will prevent the use case from starting - until they are satisfied. 
    - They **MUST** all be true before the use case is allowed to start.
    - They should almost always be verifiable by program - not in someone's head.
2. Post-conditions specify what **MUST** be true after the use case completes successfully.

If a use case doesn't have any pre- or post-conditions, then it is best to write 'None' in the appropriate spaces to indicate that they have been considered. Don't leave the spaces for them blank - that is ambiguous.

### Main flow &sect; 4.5.6

This represents the main sequence of events for a use case when everything goes well - i.e. the 'perfect world'.

It is also knows as:

- the 'Happy path'
- the 'typical course of events'

The main flow **ALWAYS** starts with the primary actor doing something to trigger the use case.

Deviations to this flow can be simple (see section &sect;4.5.6.1) or they can be complex and require writing alternative flows (see section &sect;4.5.7).

Remember that time can be an actor!

#### Simple deviations: branching within a flow &sect; 4.5.6.1

We will use an approach that includes simple deviations within the main flow without having to write separate alternative flows.

#### Simple deviations: Keyword IF &sect; 4.5.6.2

Use the keyword IF to indicate a branch in the flow. It has to be associated with a Boolean expression such as 'If the user types in a new quantity', which is either true or false. See sample in Figure 4.9 (p.83).

#### Simple deviations: repetition within a flow &sect; 4.5.6.3

Sometimes we have to document the repetition of an action within a flow of events. It is rare, when when required, we need a strategy to deal with it.

#### Simple deviations: Repetitions 1: Keyword FOR &sect; 4.5.6.4

The keyword For can be used to indicate repetition - see Figure 4.10 (p.84) for an example.

#### Simple deviations: Repetitions 2: Keyword WHILE &sect; 4.5.6.5

The keyword While can be used to document a sequence of events that must be repeated while a Boolean expression is true. See Figure 4.11 (p.85) for an example.

### Alternative flows &sect; 4.5.7

Each use case MUST have a main flow and may have many alternative flows. 

These alternative paths typically capture errors, branches and interrupts to the main flow. See the diagram in Figure 4.12 (p.86).

Alternative flows can be documented separately or be appended to the main flow.

In this course, we will document them separately. See Figures 4.13 and 4.14 (p.87) for an example.

#### Finding alternative flows &sect; 4.5.7.1

While inspecting the main flow, look for:

- possible alternatives to the main flow.
- errors that might be raised in the main flow.
- interrupts that might occur at a particular point in the main flow.
- interrupts that might occur at *any* point in the main flow.

#### How many alternative flows? &sect; 4.5.7.2

Even though there may be *many* alternative flows, they should be limited to the necessary minimum. This can be done through the following 2 strategies:

1. pick the most important alternative flows and document them.
2. Where there are groups of alternative flows that are all very similar, document one of them and add notes describing how the others differ from that one.

## Requirements tracing &sect;4.6

when you have a requirements model and a use case model, you have to relate the two in order to find out if there is anything in the requirements model that is missing from the use case model and vice versa.

There are CASE tools that provide the necessary functionality.

If you don't have such a tool, things must be done manually - usually using spreadsheets. See an example in Table 4.2 (p.91).

## When to apply Use Case modeling &sect;4.7

- Use cases capture functional requirements.
- They are not effective at capturing non-functional requirements.
- They are the best choice when the system:
    -  is dominated by functional requirements.
    -  has many types of users (there are many actors).
    -  has many interfaces (there are many actors).
- Use cases would be a poor choice when the system:
    -  is dominated by non-functional requirements.
    -  has few users.
    -  has few interfaces.


[textbook]: http://www.amazon.ca/UML-Unified-Process-Object-Oriented-Addison-Wesley/dp/B00E286B8G/ref=sr_1_3?ie=UTF8&qid=1403202307&sr=8-3&keywords=uml+2+and+unified+process "Text book"
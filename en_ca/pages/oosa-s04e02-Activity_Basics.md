# Activity Diagram Basics #

> Activity diagrams are "OO flowcharts"
> 

## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;14 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;14.11 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Define the basic constructs of activity diagrams
	* Identify where activity diagrams are best used
	* Define activities
	* List and define categories of nodes and edges in activities
	* Explain activity semantics via tokens and conditions

## What are Activity Diagrams? &sect;14.2 ##

> They allow you to model some process as an activity
> 

- Activities are a collection of _nodes_ connected by _edges_
- Nodes can be an action, decision, merge, initial, final, object, etc.
- Edges can be a control flow, object flow
- An activity can be attached to _any_ modeling element to model its behavior
- Activities are typically attached to:
	* Use Cases
	* Class Operations/Methods
	* Interfaces
	* Components
- Activities can model an entire system as a whole or high-level business processes
- A good activity diagram will:
	* focus on communicating an aspect of a system's dynamic behavior
	* be at the correct level of abstraction for the target audience
	* contain a minimum amount of information necessary to make the point
	* be as clear and as simple as possible

> ### READ MORE:
> - High level business processes are often modeled using BPMN
> - [OMG Business Process Model and Notation (BPMN) Specification][bpmn-omg]
> - [OMG BPMN Organization Site][bpmn-org]

## Activity Diagrams and UP &sect;14.3 ##

> Activity diagrams are general purpose mechanisms for modeling behavior
> 

- There is no single specific place where activity diagrams fit into UP
- Use them wherever they add value to describing behavior of a model
- They are fairly easy for stakeholders to understand (as long as they are fairly simple)
- They are useful to model:
	* early stages of analysis when little is known about structure
	* flow of use cases that are easy for stakeholders to understand
	* flow between use cases
	* details of operations in classes
	* details of an algorithm
	* business process without the complexities of BPMN

## Activities &sect;14.4 ##

> Activities are networks of nodes connected by edges
> 

There are three categories of nodes:

Node | Purpose
-----|--------
action node | discrete units of work within an activity
control node | controls the flow through an activity
object node | represent objects used within an activity

There are two categories of edges:

Edge | Purpose
-----|--------
control flow | represents the flow of control through an activity
object flow | represents the flow of objects through an activity

- See Figure 14.2 for example activity: `Send Letter`
- See Figure 14.3 and Figure 14.4 for example of activity representing a use case
- Below is an example activity: `Replace ID Card`

![][activity-addpic]

- Activities start with a single initial node
- They contain several action nodes
- They represent a certain flow of control
- Decision and merge nodes can change the flow of control
- Activities end with one final node (sometimes more than one in different places)

## Activity Semantics &sect;14.5 ##

> Activity diagrams are based on [Petri Nets][petri-nets] and model behavior by using a _token game_ semantic description
> 

- Tokens in an activity diagram can represent:
	* flow of control
	* an object
	* some other data
- The state of an activity is determined by the disposition of tokens
- Tokens move from source node to target node across an edge
- Movement of tokens can be subject to conditions
- Movement occurs when all conditions are satisfied
- We will refer to tokens and satisfying conditions when evaluating semantics of activity diagrams
- Our discussion is about the semantics of an activity and not about its implementation

> ### In Class Activity
> - Explain activity `Replace ID Card` as a movement of tokens based on conditions
> 

## Activity Partitions &sect;14.6 ##

> Partitions represent a high-level grouping of related actions
> 

- Activity partitions are sometimes referred to as _swimlanes_ (a leftover from UML 1.x)
- Partitions can be vertical or horizontal
- Partitions have a name, where you define its semantics
- Partitions are commonly used to represent:
	* locations where actions occur
	* organization units
	* roles of responsibility for actions
- Ensure added complexity of partitions offers better understanding of behavior

> ### In Class Activity
> - Reproduce activity `Course production` in Figure 14.6 in the modeling tool
>

## Action Nodes &sect;14.7 ##

> We consider action nodes with one or more input edge and only one output edge
> 

- Action nodes do something, describe them with a _verb phrase_
- An action node will execute when:
	* there is a token simultaneously on each input edge __AND__
	* the input tokens satisfy the action node preconditions (if defined)
- After an action node executes, if postconditions are satisfied, an output token is sent on the output edge
- __NOTE__: Figure 14.9 shows multiple output edges, but we will allow only one output control flow edge.

Four types of action nodes:

Type | Purpose
-----|--------
Call Action | Invokes an activity, behavior, or operation (see Figure 14.11)
Send Signal | Send a signal asynchronously (does not wait)
Accept Event | Waits for event and offers it on output edge when received
Time Event | Accepts a time event; Generates a time event (see Figures 14.12 & 14.13)

- We commonly use behavior and activity call action nodes
- We will also make use of time event action nodes

## Control Nodes &sect;14.8 ##

> They manage the flow of control within an activity
> 

- See Table 14.2 for summary of control nodes

Name | Purpose
-----|--------
Initial node | Starts an activity
Activity final node | Ends an activity
Flow final node | Ends a particular flow; other flows are unaffected
Decision node | Directs flow to the single guarded edge that evaluates to `true`
Merge node | Combines several flows into a single output flow
Fork node | Splits flow into several concurrent flows
Join node | Synchronizes concurrent flows into a single output flow

### Initial Node &sect;14.8.1 ###

- Initial nodes indicate where an activity starts
- If more than one initial node, then concurrent flows start simultaneously from each initial node
- There are other ways to start an activity without an initial node
- __NOTE__: Use a single initial node in your diagrams (use fork node to start concurrent flows)

### Final Nodes &sect;14.8.1 ###

- Activity final node stops _all_ flows within an activity
- Several activity final nodes can be used and first one activated terminates the activity
- Flow final node stops only a single flow; the other flows continue

### Decision Node &sect;14.8.2 ###

- One input edge; two or more output edges
- Each output edge is protected by a [guard condition]
- Guard conditions must be _mutually exclusive_
- A token on the input edge is provided to _all_ output edges
- The token will only traverse the _one_ edge whose guard condition evaluates to `true`
- See Figure 14.14

### Merge Node &sect;14.8.2 ###

- Two or more input edges; one output edge
- Combines incoming flows into a single outgoing flow
- A token on any input edge is provided to the output edge
- __NOTE__: Figure 14.16 shows a shorthand that you should not use

### Fork and Join Nodes &sect;14.8.3 ###

- Used to create multiple concurrent flows
- Similar to thread processing discussed in programming languages
- Fork node splits a flow into multiple concurrent flows
- Join node synchronizes multiple concurrent flows into a single flow
- Fork node:
	* one input edge; two or more output edges
	* token on incoming edge is duplicated and provided on all outgoing edges simultaneously
	* an outgoing edge can have a [guard condition]
	* tokens only traverse edges that evaluate to true
	* a token will traverse an edge without a guard condition
- Join node:
	* multiple input edges; one output edge
	* waits for a token on _all_ incoming edges and then provides a token on outgoing edge
- See Figure 14.17

![][activity-product]

- Check token availability at join nodes to ensure activities don't hang
- Remember join nodes wait for a token on _all_ input edges before proceeding

## Object Nodes &sect;14.9 ##

> They indicate that instances of a classifier are available and object flows illustrate the movement of objects in an activity
> 

- Object nodes are labelled with a classifier name (e.g., `Student`)
- Object nodes represent some instance of that classifier (e.g., some student)
- The object instances are created/consumed/modified by action nodes
- Input and output edges of an object node are _object flows_
- A token received on an input edge is offered to all output edges simultaneously
- Output edges _compete_ for the token
- There is only one token and the first edge to accept it gets it
- __NOTE__: Object node semantics can be very interesting. Create object nodes with maximum one input edge and maximum one output edge.

> ### In Class Activity
> - Reproduce activity `Product process` in Figure 14.19 in the modeling tool
>

### Object State &sect;14.9.2 ###

- Object nodes can represent instances in a particular state
- State is shown within [square brackets] and provides a helpful description of the object state
- See Figure 14.22 for example

> ### In Class Activity
> - Enhance activity `Product process` in Figure 14.19 with additional object nodes and state
> - Manufacture the new product that will be sold
> - Think about other objects and state that might be added
>

### Activity Parameters &sect;14.9.3 ###

- Object nodes can be shown as inputs and outputs of an activity
- They are drawn overlapping the activity frame
- Input object node parameters have have one or more output edges into the activity
- Output object node parameters have one or more input edges out of the activity
- See Figure 14.23 and study the narrative in terms of token passing

## Pins &sect;14.10 ##

> Pins can be useful to clean up messy object flows
> 

- A pin is an object node that represents one input to or output from an action node
- Input pins have exactly one incoming edge
- Output pin have exactly one outgoing edge
- Otherwise, they have same semantics as object nodes
- Compare Figures 14.24 & 14.25

---

[bpmn-omg]: http://www.omg.org/spec/BPMN
[bpmn-org]: http://www.bpmn.org

[petri-nets]: http://www.informatik.uni-hamburg.de/TGI/PetriNets/

<!--
(start)-><a>[picture missing]->(Take Picture)-><b>->(Replace IdCard)->(end), <a>[picture onfile]-><b>
-->
[activity-addpic]: http://yuml.me/56ae0bb7

<!--
(start)->(Design new product)->|a|,|a|->(Manufacture product)->|b|,|a|->(Market product)->|b|,|b|->(Sell product)->(end)
-->
[activity-product]: http://yuml.me/b0b086dc



# Analysis Workflow Overview #

> Analysis must focus on "what", design will focus on "how"
> 

## References ##

- [Course Textbooks](textbooks.md)
- Chapter &sect;6 of the UML 2 course textbook
- Additional references to external reading material as provided

## Learning Outcomes ##

- Section &sect;6.6 of the UML 2 course textbook (UMLUP)
- You will learn to:
	* Define the steps of analysis workflow in the Unified Process
	* Identify the UP phases where analysis mainly occurs
	* Explain the overlap and interaction between analysis and requirements workflows
	* List and explain the two main artifacts of the analysis workflow
	* Define the analysis metamodel
	* List the steps of the analysis workflow
	* List the rules of thumb for doing analysis modeling

## The Analysis Workflow  &sect;6.2 ##

Within the Unified Process:

- Main work in Analysis begins towards the end of the Inception phase
- Analysis is the main focus of the Elaboration phase (along with Requirements)
- Most activity in Elaboration is about creating models that capture desired behaviors of the system
- Analysis workflow overlaps to a great extent with the Requirements workflow
- One often analyzes requirements, which will clarify distortions and discover new ones

![][up-chart]

- Analysis workflow is aimed to produce an _analysis model_
- An analysis model focusses on _what_ the system should do; and leaves the details of _how_ it will do it to the design workflow
- Boundary between analysis and design can be vague
- Some design aspects naturally become part of the analysis model due to the nature of iterations that can involve all workflows of UP
- Some design aspects are determined early due to enterprise architectures and business goals

## Analysis Artifacts &sect;6.3 ##

In the Analysis workflow, 2 key artifacts are produced:

1. _analysis classes_ - these model key concepts in the business domain
2. _use case realizations_ - these illustrate how instances of classes can interact to realize system behavior specified by a use case

These artifacts are maintained in a metamodel:

<!-- Analysis metamodel
Could include diagram here to represent analysis metamodel from textbook
-->

- See Figure 6.3
- Analysis Model is a top level package
- Contains many other packages that organize the artifacts of the model into a meaningful structure

## Analysis Workflow Detail &sect;6.4 ##

![][up-analysis-workflow]

- The system Architect performs architectural analysis
- The Use Case Engineer will analyze each use case in turn
- The Component Engineer uses this to analyze each class and subsequently analyze related packages

## Analysis Model - Rules of Thumb &sect;6.5 ##

- A system of moderate size and complexity can probably contain 50 to 100 analysis classes
- It is **vitally important** to restrict yourself to ONLY those classes that are part of the vocabulary of the problem domain
- It is tempting to add design classes in the analysis model, but should be avoided
- Make the analysis model a concise and simple statement of the system structure and behavior

Some rules of thumb for analysis modeling:

- The analysis model is ALWAYS in the language of the business domain
- Create models that tell a story &rArr; whatever you add should add to the understanding
- Concentrate on capturing the big picture &rArr; don't get bogged down on the details of how
- Distinguish clearly between the problem domain and the solution domain
- Always try to minimize coupling &rArr; reduce associations between analysis classes
- Explore inheritance **if** there seems to be a natural and compelling hierarchy &rArr; inheritance is the strongest form of coupling between classes
- Make an analysis model that is useful to stakeholders &rArr; should be read and understood by all stakeholders
- Keep the analysis model simple!
- Inside every complex analysis model is a simple analysis model struggling to get out

---

[up-chart]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/up-chart.png

[up-analysis-workflow]: http://yuml.me/c67b2d76
<!-- steps for analysis workflow
(start)->(Perform architectural analysis)->(Analyze use cases)->(Analyze classes)->(Analyze packages)->(end)
-->
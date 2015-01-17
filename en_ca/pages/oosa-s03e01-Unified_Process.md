# The Unified Process (and other SEPs)

## References ##

[Course Textbooks](textbooks.md)

- Chapter &sect;2 of the UML 2 course textbook
- Additional references to external reading material as provided
- [Rational Unified Process Best Practices White Paper][rup-best]

## Learning Outcomes ##

- Section &sect;2.10 of the UML 2 course textbook (UMLUP)
- You will learn to:
	- Define a Software Engineering Process (SEP)
	- Give examples of historical and modern SEPs
	- Define the Unified Process and its role as a SEP
	- Define the workflows and phases of UP
	- Explain the differences between UP and RUP
	- Define Waterfall process along with its advantages and criticisms
	- Explain the Agile Manifesto
	- Identify various Agile approaches

## What is UP? &sect;2.2 ##

> UP is a modern SEP driven by user requirements
> 

![Purpose of SEP][sep-use]

- __SEP__ is an acronym for _Software Engineering Process_,
- SEP referred to as [Software Development Process (SDP)][sdp]
- A SEP defines the _who, what, when, and how_ of software development
- A SEP helps turn user requirements into working software (see Figure 2.2)
- The _Unified Software Development Process (USDP)_ is a SEP
- USDP is often referred to as just _Unified Process (UP)_
- So, UP is a SEP, a modern one that is driven to satisfy user requirements and manage risk
- UP provides the process framework for turning user requirements into working software

## What is RUP? ##

> RUP is a commercial SEP
> 

- __RUP__ is an acronym for [Rational Unified Process][rup], which is a commercial version of UP [maintained by IBM][rup-ibm]
- RUP extends UP in various ways such as process and terminology
- RUP and UP are more similar than different
- RUP describes a best practice process for developing software, and provides the tools and standards to help carry that out

> __READ MORE__: [RUP Best Practices White Paper][rup-best]
> 

## History of UP &sect;2.3 ##

> The development of UP is tied to the career work of Ivar Jacobson
> 

> __READ MORE__: [Ivar Jacobson][ivar] and [Ivar Jacobson International][ivar-intl]
> 

- Other major contributors were [Grady Booch][grady] and [James Rumbaugh][james]
- Jacobson, Booch, and Rumbaugh were affectionately known as "the Three Amigos"
- Refer to Figure 2.3

### 1967 ###

- The beginnings of UP can be traced to a _radical_ "divide and conquer" approach introduced at [Ericsson][ericsson] in 1967
- "divide and conquer" perceives a large complex system as set of subsystems with well defined interfaces that provide services
- The introduction of techniques at Ericsson became formally defined elements in UML years later

### 1980 ###

- CCITT released Specification Description Language (SDL), which was the first object-based visual modeling language
- SDL was designed to capture the behavior of telecommunication systems
- SDL-92 was a widely accepted object modeling standard

### 1987 ###

- Jacobson founded Objectory AB
- Objectory SEP formalized into 5 workflows (Requirements, Analysis, Design, Implementation, Test)
- Objectory SEP provided templates, documentation, and a tool that should be used to customize your specific software solution
- Objectory SEP was sold as a package to help turn requirements into working software

### 1995 ###

- Rational acquired Objectory AB and Jacobson went to work unifying Objectory SEP with process-related work already done at Rational
- The [4+1 architecture view][4plus1] developed out of this work
- Iterative development was formalized into 4 phases (Inception, Elaboration, Construction, Transition)
- _Rational Objectory Process_ (ROP) was the result of unifying Objectory with Rational
- ROP became the SEP sold by Rational to help turn requirements into working software

> Booch, Jacobson, and Rumbaugh were developing UML during their time at Rational
> 

### 1998 ###

- Rational acquired other companies leading up to 1998
- In 1998, Rational released _Rational Unified Process_ (RUP)
- Many subsequent revisions and improvements followed

### 1999 ###

- First publication of [Unified Software Development Process][usdp-book] (USDP), a book describing the Unified Process (UP)
- USDP and UP are used interchangeably
- UP is an open SEP, accessible to all
- RUP is commercial process product
- UP and RUP are closely related, more similar than different

### 2003 ###

- [IBM acquires Rational for $2.1 Billion][ibm-rational]
- [IBM sells and maintains RUP][rup-ibm] as a process product
- RUP, as a product, supplies all the standards, tools, and other necessities to help turn requirements into working software
- With UP, you need to discover and supply these yourself from various sources (commercial and/or open source)

### UP Timeline Summary ###

Year | Development
-----|------------
1967 | Ericsson Approach promoted "divide and conquer" technique
1980 | Software Description Language (SDL) introduced
1987 | Objectory AB founded; produced Objectory SEP
1995 | Rational acquires Objectory AB
1998 | Rational Unified Process (RUP) released
1999 | Unified Software Development Process (USDP) published
2003 | IBM acquires Rational for $2.1 Billion

## Waterfall / Traditional Approach ##

- This traditional approach is a sequential design process
- One works through successive steps in sequence
- Iterations are not part of the process
- It has been around since the 1960s

![Waterfall Lifecycle][waterfall]

> __READ MORE__: [Understanding the Waterfall Model][waterfall-techrep]
> 

### Requirements Analysis ###

- Gather customer requirements
- Understand business context and constraints
- Capture in _Requirements Specification_ document
- Include _Acceptance Test Specifications_ to use after Installation step

### Design ###

- _Software and Hardware Architecture Specification_ is produced
- Define performance and security parameters
- User interface design is addressed
- Various design specifications are output of this step
- Include _Sub-System Test Specifications_ and _Unit Test Specifications_

### Implementation ###

- Construct the software according to the design specifications
- Write the code, develop the interface, and other specialized tasks
- Output is a running set of code

### Testing ###

- Code is tested and verified 
- Unit tests are performed for individual code modules
- System testing is performed for integration between sub-systems and the overall system
- Acceptance testing is done to validate the end user experience
- Product documentation and user manual is produced
- __NOTE__: Inevitably there will be bugs so feedback is provided back to the Implementation team and  iterations start to occur between Implementation and Testing

### Installation ###

- Installation of software at customer site
- Customer trained and provided user manuals
- Customer runs acceptance test to validate correctness
- The result is operational software at the customer location

### Maintenance ###

- _Change Requests_ initiate modifications
- The fix defects, add functionality, or improve performance
- _Maintenance Releases_ are produced, tested, and installed

### Advantages of Waterfall ###

- Disciplined approach with each stage clearly identified
- Each phase has a defined start and end point
- Project progress can be evaluated at the end of each phase
- Emphasis on Requirements, Analysis, and Design before coding anything
- Useful for managing projects with high risk
- Different teams can be specialized for each phase
- Can pipeline separate projects through the various teams

### Criticisms of Waterfall ###

- Real projects rarely follow such a well laid out liner sequence
- Customers rarely know what all they want up front
- Customer involvement is only at the beginning and end of the process
- Lapsed time between Requirements Analysis and Installation can be long (many months or years)
- Iterations are inevitable, which break the process and cause disruptions in process

## The Future is Agile ##

### The Agile Manifesto ###

> We are uncovering better ways of developing software  
> by doing it and helping others do it.  
> Through this work we have come to value:  
>
> Individuals and interactions over processes and tools  
> Working software over comprehensive documentation  
> Customer collaboration over contract negotiation  
> Responding to change over following a plan  
>
> That is, while there is value in the items on  
> the right, we value the items on the left more.  

> __READ MORE__: [The Agile Manifesto][agile-manifesto]
> 

> __READ MORE__: [Principles of Agile Software][agile-principles]
>

### Scrum ###

- A management framework that utilizes one or more cross-functional teams to complete a project
- Provides structure and rules to roles, meetings, artifacts, etc.
- Introduces fixed-length iterations called _Sprints_ that typically last 1-2 weeks
- Each Sprint is an incrementally significant function of the overall project
- Scrum teams attempt to produce a complete and tested _product-increment_ for every iteration

![SCRUM Iterations][scrum-iter]

> __READ MORE__: [SCRUM Reference Card][scrum-card]
> 

> __READ MORE__: [SCRUM as an Agile Approach][agile-scrum]
> 

### The Essence Kernel ###

- Introduced by Ivar Jacobson International in 2014
- Includes a standard that defines the smallest set of concepts that are common to all software projects
- Aims to help teams assess health of software projects and improve the way they work
- Includes practical tools and assets that helps software teams put theory into practice
- It helps teams turn requirements into working software

> __READ MORE__: [SEMAT and The Essence Kernel][essence-ivar]
> 

### Agility Abounds ###

> The field of Agile Approaches is itself very agile (growing and changing)
> 

Consider the following approaches that you might encounter as part of your career:

- Adaptive Software Development (ASD)
- Agile Unified Process (AUP)
- Disciplined Agile Delivery (DAD) &lArr; A descendant of AUP
- Dynamic Systems Development Method (DSDM)
- eXtreme Programming (XP)
- Feature Driven Development (FDD) aka Behavior Driven Development (BDD)
- Test Driven Development (TDD)
- Kanban (development)

> __READ MORE__: [Agile Approaches][agile-list]
> 


---

[sep-use]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/SEP-use.png
[ivar]: http://en.wikipedia.org/wiki/Ivar_Jacobson
[ivar-intl]: http://www.ivarjacobson.com
[grady]: http://en.wikipedia.org/wiki/Grady_Booch
[james]: http://en.wikipedia.org/wiki/James_Rumbaugh
[ericsson]: http://www.ericsson.com/thecompany
[4plus1]: http://epf.eclipse.org/wikis/openup/core.tech.common.extend_supp/guidances/examples/four_plus_one_view_of_arch_9A93ACE5.html
[sdp]: http://en.wikipedia.org/wiki/Software_development_process "Software Development Process"
[rup]: http://en.wikipedia.org/wiki/Rational_Unified_Process "Rational Unified Process"
[rup-ibm]: http://www.ibm.com/software/rational "Rational Software"
[ibm-rational]: http://www-03.ibm.com/press/us/en/pressrelease/314.wss "IBM Acquires Rational"
[usdp-book]: http://www.amazon.ca/dp/0201571692 "Unified Software Development Process"

[rup-best]: https://www.ibm.com/developerworks/rational/library/content/03July/1000/1251/1251_bestpractices_TP026B.pdf "RUP Best Practices White Paper"

[waterfall]: https://s3-us-west-2.amazonaws.com/oosa-wiki/uploads/images/waterfall.png
[waterfall-techrep]: http://www.techrepublic.com/article/understanding-the-pros-and-cons-of-the-waterfall-model-of-software-development/

[agile-manifesto]: http://agilemanifesto.org/
[agile-principles]: http://agilemanifesto.org/principles.html

[scrum-card]: http://scrumreferencecard.com/scrum-reference-card/
[scrum-iter]: http://scrumreferencecard.com/scrumreferencecard-content/uploads/2013/03/scrum-iteration-detail.png
[agile-scrum]: http://agilemethodology.org/

[essence-ivar]: http://www.ivarjacobson.com/Software_Engineering_Method_and_Theory/

[agile-list]: http://en.wikipedia.org/wiki/Agile_software_development


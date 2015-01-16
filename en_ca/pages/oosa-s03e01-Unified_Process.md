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
	- Explain iterative and incremental software development within UP/RUP

## What is UP? &sect;2.2 ##

> UP is a modern SEP driven by user requirements
> 

![Purpose of SEP][sep-use]

- __SEP__ is an acronym for _Software Engineering Process_, also referred to as [Software Development Process (SDP)][sdp]
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
- SDL was designed to capture the behavior of telecommunications systems
- SDL-92 was a widely accepted object modeling standard

### 1987 ###

- Jacobson founded Objectory AB
- Objectory SEP formalized into 5 workflows (Requirements, Analysis, Design, Implementation, Test)
- Objectory SEP was sold as a package to help turn requirements into working software
- Objectory SEP provided templates, documentation, and a tool that should be used to customize your specific software solution

### 1995 ###

- Rational acquired Objectory AB and Jacobson went to work unifying Objectory SEP with process-related work already done at Rational
- The [4+1 architecture view][4plus1] developed out of this work
- Iterative development was formalized into 4 phases (Inception, Elaboration, Construction, Transition)
- _Rational Objectory Process_ (ROP) was the result of unifying Objectory with Rational
- ROP became the SEP sold by Rational to help turn requirements into working software
- Booch, Jacobson, and Rumbaugh were developing UML at this time

### 1998 ###

- Rational acquired other companies leading up to 1998
- In 1998, Rational released _Rational Unified Process_ (RUP)
- Many subsequent revisions and improvements followed

### 1999 ###

- First publication of [Unified Software Development Process][usdp-book] (USDP), a book describing the Unified Process (UP)
- USDP and UP are used interchangeably
- UP is an open SEP, accessible to all
- RUP is commercial process product
- UP and RUP are closely related

### 2003 ###

- [IBM acquires Rational for $2.1 Billion][ibm-rational]
- [IBM sells and maintains RUP][rup-ibm] as a process product
- RUP as a product supplies all the standards, tools, and other necessities to help turn requirements into working software
- With UP, you need to discover and supply these yourself from various sources (commercial or open source)

### UP Timeline Summary ###

Year | Development
-----|------------
1967 | Ericsson Approach promoted "divide and conquer" technique
1980 | Software Description Language (SDL) introduced
1987 | Objectory AB founded; produced Objectory SEP
1995 | Rational acquires Objectory AB
1998 | Rational Unified Process (RUP) released
1999 | Unified Software Development Process (USDP) published, aka Unified Process (UP)
2003 | IBM acquires Rational for $2.1 Billion

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
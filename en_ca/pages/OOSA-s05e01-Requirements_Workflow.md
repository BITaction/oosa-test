# COMP XXXX - Object Oriented Systems Analysis #

---

## Week 5 Notes - Gathering Requirements

## References

- [Course Textbook][textbook]

---

# Chapter 3

## The Requirements Workflow  &sect;3.2
- In this workflow, we have to find out what the project is trying to achieve.  
- Most of this work is done in the Inception and Elaboration Phases. See Figure 3.2 (p.51)
- Should strive to capture both functional and non-functional requirements.

## Requirements Metamodel &sect;3.3
- Folder-like symbols represent UML packages. See Figure 3.3 (p.52)
- Anchor icons (a plus inside a circle) indicates which folder is the container.


## Requirements workflow detail &sect;3.4
- Figure 3.4 shows specific tasks and who performs them.
- In this course, the tasks of this workflow will include:
    - Finding Actors and Use Cases.
    - Detailing Use Cases.
    - Structuring the Use Case model.
    - Finding functional requirements.
    - Finding non-functional requirements.
    - Prioritizing requirements.
    - Tracing requirements to Use Cases.


## The importance of Requirements &sect;3.5
- Requirements tell what the system must do.
- The leading cause of project failure is missed or incomplete requirements.
- The other leading cause of project failure is lack of user involvment.


## Defining Requirements &sect;3.6
- a requirement can be defined as a specification that should be implemented.
- The two types of requirements are:
    - functional
    - non-functional
- a requirement indicates WHAT the system must do.
- a requirements should NOT indicate HOW the system will do it.

### The requirements model &sect;3.6.1
- the key question about ANY requirement is: "How useful is it to me?"

### Well-formed requirements &sect;3.6.2
- requirements should be clearly and consistently named. See Figure 3.6 (p.57)
- requirement name should follow the structure '{id} The {system name} shall {function to be performed}'

### Functional and non-functional requirements &sect;3.6.3
- To keep things simple and useful, requirements should be divided in functional and non-functional requirements.
- Functional requirements state what the system should do (i.e. 'the ATM system shall check the validity of the inserted ATM card').
- Non-functional requirements are constraints placed on the system (i.e. 'the ATM system shall be written in C++').

### Organizing requirements &sect;3.6.4
- Use a hierarchy of requirement Types to categorize requirements.
- The two high-level types are functional and non-functional. See Figure 3.7 (p.58).
- To be practically useful, this shouldn't exceed 2 or 3 levels.

### Requirement attributes &sect;3.6.5
- A requirement should have a number of attributes such as 'Due Date' and 'Priority'.
- A suggested list of attributes. See Tables 3.5 (p.59) and 3.6 (p.60) for more details:
    - Due date
    - Priority
    - Status
    - Benefit
    - Effort
    - Risk
    - Stability
    - Target Release


## Finding Requirements &sect;3.7
Requirements come from the context of the system you are trying to model.

### Requirements elicitation &sect;3.7.1
!! The map is NOT the territory !!
When using natural language, people apply 3 filters when describing what they know:

- deletion - some information is filtered out.
- distortion - information is modified through the mechanisms creation and hallucination.
- generalization - information is abstracted into rules, beliefs, principles, etc.

Keywords to watch for that indicate that filtering is at work:

- all
- everyone
- always
- never
- nobody
- none

### Interviews &sect;3.7.2
This is the most direct way of gathering requirements - best if done one-on-one.

- Don't hallucinate a solution - set your pre-conceptions aside during the interview (hard to do!).
- Ask context-free questions - i.e. ask "Who uses the system?" not "Do you use the system?"
- Listen - give the interviewee time to talk.
- Don't mind-read! We all mind-read to some extent. That's hallucinating that we know what someone feels, wants or is thinking.
- Have patience!
 

### Questionnaires &sect;3.7.3
They are NOT substitutes for interviews!

Best used as supplements to interviews.

### Requirements workshop &sect;3.7.4
One of the most efficient ways of capturing requirements.

The workshop should focus on brainstorming.
This approach may require several workshops to be held over time as your understanding deepens.


[textbook]: http://www.amazon.ca/UML-Unified-Process-Object-Oriented-Addison-Wesley/dp/B00E286B8G/ref=sr_1_3?ie=UTF8&qid=1403202307&sr=8-3&keywords=uml+2+and+unified+process "Text book"
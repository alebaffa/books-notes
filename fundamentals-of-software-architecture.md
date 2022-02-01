---
title: "[Book] Fundamentals of Software Architecture - Notes"
date: 2022-01-16T18:27:29+01:00
draft: false
tags: ["architecture", "books"]
description: "Notes on Fundamentals of Software Architecture book"
---

![cover book.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1642342998250/dgSGYyfE9.jpeg)

The authors of the book provide the slides related to this book online: 

Fundamentals of Software Architecture Hands-on [[1 Day](https://nealford.com/downloads/Software_Fundamentals_Workshop_by_Neal_Ford_and_Mark_Richards.pdf)] [[2 Day](https://nealford.com/downloads/SAFund-2day.pdf)]

## Chapter 1: Introduction
**The four dimensions that define software architecture**

1. **Structure**, the type of the architecture the system is implemented in (microservices, layered, microkernel...).
2. **Architecture characteristics**, the success criteria of a system, the *-ilities* (reliability, elasticity, availability, security, agility, fault tolerance, deployability, testability, etc...)
3. **Architectural decisions**, *the rules *of how a system should be constructed. For example, in a layered architecture the presentation layer can access the database only through the business layer.
4. **Design principles**, a set of implementation guidelines, that are not forced rules (which instead is an architectural decision) and which choice is left to the developers. For example, "*in a microservices architecture the communication between services should leverage asynchronous messaging*".

**Eight core expectations of a software architect**

1. **Make architecture decisions**. The architect should make architectural decisions (e.g. reactive based framework) and give design principles (e.g. asynchronous messaging) to guide the development teams make their own technical good decisions (e.g. React, Vue, AMQP, etc...).
2. **Continually analyze the architecture**. 
3. **Keep current with latest trends**. Follow technology blogs, check technology radars, etc and find as much time as possible to keep up to date with technologies, tools, platforms and techniques. 
4. Ensure compliance with decisions
5. Diverse exposure and experience
6. Have business domain knowledge
7. Possess interpersonal skills
8. Understand and navigate politics

**The Laws of Software Architecture**
1. First Law: *Everything is a trade-off*
2. Second Law: *Why is more important than How*

## Chapter 2: Architectural Thinking
**Architecture versus design/development**
An architect deals with the four dimensions mentioned before and guides the design choices/implementation details managed by the developers, also through leadership and mentoring. There must be bi-directional communication between the architect and the developers team. 

**The three levels of knowledge in the knowledge triangle** 
From top to bottom:
1. **Things you know**. Developers' early career focuses mostly on this, which are also the *things you must maintain*.  This is related to the importance to keep a deep knowledge on few technical specialties.
2. **Things you know you don't know**. Advancing in one's career incidentally increases this level.
3. **Things you don't know you don't know**.

This reminds me of the  [Four Stages of Competence](https://en.wikipedia.org/wiki/Four_stages_of_competence) .

**Focus more on technical breadth rather than technical depth**
Taking *the three levels of knowledge* as a reference, the *technical breadth* includes the 1. and 2. . An architect must also maintain few deep technical specialties. 

> Developers transitioning to the architect role may have to change the way they view knowledge acquisition. Balancing their portfolio of knowledge regarding depth versus breadth is something every developer should consider throughout their career.


**Ways of maintaining your technical depth and remaining hands-on as an architect**
- Develop Proof of Concept. When doing so, an architect should try to produce code that is clean and can be followed as an example by the development team.
- Get involved in the development of some features.
- Bug fixes
- Develop automation and analyzing tools (check out https://www.archunit.org/)
- Code reviews

## Chapter 3: Modularity

**Abstractness, Instability and Distance from the main sequence**
- Abstractness measures the ratio between abstract elements (interfaces, abstract classes..) and concrete elements (concrete class).
- Instability measures the ratio between incoming coupling (*afferent coupling*, functions, components..) and outgoing coupling (*efferent coupling*, connections to other components).

The Main Sequence is a derived metrics based on Abstractness and Instability.

<img src="https://cdn.hashnode.com/res/hashnode/image/upload/v1642351293595/kzEkJdMJx.png" style="width:400px;"/>

> The closer to the line, the better balanced the class. Classes that fall too far into the upper-righthand corner enter into what architects call the zone of uselessness: code that is too abstract becomes difficult to use. Conversely, code that falls into the lower-lefthand corner enter the zone of pain: code with too much implementation and not enough abstraction becomes brittle and hard to maintain.

<img src="https://cdn.hashnode.com/res/hashnode/image/upload/v1642351366891/lnvY0jVol.png" style="width:400px;"/>


**What is meant by the term connascence?**
> Two components are connascent if a change in one would require the other to be modified in order to maintain the overall correctness of the system.

*Connascence* is an old topic that can be found in many other books related to clean code, refactoring, code smells. A useful link is [this](https://codesai.com/2017/01/about-connascence) .

## Chapter 4: Architecture Characteristics Defined
**Three criteria to be considered an architecture characteristic**
An architecture characteristic meets three criteria:

1. Specifies a nondomain design consideration
2. Influences some structural aspect of the design
3. Is critical or important to application success

**Implicit and explicit characteristics**
> Implicit ones rarely appear in requirements, yet they’re necessary for project success. For example, availability, reliability, and security underpin virtually all applications, yet they’re rarely specified in design documents. Architects must use their knowledge of the problem domain to uncover these architecture characteristics during the analysis phase. [...] Explicit architecture characteristics appear in requirements documents or other specific instructions.

**Operational, Structural and Cross-Cutting characteristics**
- **Operational** architecture characteristics cover capabilities such as performance, scalability, elasticity, availability, and reliability;
- **Structural** characteristics are about code quality concerns, such as good modularity, controlled coupling between components, readable code, and a host of other internal quality assessments. Configurability, Extendibility, Installability, Localization, Portability, etc.;
- **Cross-Cutting** characteristics fall outside or defy categorization yet form important design constraints and considerations. Accessibility, Authentication, Authorization, Security, Privacy, Legal, etc.

The International Organization for Standards (ISO) publishes a list of characteristics organized by capabilities. Check it out [here](https://iso25000.com/index.php/en/iso-25000-standards/iso-25010).

## Chapter 5: Identifying Architecture Characteristics
**Limit the number of characteristics (“-ilities”) an architecture should support**
> A common anti-pattern in architecture entails trying to design a generic architecture, one that supports all the architecture characteristics.[...] Don’t obsess over the number of charateristics, but rather the motivation to keep design simple.

This reminds me of the [Premature Abstraction](https://wiki.c2.com/?PrematureAbstraction) problem. Don't overthinkg in advance and make the architecture too complex.

**Domain concerns to architecture characteristics**

| Domain concern          | Architectural characteristic                               |
|-------------------------|------------------------------------------------------------|
| **Mergers and acquisition** | Interoperability, scalability, adaptability, extendibility |
| **Time to market** | Agility, testability, deployability|
| **User satisfaction** | Performance, availability, fault tolerance, testability, deployability, agility, security| 
| **Competitive advantage** | Agility, testability, deployability, scalability, availability, fault tolerance|
| **Time and budget** | Simplicity, feasibility |

### Chapter 6: Measuring and Governing Architecture Characteristics

**Operational Measures**

Things like performance or scalability are difficult to measure since there are many interpretations and really depends on many factors. Measurements of this kind need to be selected with statistical models, and then analyzed and monitored.

**Structural Measures**

An obvious measurable aspect of code is complexity, defined by the cyclomatic complexity metric.

> Architects and developers universally agree that overly complex code represents a code smell; it harms virtually every one of the desirable characteristics of code bases: modularity, testability, deployability, and so on. Yet if teams don’t keep an eye on gradually growing complexity, that complexity will dominate the code base.

- http://www.crap4j.org. A metrics tool in the Java world, Crap4J, attempts to determine how poor (crappy) your code is by evaluating a combination of CC and code coverage; if CC grows to over 50, no amount of code coverage rescues that code from crappiness

**Process Measures**
> Some architecture characteristics intersect with software development processes. For example, agility often appears as a desirable feature. However, it is a composite architecture characteristic that architects may decompose into features such as testability, and deployability.

**Governing Architecture Characteristics - Fitness Functions**

*Fitness function: an object function used to assess how close the output comes to achieving the aim.*

*Architecture fitness function
Any mechanism that provides an objective integrity assessment of some architecture characteristic or combination of architecture characteristics*

- Tools: [JDepend](https://oreil.ly/ozzzk), [ArchUnit](https://www.archunit.org/)
- Chaos Monkey and Chaos Engineering by Netflix: https://github.com/netflix/chaosmonkey

> A few years ago, the influential book The Checklist Manifesto by Atul Gawande (Picador) described how professions such as airline pilots and surgeons use checklists (sometimes legally mandated). It’s not because those professionals don’t know their jobs or are forgetful. Rather, when professionals do a highly detailed job over and over, it becomes easy for details to slip by; a succinct checklist forms an effective reminder. This is the correct perspective on fitness functions

## Chapter 7: Scope of Architecture Characteristics

**Architecture quantum**

An independently deployable artifact with high functional cohesion and synchronous connascence.

Quantum need to:
- be Independently deployable
- have High functional cohesion
- have Synchronous connascence

## Chapter 8: Component-Based Thinking
**Technical partitioning**:
> Organizing architecture based on technical capabilities like the layered monolith represents technical top-level partitioning.

has the side effect to support the *Conway's Law*:
> Organizations which design systems … are constrained to produce designs which are copies of the communication structures of these organizations.

**Advantages**
- Clearly separates customization code.
- Aligns more closely to the layered architecture pattern.

**Disadvantages**
- Higher degree of global coupling. Changes to either the Common or Local component will likely affect all the other components.
- Developers may have to duplicate domain concepts in both common and local layers.
- Typically higher coupling at the data level. In a system like this, the application and data architects would likely collaborate to create a single database, including customization and domains. That in turn creates difficulties in untangling the data relationships if the architects later want to migrate this architecture to a distributed system.

**Domain partitioning**:

> inspired by the Eric Evan book Domain-Driven Design [...] the architecture around domains or workflows rather than technical capabilities. As components often nest within one another, each of the components in Figure 8-4 in the domain partitioning (for example, CatalogCheckout) may use a persistence library and have a separate layer for business rules, but the top-level partitioning revolves around domains.

**Advantages**
- Modeled more closely toward how the business functions rather than an implementation detail
- Easier to utilize the Inverse Conway Maneuver to build cross-functional teams around domains
- Aligns more closely to the modular monolith and microservices architecture styles
- Message flow matches the problem domain
- Easy to migrate data and components to distributed architecture

**Disadvantage**
- Customization code appears in multiple places

**Component Identification Flow**
1. Identifying Initial Components
2. Assign Requirements to Components
3. Analyze Roles and Responsibilities
4. Analyze Architecture Characteristics
5. Restructure Components

**Entity trap**
> The entity trap anti-pattern arises when an architect incorrectly identifies the database relationships as workflows in the application, a correspondence that rarely manifests in the real world.

Three ways to determine the components of a system:
- Actor/Actions approach
- Event Storming
- Workflow approach

[Fallacies of distributed systems](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing)

## Chapter 9: Architecture Styles

**Monolithic**
- Layered architecture
- Pipeline architecture. Ex: systems using ETL tools that use pipes (comm channels between filters) and filters (producer, transformer, tester, consumer)
- Microkernel architecture

**Distributed**
- Service-based architecture
- Event-driven architecture
- Space-based architecture
- Service-oriented architecture
- Microservices architecture

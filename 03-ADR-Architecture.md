---
# Configuration for the Jekyll template "Just the Docs"
parent: Decisions
nav_order: 3
title: Monolithic vs Microservice vs Layered Architecture

status: "{proposed}"
date: {07-12-24 when the decision was last updated}
decision-makers: {Harvey Spencer, Ethan Hemmingway, James Kerridge, Tasnim Begum}
consulted: {Soumya Basu & Chris Bates}
informed: {Soumya Basu & Chris Bates}



#<!-- we need to disable MD025, because we use the different heading "ADR Template" in the homepage (see above) than it is foreseen in the template -->
#<!-- markdownlint-disable-next-line MD025 -->


{Comparing Monolithic, Microservice and Layered Architecture in a Geographically Distributed Media Library System}

## Context and Problem Statement

{One of the key challenges when planning the build of the AML library system has been whether to adopt a monolithic, microservice or layered architecture. Our main concern is finding a balance of good horizontal scalability while maintaining a reasonably low level of complexity. All three have pros and cons that impact on the requirements set by the client such as scalability, maintainability, fault tolerance and complexity. Our decision here will massively impact our development process so it is one that will not be made without forethought.}

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* {The system should be horizontally scalable to allow the system to grow annually without performance drops}
* {As the system is geographically distributed, a technology must be chosen that can be deployed over a large geographical area}
* {The system must be easily maintainable and easy for 3rd party software developers doing maintenance work to understand}

## Considered Options

* {Microservice Architecture}
* {Monolithic Architecture}
* {Layered Architecture}
* {Service Based Architecture}


## Decision Outcome

Chosen option: "{Layered Architecture, because it enforces separation of concerns, improving maintainability and code organization and, ensures the system's functionality while accommodating the geographically distributed nature of the media library system.}"


### Consequences

* Good, because {The system is broken into distinct, independently deployable services, making it easier to manage, scale, and maintain.}
* Good, because {Each service can be scaled independently based on demand, such as scaling the Borrowing Service during peak periods without impacting other parts of the system.}
* Good, because {If one service fails, it doesn't impact the entire application, ensuring the rest of the system remains operational.}
* Good, because {Different technologies or programming languages can be used for different services, allowing our team to optimize performance and innovate as needed.}
* Good, because {Teams can work on different services in parallel, enabling faster delivery of new features or updates.}
* Bad, because {Managing a system with multiple services can be challenging, requiring robust orchestration, monitoring, and communication mechanisms.}
* Bad, because {Services need to communicate with each other, often over the network, which can introduce latency and potential points of failure.}
* Bad, because {Testing requires verifying interactions between services as well as their individual functionality, increasing the overall testing complexity.}

<!-- This is an optional element. Feel free to remove. -->
### Confirmation

{Compliance with this ADR can be confirmed through code checks and ensuring that the services seamlessly integrate with each other. During development, if we are encountering issues with this then we may have to switch to a less complex architecture to improve complexity issues and ensure the system is ready within the proposed time frame.}




## Pros and Cons of the Options
### {Microservice Architecture}
* Good, because {a microservice architecture can improve team autonomy as individuals can build and deploy services themselves without having to wait for pull request approval}
* Good, because {it allows for flexible scaling where individual services can be scaled in accordance with demand, this can save both time & resources}
* Good, because{this architecture allows programs to be highly maintainable and allows experimentation with new features. It is also easier to isolate & fix faults within individual services}
* Good, because{the system will be much more reliable as changes for specific services can be deployed without the worry of bringing down the entire application, only that service}
* Bad, because {there can be a lack of standardisation within microservice applications due to different languages & logging methods}
* Bad, because {each new microservice may be developed by a different individual/team it may be difficult for somebody else to perform maintainance on this if they don't understand the structure of the creators code}
* … <!-- numbers of pros and cons can vary -->

### {Monolithic Architecture}
{Ebay | Ebay's architecture is monolithic where all products, user data and transactions are stored in a singular database | https://medium.com/@roopa.kushtagi/system-design-trade-offs-monolithic-vs-microservices-architecture-1e14a9fe9e99 | …}

* Good, because {since the entire system will be within one executable file, deployment will be easier}
* Good, because {With a centralised code base, one API can perform multiple functions that numerous APIs perform using microservices}
* Neutral, because {debugging is easier as all code is located in one place}
* Bad, because {a huge monolithic application can add complexity and slow development as it gets more and more difficult to read and follow as development continues. Team members may be confused after changes are made and code is moved around.}
* Bad, because {A small change to a monolithic application require the redeployment of the entire application}
* Bad, because {monolithic applications are less reliable since any errors in modules can cause the application to fail}

### {Layered Architecture}
* Good, because {it enforces clear separation of concerns, making it easier to organize and maintain code by assigning specific responsibilities to each layer.}
* Good, because {it is simple and widely understood, allowing for quick onboarding and consistent workflows, especially for small teams.}
* Good, because {changes in one layer typically have minimal impact on other layers, improving maintainability and reducing risk during updates.}
* Bad, because {it can become tightly coupled over time, making large-scale changes or refactoring difficult.}
* Bad, because {it has limited scalability since scaling typically requires replicating entire layers rather than specific components.}

### {Service Based Architecture (Chosen Option)}
* Good, because {it provides modularity, enabling teams to work on specific services without interfering with others.}
* Good, because {it allows scaling of specific services based on demand, optimizing resources and improving performance.}
* Good, because {services are loosely coupled, improving fault isolation. If one service fails, the others can continue functioning.}
* Bad, because {it introduces complexity in orchestrating communication between services, requiring tools like API gateways.}
* Bad, because {scaling services separately can create resource bottlenecks or coordination challenges if dependencies are not well managed.}


### {References}
* GeeksforGeeks. (2024, September 30). Monolithic vs. ServiceOriented vs. Microservice Architecture. GeeksforGeeks. https://www.geeksforgeeks.org/monolithic-vs-service-oriented-vs-microservice-architecture/
* Richards, M. (2019). Software Architecture Patterns. O’Reilly | Safari. https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch01.html

‌
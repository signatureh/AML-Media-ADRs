---
# Configuration for the Jekyll template "Just the Docs"
parent: Decisions
nav_order: 1
title: Language Choices for AML Media Library


status: accepted
date: {2024-10-10 when the decision was last updated}
decision-makers: {Harvey Spencer, Ethan Hemingway, James Kerridge, Tasnim Begum}
consulted: {Soumya Basu & Chris Bates}
informed: {Soumya Basu & Chris Bates}
---
<!-- we need to disable MD025, because we use the different heading "ADR Template" in the homepage (see above) than it is foreseen in the template -->
<!-- markdownlint-disable-next-line MD025 -->
# {What language is best when scalability is a major concern?}

## Context and Problem Statement
{For a library system with an expected annual growth of 10%, the goal is to develop a horizontally scalable system. The chosen languages should optimize for modularity, performance, and seamless integration between services while supporting robust database operations and high availability.
The system must efficiently handle user operations such as borrowing, extending, and returning media across a geographically distributed user base. We considered the best languages to enable modular, efficient development with easy integration of frontend and backend components.}

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* {decision driver 1, The system should be scalable to handle user base growth}
* {decision driver 2, The system should not face a drop in performance during peak hours}
* {decision driver 3, The system should seamlessly integrate with a database that can handle large data sets}
* {decision driver 4, The system should have 99.9% uptime and any downtime should be communicated to users}
* … <!-- numbers of drivers can vary -->

## Considered Options

* {GoLang}
* {NodeJS}
* {C#}
* {HTML, CSS etc.}
* {Python}
* {JavaScript}

## Decision Outcome

Chosen option: {"Node.js, JavaScript, GoLang, and HTML/CSS", because they collectively address the concerns of scalability, performance, and developer productivity. Node.js excels in real-time, asynchronous operations, GoLang provides lightweight and performant backend processing, and HTML/CSS ensure a responsive and universally accessible frontend.}

<!-- This is an optional element. Feel free to remove. -->
### Consequences

* Good, because {Node.js and GoLang's modular design and lightweight runtimes enable efficient horizontal scaling of services.}
* Good, because {GoLang's concurrency model (goroutines, channels) ensures backend operations are highly performant and non-blocking, even under heavy workloads.}
* Good, because {HTML/CSS allow for responsive web designs, ensuring a consistent user experience across devices and browsers.}
* Bad, because {Managing a multi-language stack requires more sophisticated pipelines and increased operational overhead.}
* Bad, because {Node.js's single-threaded nature and callback-heavy architecture can complicate debugging in highly asynchronous workflows.}

<!-- This is an optional element. Feel free to remove. -->
### Confirmation

{Compliance with this ADR will be confirmed when we begin development in Go, so long as there are no major issues during development, this ADR will be confirmed simply by beginning to use Go.}

<!-- This is an optional element. Feel free to remove. -->
## Pros and Cons of the Options

### {GoLang}

<!-- This is an optional element. Feel free to remove. -->
{GoLang | GoLang is an open source language designed by Goodle, it's simple & easy to use but still optimised for efficiency and high performance when building large scale distributed systems. | pointer to more information https://go.dev/learn/| …}

* Good, because {the built in concurrency support with goroutines and channels make it the perfect choice when developing an application with efficiency and horizontal scalability in mind.}
* Good, because {GoLang has a simple, easy to learn/understand syntax meaning that rapid prototyping and development is possible}
* Good, because {the compiled nature of GoLang allows it to run on multiple platforms without the need for virtual machines}
* Bad, because {GoLang doesn't have access to the extensive amount of libraries that something like Python or Java does due to it being a relatively new and unused language when compared to older, more stable languages}
* Bad, because {Some errors can be difficult to understand due to the lack of a sum type meaning that some issues can take a while to diagnose and fix}


### {Node.js}
* Good, because {it supports asynchronous programming and non-blocking I/O, making it highly effective for real-time updates and high concurrency.}
* Good, because {its vast ecosystem of NPM packages speeds up development and reduces repeat code}
* Bad, because {unhandled asynchronous errors can complicate debugging and maintenance.}

### {JavaScript}
{JavaScript is a core component of the tech stack for the AML Media Library. It enhances interactivity on the frontend and provides a seamless bridge between Node.js and HTML/CSS.}
* Good, because {JS is essential for creating dynamic web pages, allowing for client side interactivity.}
* Good, because {It integrates well with both HTML/CSS and NodeJS.}
* Bad, because {Using JS can result in debugging complexities and inconsistent coding practices due to its flexibility.}



### {HTML & CSS}

{Website Development | using HTML and CSS to create websites rather than desktop applications | [pointer to more information](https://www.w3schools.com/html/html_css.asp) | …}

* Good, because {HTML has widespread browser compatability making it cross platform by default and the web pages will look the same on all different browsers}
* Good, because {HTML has a very loose syntax and allows developers creative freedom to create diverse web experiences}
* Bad, because {The code structure can be extremely convaluted & difficult to read, if a complex program is being created then this may lead to code repitition and huge load times}
* Bad, because {No offline access}

<!-- This is an optional element. Feel free to remove. -->
## More Information

{You might want to provide additional evidence/confidence for the decision outcome here and/or document the team agreement on the decision and/or define when/how this decision the decision should be realized and if/when it should be re-visited. Links to other decisions and resources might appear here as well.}

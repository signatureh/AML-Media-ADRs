---
# Configuration for the Jekyll template "Just the Docs"
parent: Decisions
nav_order: 100
title: Database


# status: "{Accepted}"
# date: {07/12/24}
# decision-makers: {Harvey Spencer, Ethan Hemmingway, James Kerridge, Tasnim Begum}
# consulted: {Soumya Basu & Chris Bates}
# informed: {Soumya Basu & Chris Bates}
---

# {JWT and Other Considered Options for Scalable Authentication and Authorization}

## Context and Problem Statement

{The AML media library system requires security functionality to manage user authentication and authorisation. This solution must be lightweight, scalable and compatible with a
 distributed architecture. It should ensure data confidentiality and integrity across sessions and should support functionality such as borrowing and returning.}

## Decision Drivers

* {Scalability: The security system should function efficiently as the system scales to handle increased users.}
* {The security should ensure strong encryption, data integrity and have minimal avenues of cyber attack.}
* {User experience remains important even within a security system, no unneccesary friction should be added to the login process.}


## Considered Options

* {JSON Web Tokens (JWT)}
* {Session Cookies}
* {OAuth 2.0}
* {Single Sign On (SSO)}
* {WWW-Authenticate}


## Decision Outcome

Chosen option: "{JWT}", because {It meets the scalability requirement while still offering robust security and compatability with a distributed system. It ensures efficient authorisation by encoding user data in a compact, signed token that requires no additional server side storage}.


### Consequences

* Good, because {JWT is lightweight, allowing fast transmission of tokens over the network.}
* Good, because {it supports encryption and digital signing, ensuring confidentiality and integrity of the token.}
* Bad, because {If token configuration is done wrong, such as wrong expiration time, security vulnerabilitys may begin to appear.}



### Confirmation

{The implementation of JWT will be confirmed through a code review to ensure token creation, validation and signing are all fully functional.}


## Pros and Cons of the Options

### {JWT}
* Good, because {JWT's statelessness and support of distributed systems improve scalability and performance.}
* Good, because {JWT tokens can be user for role authorisation}
* Neutral, because {Policies must be carefully configured to balance security and usability}
* Bad, because {Adding token revocation before expiry requires additional server side mechanisms}

### {Session Cookies}

{Server side session management tool using browser cookies to store session IDs}

* Good, because {It supports automatic session invalidation when the session is deleted server side}
* Bad, because {It's stateful nature requires server side storage, which does not scale well in a distributed environment}
* Bad, because {Load balancing requires session replication which can consume the applications processing power}

### {SSO}

{Centralized authentication service that generates tokens or credentials for connected applications.}

* Good, because {It centralises user authentication which reduces the number of avenues for a potential cyber attack}
* Good, because {User experience is improved by reducing login redundancy}
* Neutral, because {Integration with a 3rd party identity provider is required which may add unwanted cost and complexity.}
* Bad, because {Any compromise of the 3rd party identity provider will affect the whole system.}

### {OAuth2}

{Authorisation framework for token based access}

* Good, because {It provides access control through the use of token scopes}
* Good, because {It is widely supported and considered standard for 3rd party integrations}
* Bad, because {It adds complexity to the implementation and has a steep learning curve before usage.} 
* Bad, because {OAuth 2.0 requires dependancy on 3rd party services. If this service goes down it can directly impact OAuth's integration.}


## More Information

{You might want to provide additional evidence/confidence for the decision outcome here and/or document the team agreement on the decision and/or define when/how this decision the decision should be realized and if/when it should be re-visited. Links to other decisions and resources might appear here as well.}


## references
* Bakare, P. (2024, September 8). Session, Cookie, JWT, Token, SSO, and OAuth 2.0. DEV Community. https://dev.to/mrcaption49/session-vs-14md
* auth0.com. (2019). JWT.IO. Jwt.io. https://jwt.io/
* Chinta, M. (2024, February 13). OAuth 2.0. CodeNx. https://medium.com/codenx/oauth-2-0-4cddd6c7471f
* Auth0. (2015, September 23). What Is and How Does Single Sign-On Authentication Work? Auth0 - Blog. https://auth0.com/blog/what-is-and-how-does-single-sign-on-work/
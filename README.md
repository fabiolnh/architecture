# Fundamentals of Software Architecture (Currently Studying)

## Types:

1 - Solution Architect
  - Stays between the business area and the software
  - It is a technical area with a great vision of the business
  - Transform the business requirement into software solution
  - draw solution software architectures to reproduce how it will work 
  - C4, UML, BPMN
  - He will analyze the commercial impact when choosing a technology
  - Participate in commercial meetings of pre-sail or sail to show technical details
  - He can analyze costs to the business
  
2 - Technology Architect:
  - A Specialty based in a specific technology
  - Ex: Elastic Architect (specialty in ElasticStack), Java Architect, SQL Server, SAP, Salesforce, etc.
  
3 - Enterprise Architect
  - Impact the whole organization
  - Evaluation of new technologies to define which one will be used
  - Technology Standardization in the company
  - Big implementation planning
  - Cost Evaluation
  - Migrations
  - Core Systems of the company
  
4 - Software Architect
  - A Software Engineering discipline
  - Directly relation to the software development
  - "Low Level"
  - Affects the Organization Structure: Team Formation, Software Components
  - How the software will be developed according to the team formation.
  - It is the relation between the goal business and their restrictions, with the components that will be created and the responsibilities, aiming the software evolution
  * Roles:
    - Transform business requirements into architecture pattern
    - Orchestrate devs and domain experts
    - Understand deeply concepts and architecture models
    - Assists in decision making when everything is not good
    - Reinforce good development practices
    - Code Review
  * Why should we learn?
    - Macro Vision
    - Understand all the options to decide which one is better
    - Think in long term
    - Taking Decisions not based in market "hypes"
    - Good project patterns, development and good practices
    - Clarify of the software impact in the company
    - Make decisions with confidence

## Architecture VS Design
  - Architecture: Global Scope, High Level (components, abstractions, etc)
  - Design: Local Scope (class responsibilities, patterns, etc)
  - Both go together. There is a discussion of what each one means.

## Sustainability
  - Software is expensive
  - Software has to be paid in long term
  - Software needs to follow the business evolution
  - The solution needs to be architected

## Pillars
  - Structure
  - Easy evolution to attend requirement business
  - Components
  - Systems relationship
  - Governance (patterns, rules, documentation, definitions, languages, protocols, systems to communicate)
    * If someone goes away from the company, the project cannot finish

## Architectural Requirements
  - Performance
  - Data storage
  - Scalability
  - Security
  - Legal (ex: LGPD)
  - Audit
  - Marketing

## Features
  - We should think in some features before begin a system, we should not depend on luck. These answers will define what technologies you will use and how your system will be architected.
  1 - Operational Features
    * Availability (SLA, SLO) (Ex: observability to check)
    * Disaster Recovery (Ex: how we should act when the system will get offline. Ex: Multi-Region in case a Region fails. Ex: Terraform to recreate the whole structure)
    * Performance (Ex: latency and throughput (capacity of receive requests))
    * Recovery (Backup) (Ex: check if the backup is ok in a period and put it in another network)
    * Reliability and Security (Ex: Brute force in an endpoint)
    * Robust: (Ex: if a Availability Zone go down, what you should do?)
    * Scalability (Ex: Vertically or Horizontally)
    
  2 - Structural Features
    * Configurable (Ex: How ease is the changing of a Config. Ex: Envirenment Variable, Key of the API Gateway). Think: If you put your application in the Stage Env and you have to change something in your code to get the application work, it is not OK!
    * Extensibility (Ex: The application has to be thinked in get bigger)
    * Easy Installation (Ex: Containers)
    * Reusable Components (Ex: libraries. Usually separated teams create different solutions. It is good to centralize it and create a team to maintain these libraries)
    * Internalization (In the frontend, when we change the language, the things sometimes not work exatcly as we expected. Think it. In the backend: Think not only texts, but: Coin, Conversions, Payment, etc)
    * Easy Maintenance (it is not so simple. The major difficult is a complex solution gets simple. SOLID, Layes, Adapters, Interfaces, Design Patters, Accoplaments. Quertions: It is easy to add new features? It is easy to fix some points? There are Tests?
    * Portability (Ex: more than one database. OBS: it os not so easy to change database, however, Will be a lot of impacts if we change the Database? Ex: you are working with Elastic Stack, It will be easy to change to NewRealic? Maybe will be better to work with OpenTelemetry. Ex: It is easy to change the Payment Gateway? Etc.)
    * Easy Support (Ex: logs, Debugging. A way to see the problems before the client call to the team. Observability in general)
    
  3 - Cross-Cutting Features
    * 

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
  - We should think about some features before beginning a system, we should not depend on luck. These answers will define what technologies you will use and how your system will be architected.

1 - Operational Features
  * Availability (SLA, SLO) (Ex: observability to check)
  * Disaster Recovery (Ex: how we should act when the system will get offline. Ex: Multi-Region in case a Region fails. Ex: Terraform to recreate the whole structure)
  * Performance (Ex: latency and throughput (capacity of receive requests))
  * Recovery (Backup) (Ex: check if the backup is ok in a period and put it in another network)
  * Reliability and Security (Ex: Brute force in an endpoint)
  * Robust: (Ex: if an Availability Zone goes down, what should you do?)
  * Scalability (Ex: Vertically or Horizontally)
    
2 - Structural Features
  * Configurable (Ex: How ease is the changing of a Config. Ex: Environment Variable, Key of the API Gateway). Think: If you put your application in the Stage Env and you have to change something in your code to get the application work, it is not OK!
  * Extensibility (Ex: The application has to be thinked in get bigger)
  * Easy Installation (Ex: Containers)
  * Reusable Components (Ex: libraries. Usually separated teams create different solutions. It is good to centralize it and create a team to maintain these libraries)
  * Internalization (In the frontend, when we change the language, things sometimes do not work exactly as we expected. Think about it. In the backend: Think not only texts, but: Coin, Conversions, Payment, etc)
  * Easy Maintenance (it is not so simple. The major difficulty is that a complex solution gets simple. SOLID, Layes, Adapters, Interfaces, Design Patterns, Accouplements. Questions: It is easy to add new features? Is it easy to fix some points? There are Tests?
  * Portability (Ex: more than one database. OBS: it is not so easy to change databases, however, Will there be a lot of impacts if we change the Database? Ex: you are working with Elastic Stack, It will be easy to change to NewRealic? Maybe it will be better to work with OpenTelemetry. Ex: It is easy to change the Payment Gateway? Etc.)
  * Easy Support (Ex: logs, Debugging. A way to see the problems before the client calls the team. Observability in general)
    
3 - Cross-Cutting Features
  * Accessibility (Is it easy for other people to use the platform?)
  * Process of Retention and Recovery Data (How long will the data be saved? Ex: How long will the Data will be in a topic on Kafka? Ex: Keep the data in a storage that is less expensive. Ex: S3 Deep Archive)
  * Authentication and Authorization (Ex: Authenticate the user in the API Gateway, before it gets into the services, if we are talking about microservices)
  * Legal (Data conformity in Laws)
  * Privacity (Ex: LGPD)
  * Security (Web Firewall, Think the security before it gets into the service, Mechanisms to identify Bots, SQL Injection, Cross Site Scripting, Use everything that is open pattern (do not create anything))
  * Usability (not only in the frontend, but also in the backend: the api has documentation? Is there OpenApi? Is there a good contract to make available to others? Is it easy to reuse? Is there a README file?)

## Performance

- Focus: Reduce latency and increase the throughput

- Units:
  * Latency (Response time)
  * Throughput (how many requests the software can handle)

- A Performable Software is different than a scalable software

- How to perform?
  * Decrease the response time (if you are measuring in seconds, not in milliseconds, probably the software is not performable, depending in each case, obviously)
  * Check application processing, network and external calls
  * Increase the throughput (allow more requests)

- Main reasons for slow performance:
  * Insufficient processing
  * Limited computer resources
  * Work with a blocking way (find a way to not wait a single thread finish to receive other call)
  * Serial access (occurs when a software waits for a request to finish to receive the next one, such as a unique thread to receive all the requests)

- Main ways to increase the performance:
  * Scale the compute capacity (CPU, disk, memory, Network)
  * Logic behind the software (algorithms, queries, framework overhead)
  * Concurrency and Parallelism (work with a language that allows you to use it)
  * Database (types and schema)
  * Caching

- Vertical Scaling: Increase the compute resources
- Horizontal Scaling: Increase the number of machines or pods, putting a load balancer in front of them

- Serial: A blocking process that can do one thing each time
- Concurrency: To lead with a lot of things in the same time
- Parallelism: To do a lot of thing in the same time

- Caching:
  - Types:
    * Edge Computing: the cache is kept very near from the final user. Not only CDN (Ex: CloudFront, Cloudflare Workers, Vercel, Akamai), but also a proccessment near the final user (Ex: Lambda Edge)
    * Static: Images, CSS, etc (Ex: CloudFront)
    * Web: Cache without call the "backend"
    * Internal Functions Caching: 
      * Avoid reprocessing heavy algorithms
      * Avoid access the Database (very expensive: IO, network)
    * Objects: Using ORM
    
  - Exclusive VS Shared:
    * Exclusive: 
      - Processed in that machine (Low latency). 
      - It is duplicated among nodes
      - Problem working with sessions
    * Shared: 
      - Bigger Latency
      - A centralized cache
      - No cache duplication
      - Shared Sessions
      - External Database (Ex: MySQL, Redis, Memcache)

## Scalability

  - Focus: The possibility to increase or decrease the throughput adding or removing the computational capacity
  
  - Vertical Scaling: Increase the compute resources (there is a limit)
  - Horizontal Scaling: Increase the number of machines or pods, putting a load balancer in front of them
    * Attention Points:
      - Efêmero Disk (the data in the disk is lost): The disk is only for temporary files.
      - Application Server (app. this one that will be scalable) VS Assets Server (CSS, images, etc. are has to be in another server) 
      - Centralized Cache (Shared Cache. The cache will not be in the machine)
      - Centralized Sessions (In a cache server). The app does not keep state (It has to be Stateless). 
      - Upload (the files will not be kept in the machine)

  - Scaling the database:
    * Increasing the Computational Resources
    * Share Responsibilities (Read and Write). Ex: Create a Database for Read (Read Replica) and other to Write
    * Shards in an horizontal format. Ex: Add a lot of Read Replicas or change the database type
    * Serverless. (You do not worry about server level)
    * Query and Index Optimization
       - You have to have an APM to measure everything (doing some "explain" in the queries, to show each step and see which one is slow)
       - Work with Index in a consistent way
       - CQRS (Command Query Responsibility Segregation): A pattern to develop the software ("commands" to record the data and "query" to read the data)

  - Reverse Proxy:
    * Normal Proxy: When the user accesses some site, the proxy redirects it this site or other site (in case that is a malicious site)
    * Reversed Proxy: When the user accesses something, the proxy forwards the request to a server that the proxy knows that will answer the request to the user (it is a proxy that stays in front of web servers and has rules, forwarding the client requests to that servers)
      - Ex: a.teste.com -> A Server
      - Ex: b.teste.com -> B Server
      - Ex: NgInx (Pronunciation: Engine X) (the most famous), HAProxy (High Availability), Traefik 

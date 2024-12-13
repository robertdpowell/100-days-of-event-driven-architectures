# 100-days-of-event-driven-architectures

## Day 1 

Event driven architectures can enable agility.
- Producers and consumers can evolve independently.
- If consumer fails, producer is not necessarily impacted.

Organise business into domains, and organise teams around domains (Domain Driven Design)


## Day 2

Over time, we add producers and consumers to our architecture and we can end up with what is referred to as a **'big ball of mud'**.

Big ball of mud architectures are characterised by 
- Unclear domain boundaries
- Being hard to understand and change (hampers agility)

To avoid the ball of mud...
- Use **DDD** to define **boundaries, core domains and subdomains**.
- **Event storming and event modeling** are techniques to help with this
- Distinguish between private and public events. Private events stay within the same boundary. Sometimes it helps to include more implementation detail in our events, and that can be OK with private events as they do not escape the boundary. We need to be more careful with public events and design carefully to only share what is required.

Define a **common language** within a domain.

When interacting with an event, there are **context mapping** options
- e.g Conformist means to consume it as is, and be bound by the contract.
- e.g. we might wish to transform the event into something more useful for our need (and use a language more relevant to our domain)

## Day 3 

Batch processing and event streams are two methods of managing data within an EDA.

**Batch**
- Process lots in one go. For tasks that can tolerate delay and real-time is not a requirement

**Event streams**
- process data as it happens. Continuous flow in real time. Useful when real time insights are required - can give a competitive edge.
- Consider the business requirement and choose appropriately, bearing in mind the cost.

## Day 4

Today I looked at bi-directional patterns.

There are a number of event communication patterns we can consider:-

- Within services and boundaries
- Between organisations, as companies look to exploit the value of their data in real time.
- Between frontend and backend

I also read into bounded contexts, which is a central pattern of DDD and allows us to encapsulate parts of our system. Each booundary has its own language to define the events and schemas within it.

EDAs allow the decoupling of areas of our systems through definition of these clear boundaries. Decoupling enables flow.

## Day 5

- EDAs enable evolutinary design and implementation transformations.
- Consider a scenario where a legacy app raises an event for the new systems to listen to.
- Part of the transformation should be looking at the domain itself and whether it should be reflected as is in the future state.

- EDAs help us scale.
- Event storming and modeling help us to define our bounded contexts
- Implementing can also help us define these domains! Don't dwell too long in the theoretical space
- Domain discovery is a continuous process, not a one off event

## Day 6





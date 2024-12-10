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
- Hard to understand and change

To avoid
- Use **DDD** to define **boundaries, core domains and subdomains**.
- **Event storming and event modeling** are techniques to help with this
- Distinguish between private and public events. Private events stay within the same boundary. Sometimes it helps to include more implementation detail in our events, and that can be OK with private events as they do not escape the boundary. We need to be more careful with public events and design carefully to only share what is required.

Define a **common language** within a domain.

When interacting with an event, there are **context mapping** options
- e.g Conformist means to consume it as is, and be bound by the contract.
- e.g. we might wish to transform the event into something more useful for our need (and use a language more relevant to our domain)

## Day 3 

  

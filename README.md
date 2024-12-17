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

**Choereography** - using events to talk between services or bounded contexts, with services interacting independently.

**Orchestration** - flow of state handled by an orchestrator within a bounded context.


**Claim Check Pattern**
Store information first --> then send message to consumers. Allows us to avoid sending large amount of data in the event. We can share a key with the consumer, which allows the consumer to retrieve the data themselves.

This pattern helps us answer the question:- *How can we reduce the data volume of message sent across the system without sacrificing information content?*

**Analogy** - *dropping luggage at airport check-in and then retrieving it later with your barcode.*


## Day 7 

**Commands vs Events**

Commands represent the intent (think of a use case with a doing verb - PlaceOrder, RequestCredit) whereas an event is something that did happen in the past and is immutable (OrderCreated)

**Common Issues when Scaling EDAs**

- Keep a track of who is consuming which event, to help understand impact of changes to schemas and events.

- Make events discoverable. How will people discover events 2 years from now?

- In terms of coupling, remember that consumers rely on the contract of the event **and** the schema. 

- Create multiple versions of events and give consumers time to migrate

**Leaky events**

- Consider standards on what goes into our events
- Consider our domains and bounded contexts, to inform what should and should not be in an event
- Consider transforming events we consume to avoid external domain info leaking into our domain
  

## Day 8

**Content enricher pattern**
When downstream consumers need more information than is provided in the event.
With the content enricher pattern the enricher sits in the middle to pick up messages/events and enrich them (literally appends information to the message) before sending downstream to consumers.

This helps the consumer as they don't need to add the enrichment in their own domain.

Where does the enricher get its additional info from
- It might compute it
- It might retrieve it from another system
- It might collect it from its own environment (e.g. a timestamp).


BUT - consider this ---> if the consumer needs more information than we are providing, have we defined our payloads/boundaries correctly?


**Day 9**

Producers should not know about consumers. So how can we document our EDAs to help our stakeholders understand the landscape?

**Questions we need to answer in our documentation**

- What events is this service producing?
- What events messages can I consume from this service?
- What is the format of those messages?
- Which schema version should I use?
- Who is producing what?
- Who is consuming what?


**How to document?**

- Readme? But doesn’t fulfil discovery requirement.
- AsyncAPI
- Eventcatalog - opensource (add event catalogue to my product page)




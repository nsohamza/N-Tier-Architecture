# N-Tier-Architecture!
LEARNING PURPOSES AND DOCUMENTATION!
(https://i.gyazo.com/ee9cc96fa67f37fe03082e489d22b91c.png)

Layers:
Logical Structure: Layers are the logical separation of the components of your application into different categories based on their function. 

Layers are a way to separate responsibilities and manage dependencies. 
- Each layer has a specific responsibility.
- A higher layer can use services in a lower layer, but not the other way around.

Tiers:
Physical Deployment: Tiers refer to where these layers are physically deployed or run. 

Tiers are physically separated running on separate machines. 
Tier can have their communicationn modules be strict or relaxed. 
a request must go through adjacent tiers, one by one, and can't skip any tier in between. 
For example, from the web application firewall to the web tier, then to middle tier 1, and so on.
In contrast, in the relaxed approach, the request may skip some tiers if it's necessary.


The strict approach has more latency and overhead, 
and the relaxed approach has more couplings and subsequently it's more difficult to change.

Strict Approach: 
More Latency and Overhead: In a strict N-tier model, communication must go through each layer in sequence, which can increase latency. Each layer adds overhead in terms of processing time and network calls, especially if each layer is on a separate server or VM.
Advantages: It provides clear separation of concerns, making it easier to maintain, scale, and secure individual layers. Updates to one layer are less likely to affect others, enhancing modularity.

Relaxed Approach: 
More Couplings: Allowing layers to communicate more freely or directly bypasses some layers for efficiency, which can introduce more coupling between components. This coupling means changes in one part might require coordinated changes elsewhere, complicating maintenance.

The strict approach might be preferred for applications where security, clear role separation, and ease of maintenance are priorities, while the relaxed approach might suit systems where performance is critical, and the architecture is expected to evolve rapidly or where some level of coupling is acceptable for the sake of speed or ease of integration.

A tier can call to another tier directly, or use Asynchronous messaging patterns through a message queue.
Physically separating the tiers improves scalability and resiliency, but also adds latency from the additional network communication.

# A traditional three-tier application has a presentation tier, a middle tier, and a database tier. The middle tier is optional. More complex applications can have more than three tiers. The diagram above shows an application with two middle tiers, encapsulating different areas of functionality.

An N-tier application can have a closed layer architecture or an open layer architecture:
- In a closed layer architecture, a layer can only call the next layer immediately down.
- In an open layer architecture, a layer can call any of the layers below it.

In Simple Terms: 
- Closed is like a single-file line where each person (layer) can only talk to the person directly in front of them.
- Open is more like a classroom where anyone (layer) can pass a note to anyone sitting further back without going through the person in front.


# When to use this architecture
N-tier architectures are typically implemented as infrastructure-as-service (IaaS) applications, with each tier running on a separate set of VMs.
However, an N-tier application doesn't need to be pure IaaS.

Consider an N-tier architecture for:
- Simple web applications.
- A good starting point when architectural requirements are not clear yet.
- Migrating an on-premises application to Azure with minimal refactoring.
- Unified development of on-premises and cloud applications.

N-tier architectures are very common in traditional on-premises applications, so it's a natural fit for migrating existing workloads to Azure.


# Benefits
- Portability between cloud and on-premises, and between cloud platforms.
- Less learning curve for most developers.
- Relatively low cost by not rearchitecting the solution
- Natural evolution from the traditional application model.
- Open to heterogeneous environment (Windows/Linux)

# Challenges
-It's easy to end up with a middle tier that just does CRUD operations on the database, adding extra latency without doing any useful work.
- Monolithic design prevents independent deployment of features.
- Managing an IaaS application is more work than an application that uses only managed services.
- It can be difficult to manage network security in a large system.
- User and data flows typically span across multiple tiers, adding complexity to concerns like testing and observability


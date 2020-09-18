
* Architecture Types
* Business Architecture
* Technical Architecture
* Security Architecture
* Data Architecture
* Operational Architecture

An evolutionary architecture consists of three primary aspects
* incremental change
* fitness functions
* appropriate coupling

An evolutionary architecture supports guided, incremental change across multiple dimensions. The word guided indicates that some objective exists that architecture
should move toward or exhibit.

An architectural fitness function provides an objective integrity assessment of some architectural characteristic(s).

The fitness function protects the various architectural characteristics required for the
system. The specific architectural requirements differ greatly across systems and
organizations, based on business drivers, technical capabilities, and a host of other
factors. Some systems require intense security; others require significant throughput
or low latency. 

 systemwide fitness function as a collection of fitness func‐
tions with each function corresponding to one or more dimensions of the architec‐
ture. Using a systemwide fitness function aids our understanding of necessary
tradeoffs when individual elements of the fitness function conflict with each other. As
is common with multifunction optimization problems, we might find it impossible to
optimize all values simultaneously, forcing us to make choices. 

it is good to never try to “evaluate” this systemwide fitness function. Rather, it provides
guidelines for prioritizing decisions about the architecture in the future.

real-world architecture consists of many different dimensions, including requirements around performance, reliability, security, operability, coding standards, and integration, to name a few. 

Adding evolvability to existing architectures depends on three factors: component coupling, engineering practice maturity, and developer ease in crafting fitness functions.

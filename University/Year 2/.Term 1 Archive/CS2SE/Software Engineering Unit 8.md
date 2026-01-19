### Lecture 7/8
The past units have discussed analysis - what the system or software must do - but we also have to "design" the system - define how it works. We specify a system that fits the business, its requirements and assists it to meet its objectives.
"Logical" design refers to design elements independent of the implementation language or platform, such as UI or types of fields or position in windows.
"Physical" design is constrained by the implementation language or platform.
The two types being distinct is useful if we're producing software for multiple platforms. But there is also "System" and "Detailed" design.
System design deals with the high-level architecture of the system, including sub-system structure and their interactions, etc. Detailed design deals with inputs, outputs, processes etc.

A good quality design is functional, efficient, economical, reliable and secure. It is realistically buildable, maintainable, usable, reusable and flexible.
There are also incompatible design traits which will lead to trade-offs, e.g., functionality/reliability/security can conflict with economy at times, so there needs to be priorities in the design choices (discussed between developers and clients).

"Trustworthy programming" - Trustworthiness seeks to address the quality and robustness of software, ensuring that the software performs as it should, when it should and how it should. (UK-TSI, 2016).
BS 10754-1:2018 Systems Trustworthiness is a publicly available specification hosted by the British Standard Institution.
To sum it up, there are five facets of trustworthiness (set by the Trustworthy Software Foundation):
- Safety
- Reliability
- Availability
- Resilience
- Security

The guidance document should also set out the baseline requirements of trustworthiness during the software's life cycle (UK-TSI, 2016):
- Scope for use
- Coding practices
- Using tools effectively
- Defect management
- Artefact management

Structure and behaviour of the system's components is defined by architecture, as well as it balancing stakeholders' possibly conflicting needs and following a particular scope.

Sub-systems are groups of system elements that fall under common properties, which allows us to produce smaller units of development in a possibly complex system and maximise our reuse/maintainability/portability at the component level.
There are two approaches to dividing a system into sub-systems:
- Layering - different sub-systems represent different levels of abstraction (think of the Business Process Map).
- Partitioning - each sub-system focuses on a different piece of functionality.
We can see both approaches utilised in a single system.
![[{13D1B864-76D0-4735-A334-CEBA0567646A}.png]]
A layered architecture is a logical structuring - it groups code and functionality based on its level of abstraction, all layers of which can reside on the same computers.
A tiered architecture is a physical structuring - it also concerns the logical grouping of functionality and code, but tiers reside on and are executed by different computers.
![[{2B9F2C35-0851-49F6-94CA-0BF7C9945614}.png]]
![[Pasted image 20260107055952.png]]
Some architectures can end up with multiple interfaces for the same core functionality:
![[{2789ADF5-D17C-4A43-AFB7-3F9A3EF1ABC7}.png]]
Now let's look at the Model-View-Controller:
![[{664DA3C2-7E4D-4073-82EE-AB0630DBC8C1}.png]]
The "Model" is the data and rules governing access and updating of the data.
The "View" renders the contents of a model and update its presentation as needed. The view can register itself with the model for change notifications, or call the model for up-to-date data.
The "Controller" translates user interaction with the view into actions that the model understands and can perform. In an isolated GUI client, user interactions could be button clicks or menu selections, whereas in an enterprise web-application they appear as GET and POST HTTP requests.
Below is a UML Class Diagram of the above model:
![[{773F6455-EF8A-4DCA-A53C-79492965E93E}.png]]
"CalcMVC" is the top-level class, creating the model, view and controller objects.
"CalcModel" has no access to the view or controller and notifies its subscriber (the view) of any property change notifications.
"CalcView" renders data from the model through a GUI and subscribes to the property change notifications from the model, passing user input events to its subscribers (CalcModel and CalcController).
"CalcController" subscribes to all user input events, defines event handlers for GUI events and calls the model to change its state based on the user input events.
Here's a code-example of CalcMVC:
![[{CD0FCAC6-EF55-4DD0-817A-54688C72D743}.png]]
Also a single model of an MVC with multiple views:
![[{8633B494-DD0E-4DD3-925D-5FB07FAE97E7}.png]]
To put it lightly, the MVC architecture is pretty flexible. It can involve multiple views, and changes made to a model with one view will affect any other view that utilises the same model.

Sub-systems can provide services for other sub-systems. This is done through two types of communication - client-server and peer-to-peer.
![[{95695682-BB08-4AFC-A689-5BBC6B080EFC}.png]]
Client-server communication requires the client to know the interface of the server sub-system, as the communication is asynchronous.
The client sub-system requests services from the server, as a consumer while the server is the supplier. We can find examples of this set-up in most network-based applications like email systems.
Peer-to-peer communication requires each subsystem to know each other's interface, coupling them more tightly.
Each peer needs to be running the same program, providing identical services. This means it is two-way communication.
To find a peer with the information you need, you can use a Centralised Model (used by Napster, the music platform), Flooding (used by Gnutella, a P2P service) or a Distributed Hash Table (used by Kademlia, Chord, other examples of P2P services).
![[{14F1F9F4-6F91-493D-A0A6-435FFAA89EEF}.png]]
![[Pasted image 20260107061203.png]]
![[Pasted image 20260107061227.png]]
Torrent file-sharing systems use distributed hash tables to facilitate storing and retrieving large files. Each peer knows which portions of files it keeps, and where to look for other chunks from peers, through a key-value stored in various nodes of the network. By contrast, in a blockchain each network node stores the full ledger of transactions.

Large distributed systems can use Service-Oriented-Architecture (SOA) in their design, which is the invocation of remote services. 
A service typically refers to a Web service, which communicates via Internet protocols such as HTTP and send/receive structured data like in XML or JSON format. 
In a SOA, services interact via a common communications protocol, the resulting components are loosely coupled with each other.

For example, let's say there is a network of Web services comprising and supporting travel agents, composed of services for booking flights, hotels and car hire. Agent applications will use these services to create complex holiday-package services for their clients.
![[Pasted image 20260107061648.png]]
Each bubble above is a service, potentially provided by a different vendor, using another service to complete its task. It should be easy to switch between similar types of services even when provided by a different vendor.
![[Pasted image 20260107061850.png]]
Reusable logic can be divided into services.
Services share formal contracts, especially in information exchange.
These services are loosely coupled.
Services abstract underlying logic, the only part of the service visible to the outside world is what the service's description exposes.
Services can be composed of other services, also referred to as being composable.

Business use of SOA promises easier reuse of services for multiple purposes, better adaptability, the ability to integrate new and legacy systems and the ability to cheaply set up e-business links across the entire world.
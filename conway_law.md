Proof of Conway law
==

Updated: 2015.08.22.

Visual proof
--

### Conway law

Conway's law states that

> organizations which design systems ... are constrained to produce designs which are copies of the communication structures of these organizations

-- **[Melvin E. Conway: How Do Committees Invent?](http://www.melconway.com/Home/Committees_Paper.html)**


A simple visual proof using the concept of the original paper is the following:

![](img/conway_law.png)

### structure of the system

1. Complex systems are typically designed using a divide-and-conquer approach. That is **the system is decomposed into smaller subsystems**, until the complexity becomes manageable by the individual designer (or designer group).
2. **Subsystems need to communicate each other** (in some meaningful way specific to the domain the system deals with). This is necessary in order to act as a whole, that is as a system.
3. **Subsystems and subsystem communications define a graph-like structure** where the nodes are the subsystems and the edges are the direct communication links between subsystems. 

### *designed by* relation

1. **Every subsystem is *designed by* a designer** (or designer group), which then creates a mapping from subsystems to designers (or designer groups). 

Note that: The above *design by* relation is called an `N:1` relation in the database engineering world, since (a) the same designer could design many subsystems and (b) each subsystem has a designer.

### relation between system- and human communication links

1. **When two subsystems communicate each other, they require an agreed upon contract which governs their communication.** 
2. **This contract (since it is a contract) should be based on the agreement between the corresponding designers.** That is it must be the result of some cooperation between the designers of the two subsystems. Since cooperation needs some communication, hence: 
3. **There should be a communication link between the designers who designed such subsystems which directly communicate each other**. This then creates a mapping between the (communication) links of the subsystems and the (communication) links between the designers who designed them. 

### a special case

There is the special case, when the two subsystems are designed by the same designer. So generally we can say the following:

5. **Each communication link of the subsystems is either (a) mapped to the same designer if she designed both systems or (b) mapped to two designers if different persons (groups) designed them. Either the designer is the same, or at least they communicate each other**.


Practical considerations
--

### A common misunderstanding

A common misunderstanding of the law is that (it states that) every system mirrors the static structure of the organization who designed it. Conway law does not state that:

* The "static structure" often means the functional decomposition of the organization, ie. the organization split into functional organization units dealing with regular/recurring tasks.
* Meanwhile "organization structure" in Conway law does not mean anything but the communication structure during the design of the system and between the designers of the system. 

If we want to seek a common term that is close to the above meaning then it would be rather the "dynamic structure" or "project structure" of the organization. But even this could be different (ie. if the project structure diverges from the real relationship between designers). 

When Conway law speaks about organization structure it speaks about two things:

* the communication structure, ie. the communication of designers
* the politics governing/constraining such communication

It is the latter which shares some relation with the organization's static structure. Ie. the communication politics/constraints could be rather static, which leads to the following:

### Communication constraints

If the communication paths between designer organizations are constrained by some rules (ie. there are restrictions on who can talk to whom), then the same rules would constrain the system itself as well. Or by  the original words of Conway:

> organizations which design systems ... are constrained to produce designs which are copies of the communication structures of these organizations. 

### Developers vs. designers

In the IT world there's a tendency to blur the frontier between designers and programmers (ie. *eat your own dog food*). Hence within the IT domain, nowadays one may replace *designers* with *developers* in the above statement. Note that there is an emphasis on "IT domain", since Conway law applies to other domains as well, not just to the IT domain.

Quasi-formal proof
--

The above informal proof could be more-or-less formalized if the core terms/assumptions are defined. Let's do that:

### Terms

Let's collect terms first:

1. **Communication structure** means the communication between designers which yields a graph-like structure, where (I) vertices represent designers, and (II) edges represent communication links between designers (who communicate each other)
2. **Communication** means either direct or indirect communication between parties (see further questions below for more details).
3. **Structure of the system** is the decomposition of the system into subsystems, which again yields a graph-like structure, where (I) vertices are subsystems and (II) edges are the links between subsystems directly communicating each other.
4. **Designed-by** is the relation between a subsystem and its designer

### Statement

After all the law states the following:

**The communication structure is the homeomorphic image of the system's structure using the designed-by relation as the mapping between the two**.

In order to prove the above statement, the basic premises should be also defined:

### Premises

Conway theorem builds upon the following premises:

1. **Designed-by relation is well defined**: For each subsystem there is a designer who designed it (ie. the designed-by relation is defined, in fact it is an N:1 relation)
2. **Integration relies upon (API) contracts**: If two subsystems communicate each other then there must be a contract (API or kind of) between them. 
3. **(API) contracts relies upon agreement**: If an (API) contract exists between two subsystems then there must be an agreement between the parties who designed the subsystems.
4. **Agreement relies upon communication**: If an agreement exists between parties then they communicate each other.

### Proof

The proof is evident, in fact the visual proof already did the work when using the above terms/premises as evidences. That is to say, if the above premises are true, then Conway law is true as well.

Further questions
--

Now let's do the opposite and question the core terms/premises behind Conway law:

### Direct vs. indirect communication

IT produces many open standards/interfaces, which then yields a slightly  different type of cooperation/agreement between developers, different from direct peer-to-peer agreements. 

For instance both webservers and web browsers should adhere to the http specification, however this does not necessarily mean that each webserver/browser developer participated in the HTTP specification or directly communicated.

This means that the meaning of "communication" should be probably extended to cover indirect communications as well (like communication through (open) specifications).

### Cross-system contracts

Another interesting phenomenon could be the following: 

Sometimes business processes/rules span many subsystems. In this case the "contract" (participating subsystems must adhere to) does not just effect the nodes linked directly (ie. the direct communication links), but the set of participating systems taken as a whole (linked either directly or indirectly).

This may yield a slight extension of Conway law (?!). That is, it might not be enough just to ensure peer-to-peer communications (associated with peer-to-peer relations between subsystems). In some cases it might be necessary to ensure communication between a set of parties.

Note that from the (communication) complexity point of view this phenomenon would yield exponential complexity `O(2^n)` (ie. one has to deal with each subset of  the peers). This is in contrast with the linear `O(N)` or quadratic `O(N^2)` complexity of peer-to-peer communications (ie. linear in a tree-like structure and quadratic in a free-form graph).

### Designer is changing

What does happen if the designer of a subsystem changes? How does it effect Conway law?


History
--

* 2015.08.22 - Description of a common misunderstanding, added quasi-formal proof
* 2015.06.01 - Original version

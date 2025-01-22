# Softening CAP limitations
2025.01.23.

There is a phenomenon related to CAP, a new kind of CAP softening which I encountered in a previous project, but I didn't have time to analyze it in detail then. Now I encountered a similar case again in a new project:

## Context

Given two systems, let's call one an Application, the other an Operation. Both systems work on the same resources. For instance in SCADA the resource can be a power plant, where the Application is production control, and Operation is remote monitoring. 

Since the two applications work with the same resources, the control must be synchronized between them: both systems cannot have the control over the same resource at the same time. For instance in the SCADA case, a generator can only be put into maintenance if it is taken out from production so the control must be synchronized between the two. Enter CAP:

## Consistency

In our setting, two types of inconsistencies could theoretically occur:

1. When both systems believe that they have control
2. When both systems believe that the other has control over the resource

In the event of a link failure (aka network partition), according to the CAP-theorem the consistency and availability of the systems cannot be ensured at the same time. Thus, this case, both cases of inconsistencies cannot be handled, at least not without sacrificing availability. However, it seems that either one of them can be handled even with providing high availability.

Of the two cases, the first seems to be the more serious: it should be automatically prevented that both systems do not take the control over the same resource. A simple solution to this is to introduce an ACK protocol. The Operation only takes control over the resource once the Application has acknowledged that it has released the control. (This way, the first inconsistency case can be prevented but the second case can still occur in case the ACK fails).

## CAP softening

In the above protocol, availability (the A of CAP) is guaranteed in all cases. As for consistency (the C of CAP)... we protect one type of consistency (controller is unique) at the cost of allowing the other type of inconsistency (control may be lost, at least for a while). That is in this case, we always guarantee the availability (A), but we also guarantee the consistency (C) partially. 

This then can be considered a new kind of "softening" of the CAP theorem. As a reminder, the well-known "softening" of CAP is Eventual Consistency, when the C converges: the systems eventually converges to the same state. There is however more to it here, since consistency is always guaranteed for one part and in the part where it is not, it can still converge.


## Closing question

Have you ever met similar case in practice? Such as when consistency can be maintained partially while also maintaining high availability...

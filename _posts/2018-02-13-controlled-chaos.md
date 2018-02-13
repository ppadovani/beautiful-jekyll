---
layout: post
title: Controlling Microservice Chaos
bigimg: /img/microservice-hell.png
---

Microservices are the new big thing, and they are not without their pitfalls. This 
[blog post](https://www.linkedin.com/pulse/dependency-hell-microservices-how-avoid-nabil-hijazi/) talks about how to
control the dependency hell that comes with microservices. However, one issue that seems to be missing
in the discussions around microservices is system control.

![https://commons.wikimedia.org/wiki/File:STS-128_MCC_space_station_flight_control_room.jpg](/img/complex-control.jpg)

Let me ask a hypothetical question that assumes you have deployed several thousand micoservices: 

***How would you put the entire system, or a sub-system, in read-only mode?***

Let’s say you needed to go into read-only mode in order to perform some backend maintenance, while still allowing read access. How do you tell some or all of the services to disallow writes? How do you keep track of which services need to be told? Adding an additional level of complexity, what if you were managing a multi-tenant system and wanted to only put a single customer in read-only mode?

Assuming you knew which services needed to be controlled, a single script that made a call to each would do the job. In the world of microservices, this list may change at any time so how would you keep it up to date? Thanks to [Jim Snyder](https://www.linkedin.com/in/jamessnyderii), at [Civitas Learning](https://www.civitaslearning.com), we found a solution pattern that turns this problem on its head.

Instead of trying to keep track of what services should be affected by what system control operations, instead have each microservice know how to handle specific system control operations. Then by simply creating a single system control operations messaging channel in 
a product like Kafka, each service would get the operation and act on it if it were applicable. 

This pattern of central system control using messaging operations, provides the flexibility needed to help tame the microservice hell.


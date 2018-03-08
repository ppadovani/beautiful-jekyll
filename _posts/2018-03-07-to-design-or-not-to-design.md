---
layout: post
title: To Design or not to Design, that is the question.
bigimg: /img/2018-03-07/800px_COLOURBOX4293478.jpg
---

Software engineering is much like any other engineering field, in that math and science is required in order to build
a working system. What is different is the design process, and how much design should actually be done.

![https://www.breakoutsmart.com/partners/](/img/2018-03-07/airplane-blueprint.jpg){: .image-left }
When we think of engineering designs, I would guess that one of the first things to pop into our heads is an image
of a blueprint. In most engineering professions, design is an iterative process, but most designs will be extremely
detailed and thoroughly thought out. One of the primary reasons for this is that a fault in the design may actually
kill someone. Would you want to fly on a plane or drive a car that hasn't been thoroughly designed?

I talked about the agile development process [in a previous blog post](2018-02-12-corruption-of-agile), which briefly
mentioned design as part of the process. Before a software project can even be started, a certain amount of upfront
design must take place, for without it the software engineers writing the code would have no idea exactly what the 
 software should do or how the software should be built. So how much design must be done?
 
***Answer: It depends.***

It depends on the phase of development the project is in as well as the kind of project that is being built. Software
control systems for airplanes, cars and other life or death pieces of engineering, are outside the scope of this 
discussion, but do require an extreme amount of design discipline.

## The Prototype

So you have a product/software idea that you believe will be successful in some fashion. How do you start the design?
Do you already know what technologies you are going to use and how to use them? If the answer is no, then generally
a software team will begin prototyping. Almost no design is done at this phase, there is a general understanding about
what the product will accomplish, but not how it will be put together. 

The prototyping is done in a quick and dirty manner, with little regard to full functionality or even testing. It is 
simply a way of testing technologies that may or may not be applicable to building the final solution. It is all about
***learning in order to design***. 

![danger](/img/2018-03-07/danger.png)
One of the biggest mistakes a software engineering team can make is to not stop prototyping, and continue to build
out the software solution based on the prototypes. They may feel like they have something that works, and demo
that to management who enthusiastically push the development team to finish. The amount of hacking typically done during
a prototyping stage can lead to an incredible amount of technical debt as well as scalability and performance problems.
It could cost a company more to unwind the prototyped code and build out properly designed code, than it would have
taken to just do a little upfront design after a completed prototype.

## The Design 

![https://towardsdatascience.com/10-common-software-architectural-patterns-in-a-nutshell-a0b47a1e9013](/img/2018-03-07/software-design.png){: .image-left } 
Once the basic understanding around the technologies and goals have been defined, the real designing of the 
software can be done. In simple cases it doesn't take long, in others the overall system complexity might lead
to a much longer design cycle. In all cases the initial design will block out the basic building blocks of the
software in order to understand the work breakdown and delivery order. 

It is tempting for many software architects and higher level engineers to continue down the design path and dive into
the minute details of each broken down component or system. In fact many a time, I've seen ***analysis paralysis*** 
happen because engineers feel that they must design for all cases, known and unknown, before starting to write code.

Knowing when to stop designing is just as important as knowing when to stop coding and go back to designing. Look, one
of the greatest benefits of software engineering is the ability to quickly iterate on designs. Embrace the plain and
simple fact that the first design, no matter how hard you try, is going to have flaws. Here are my simple rules for
knowing when to stop the design and start the coding.

### Time 

Time is always a limit. You cannot design forever. Be cognizant of delivery time lines, and cut off design time in order 
to meet them. If you keep this in mind when you start, you will begin to look for patterns that can be reused and reduce 
design burden.

### Feature Creep

When you start to design in features because you think they will be needed, but haven't been asked for. Be very critical
when you start injecting additional features outside the initial scope. Ask hard questions: ***When would this be used? 
Now? A year from now?*** If the answer is not in the near term, drop it and move on. I must admit, I've even failed with 
this one.  

### Over thinking

This one is interesting to me. I've seen many an engineer work on a design task, and begin to over think the problem. 
They get stuck working out exceedingly esoteric edge cases either in hopes of not producing a design with flaws, or
to ensure that the developers that are implementing the design will not have any questions. Another aspect of this, 
is where an engineer will produce a very complex design that was very well thought out, except a much simpler solution
exists that they considered and threw out ***because*** it seemed too simple.

When it comes to design there is a spectrum of level of effort that engineers fall into. Some prefer minimal design 
and maximum coding, and others are the opposite. In my opinion the most successful software engineers are the ones
that are self critical enough to know when to stop designing and start coding. The most successful software teams are
led by seasoned engineers and managers that are able to properly manage the design process to its fullest potential.

In case you are wondering, I fall into the side of the spectrum where I would rather code than design.

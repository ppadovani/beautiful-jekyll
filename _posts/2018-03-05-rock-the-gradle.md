---
layout: post
title: Rock the Gradle
bigimg: /img/2018-03-05/rock-the-gradle.png
---
For those of you out there that are software engineers, how many build tools have you seen over the course of your
career? The newest *fad* in build tooling is called Gradle. I'm just going to come out and say it. ***I HATE GRADLE!*** 

From [Wikipedia](https://en.wikipedia.org/wiki/Gradle):

*"Gradle is an open-source build automation system that builds upon the concepts of Apache Ant and Apache Maven and 
introduces a Groovy-based domain-specific language (DSL) instead of the XML form used by Apache Maven for declaring the 
project configuration. Gradle uses a directed acyclic graph ("DAG") to determine the order in which tasks can be run."*

## In the Beginning 

![https://dribbble.com/shots/2738115-Makefile-Logo-v2](/img/2018-03-05/makefile-logo-v2_1x.png){: .image-left } 
Ok, lets first talk about build tool evolution and go back in time a bit. One of the first standardized build tooling
systems was based on a system called Make. Make required that developers build Makefiles that knew what specific steps
were required and in what order. There was no dependency management, or easy ways to pull in 3rd party tooling to 
help build or package your final project. In all honesty it wasn't a bad system for the time, and was an improvement
over what existed before.  It is still in heavy use today, with improvements that have helped solve some of the
underlying issues developers had with the tooling in the past.
  
## Apache Ant

![gradle icon](/img/2018-03-05/ant_icon.png){: .image-left } Ant (A Neat Tool) came into being because some Java developers 
found that Makefiles, at the time, were too limiting, and didn't meet the needs of the Java language. One of the 
fundamental differences between a Makefile and an Ant build file is that the Ant build file was written in XML. 
Additionally, Ant had a built in mechanism for limited dependency management meaning it sort of knew what pieces
of code needed to be rebuilt when. Ant made building Java projects easier than using a Makefile.

## Apache Maven

![maven icon](/img/2018-03-05/maven_icon.png){: .image-left } Maven is to Ant as Ant is to Make. Maven is a further refinement
of Ant in which less is more. Fewer lines of XML need be written, and more reusable functionality is provided. Maven
provides the ability to download require dependencies from global repositories automatically, as well as providing 
out of the box packaging tooling. Additionally, a plugin system was created to allow for anyone to write a custom
maven plugin to perform specific actions needed for their project. Maven, like Ant, was primarily build for, and is 
in use by Java developers. Maven made building Java projects easier than using Ant.

## Gradle

![gradle icon](/img/2018-03-05/gradle_icon.jpg){: .image-left } The intention of Gradle is to continue to the evolution of
build tooling. Gradle throws away the XML format adopted by Ant and Maven and instead introduces the requirement to
know and understand the Groovy DSL. It provides a plugin system that allows anyone to write a new piece of 
functionality, and additionally provides the ability to extend existing tasks and override or extend them. For a simple
Java project, the build file can simply be a single line.

## Why the Hate?

![haters_meme](/img/2018-03-05/haters_meme.jpg)
 
I've recently had the *pleasure* of working on a complex set of projects that use Gradle as the base build system.
My pet peeves:

  * Simplified Gradle build files were nowhere to be found.
  * Poor documentation
  * Black-magic functionality was hidden deep down in an obscure plugin
  * External dependency management of a moving SNAPSHOT sometimes required that I delete the cached version.
  * ***I had to learn a programming language in order to write a build file***
  
I want to emphasise the last point. The evolution of build tools took us from a sort of scripted file with Make, to 
a configuration based set of tooling (Ant and Maven) based on simple XML. Now the [new fad](2018-02-06-new-addiction) 
is to go backwards to a more complex system where it is required to learn another programming language in order to 
build software based on a different programming language?!?!?

So, is 'hate' too strong a word here? I learned and fought the build system for most of a week as  I worked to get a 
deliverable completed. There were times it was frustrating, baffling, obtuse and output cryptic error messages. So,
what did I learn?

I learned that I hate it when technologies are adopted because they are new, when the old can accomplish the task
just as well. 

I learned that Gradle is barely usable, and I have no intention of attempting to maintain the build system. They
made it, they can maintain it.   

Maybe the next build tool that comes out I'll hate less.
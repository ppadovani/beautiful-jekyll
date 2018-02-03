---
layout: post
title: The shortcut to nowhere.
---

Since last fall, I've been mentoring a [FIRST](https://www.firstinspires.org/robotics/ftc)
robotics team at my kids high school. I've guided and watched this team design and build a robot to
compete with against other schools. They spent time and effort creating some CAD models, but in
the end they took shortcuts during the build. Duct tape and zip ties were most definitely harmed
in the making of said robot. They did reasonably well during their first two meets, but the robot began
to have significant technical issues during the third.

![© Eduardo M.](/img/road-to-nowhere-sao-paolo-brazil-3759050855.jpg)

Observing this team take shortcuts provided me an opportunity to reflect on how similar
decisions are made in the software industry. I've been in the industry for many years
and have seen shortcuts made by ***both*** engineers and management that have come back 
and haunted them. 

![rube goldberg](https://i.imgur.com/ynqc5zu.gifv)

Years ago, I was tasked with rewriting a Java applet that ran in a web browser to a Javascript
equivalent. The main thrust behind this effort was to avoid some of the support costs incurred
with a Java applet, and to work out a path that would lead to introducing new features in the 
future. I delivered the updated functionality, and during a final feature inclusion 
meeting with the product manager, was asked:
 
***What new features does this provide?***

Well, in all honesty I only had time to create a functionally equivalent piece of code. The product 
manager told us, over our objections because of the sercurity issues with Java applets at the time, 
to **NOT** include this work in the product release. The product manager took a shortcut, to 
avoid extra work and possible costs. 

We released the product.

One month later all browser vendors rolled out a patch to disable Java applets.

![facepalm](/img/picard-facepalm.jpg)

Here is what I grok:

There is a time and place where shortcuts bring great value. However, in the end shortcuts will always 
come back and haunt you.

Oh, and that robotics team I am mentoring? After that last meet, they spent the time to re-CAD 
and rebuild the portions of their robot that they took shortcuts on. The robot is much more reliable
now, and they are continuing to compete. 
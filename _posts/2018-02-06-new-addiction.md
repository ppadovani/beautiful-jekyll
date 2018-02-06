---
layout: post
title: The 'New!' Addiction
bigimg: /img/new_awesome.png
---

In this day and age we are inundated with ***NEW!*** and ***AMAZING*** must have pieces of 
technologies. Everything from smartphones to 4K flatscreens to drones. There are times where
adoption of something new seems like the right decision, but is it?

![businessinsider.com](/img/iphone-upgrade.png)

The above chart from [Business Insider](http://www.businessinsider.com/iphone-upgrade-sales-data-2017-2) talks about the 
iphone upgrade cycle, and shows how the number of new iPhone users acquired per year decreases, while the number of 
upgrades increases. How many of those upgrades were due to real need versus ***"I gotta have the new model!"***? 
Yes, yes, I know some of you out there attribute the upgrade cycle to the evil Apple empire and forced upgrades due to 
the integrated battery. Really though, look at the consumer electronics industry and how they push the
new technologies like 4k flatscreens. Do you **really** need that over what you might currently have?

Ok, so what about outside the consumer space? I'm a developer by trade and a geek by nature, and new
libraries, frameworks or tools that promise to make my job easier are always appealing. What about 
Javascript frameworks? Well as it happens, this new addiction seems to affect Javascript libraries as well.

![https://stackoverflow.blog/2018/01/11/brutal-lifecycle-javascript-frameworks/](/img/javascript-trends-minor.png)

There is a great [blog entry from Stack Overflow](https://stackoverflow.blog/2018/01/11/brutal-lifecycle-javascript-frameworks/) that discusses 
the lifecycles of Javascript libraries. Very much worth a read. Then there is this little gem I ran across:

![https://github.com/jgraph/mxgraph](/img/mxgraph-disclaimer.png)

So what if you **must** adopt a new technology, how do you choose? How do you know which to risk your future on? Unfortunately
it comes down to a business decision around the risks involved. 

* Unseen costs for transitioning
* Library/product maturity
  + Stability
  + Support
  + Release cycle

Sometimes you understand the risks, and have to adopt the new technology anyway. I worked for a company that
decided to roll out Apache Kafka in a big way. At the time we knew that there were maturity issues, training costs
and migration costs for moving away from RabbitMQ. Much pain was self induced, and after almost a year of work
a full stable production deployment was achieved, and deemed worth the costs inccurred. 

Bottom line: Don't become blinded by the 'new', and evaluate objectively.

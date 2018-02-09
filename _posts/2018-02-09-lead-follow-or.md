---
layout: post
title: Lead, follow, or ? 
---

Have you ever given advice, technical or factual, only to have it ignored? Then watched those
advised as they blithly drive off a cliff or into a wall because they chose to ignore the 
advice? I've seen this scenario play out many times, and found that how you approach those
needing advice matters. A lot.

Do you remember the robotics team I [mentioned in a previous blog post?](./2018-02-02-shortcut-to-nowhere) 
As a mentor, my responsibility was to provide advice and guidance around both software and hardware
as they moved through their build cycle. As I'm sure everyone knows, high school aged kids generally don't 
like to listen to adults telling them: they did something wrong; what to do; or how to do it. 
(Ok, raise your hand if you know an adult that behaves the same way!) So, how did I handle this?

![http://latestimageswallpapers.blogspot.com/2013/08/2d-animation-refeerence-gif-images.html](/img/099-tiptoe.gif)

Very carefully. I was lucky in that all parent mentors were given advice from the lead teacher on ways 
to handle the students. 

* Build up trust by respecting their opinions, and **LISTENING**.
* Treat them as adults in the discussion, don't talk down to them.
* Ask them questions to help them think through the problems.
* Do not, get frustrated if they don't follow your advice. 
* Let them fail at times if that is where things are headed, but try and get them back on track.
* Above all do ***NOT*** dictate what or how something should be done.

So how about leading in the workplace? Honestly as I think back, many of the above rules *STILL* apply
you just have to know which to apply and when. 

Years ago I was dealing with a particular gnarly piece of
code, *that I did not own*, that had to be thread safe. (This means that more than one active processing 
task could be executing the code at the same time.) To be thread safe, code must be very careful about
 what in memory they modify in order to avoid corrupting or changing the data in unpredictable ways. I
discovered that the code was not in fact thread safe, and would throw an exception(error) under very
specific conditions.

When I initially pointed out the issue to the owner of the code, there was much denial that there was
any issue. So, I took a different approach. I asked them to sit down and go through the code line by
line so that they could help me understand the code better. I played dumb. In actual fact, I was using this as an
excuse to ask probing questions around the specific location within the code that was at fault. In the
end I was able to get the developer to grasp the subtle defect in his code that was at fault.

I don't profess to be an expert, but I have found more often than not that leading by dictating isn't as
nearly as effective as following one or more of the rules above.

Advice given. Your milage may vary.

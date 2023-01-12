---
layout: page
title: Calendar
nav_order: 3
description: Listing of course topics and due dates.
---

# Course Calendar (Topics and due dates)


Each week corresponds to one Chapter in the zyBook.

"Week 1" in zyBooks is effectively Chapter 1 and so on.

We have the following course activities that need to be completed in zyBooks on a weekly basis: 
* **PA**{: .label .label-orange }(Participation Activities), 
* **CA**{: .label .label-blue }(Challenge Activities), 
* **LA**{: .label .label-green }(Lab Activities).

All due times in our class are at **11:59PM Pacific time **.


<!--[Jump to the current week]({{ site.url }}{{ site.baseurl }}/calendar#week-1){: .btn .btn-blue }-->
{% for module in site.modules %}
{{ module }}
{% endfor %}

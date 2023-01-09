---
layout: page
title: Who We Are
nav_order: 6
description: A listing of the course staff.
---

# Staff

The course staff includes the instructor, graduate teaching assistants (TAs) and undergraduate learning assistants (LAs).

If you want to contact us, please use Piazza rather than email or other means of communication; this helps us:

* keep track of whether your query has been answered
* better share the workload to answer your questions more quickly

## Instructor

{% assign instructors = site.staffers | where: 'role', 'Instructor' %}
{% for staffer in instructors %}
{{ staffer }}
{% endfor %}

{% assign teaching_assistants = site.staffers | where: 'role', 'Teaching Assistant' %}
{% assign num_teaching_assistants = teaching_assistants | size %}

{% if num_teaching_assistants != 0 %}

## Teaching Assistants

{% for staffer in teaching_assistants %}
{{ staffer }}
{% endfor %}
{% endif %}

{% assign learning_assistants = site.staffers | where: 'role', 'Undergraduate Learning Assistant' %}
{% assign num_learning_assistants = learning_assistants | size %}
{% if num_learning_assistants != 0 %}

## Undergraduate Learning Assistants

{% for staffer in learning_assistants %}
{{ staffer }}
{% endfor %}
{% endif %}

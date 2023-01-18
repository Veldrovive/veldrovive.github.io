---
layout: post
title: "Task Assignment Problem"

demo_url: '/projects/multi-agent-control'
demo_url_text: 'Main Project'
---

In my quest to build a [system that can coordinate multiple robots](/projects/multi-agent-control) to execute complex tasks, one of the most important building blocks is the task assignment algorithm.

## The Problem
We can state the basic premise as: Given a dependency graph of tasks and a set of agents that have a set of abilities, how do we assign tasks to agents such that we can minimize metrics such as completion time, cost, and energy consumption?

We must also acknowledge that for this system to be useful, it needs some further capabilities.
* What if in order to complete a task, the agent first needs to have completed a prerequisite task? In a single agent system, this is trivial because the dependency graph already ensures that, but with multiple agents it is possible that the prerequisite task is assigned to a different agent.
* What if a task uses multiple agents instead of just one? Or similarly what if this task should be completed by all agents that have completed some previous task?
* How can we effectively plan given uncertainty in completion time?

We will tackle these as we go along, but first, the initial problem...

## The Solution
Since we assume there is some travel time between tasks, we can see this is a variation of the traveling salesman problem. Specifically, it is the multi traveling salesman problem. Or if we want to get very specific it is also called the task assignment problem. Fortunately, there is a lot of literature on this topic, unfortunately, most of it is not very accessible. A paper summarizing most key findings is here (Sorry for the paywall): <a href="https://www.sciencedirect.com/science/article/pii/S1574013721000095" target="_blank">A comprehensive survey on the Multiple Traveling Salesman Problem: Applications, approaches and taxonomy</a>.

{% include image.html text="MTSP Approaches" image="posts/task-assignment-problem/mts-taxonomy.jpg" %}

*To be continued...*
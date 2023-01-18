---
layout: post
title: 'Truss Solver'

code_url: 'https://github.com/EngSci-Tools/Truss-Solver'
code_url_text: '/truss-solver'  # Not required, defaults to the stuff after the last '/'
code_url_icon: 'github'  # Not required, defaults to 'github'

demo_url: 'http://truss.aidandevelops.com'
demo_url_text: 'Demo'  # Not required, defaults to 'Demo'
demo_url_icon: 'external-link'  # Not required, defaults to 'external-link'
---

{% include image.html image="projects/truss-solver/pratt_truss.png" text="Pratt Truss" %}

Trusses are a fundamental building block of stable structures, widely used in various engineering applications such as bridges, buildings, cranes, and even in biological structures like bones. They are known for their efficient use of materials and ability to distribute loads evenly, making them a popular choice for many types of construction projects.

Truss Solver is a web application built on VueJS framework that allows users to design and analyze truss bridges. By placing joints and members on a visually pleasing interface, users can easily create and manipulate their bridge designs. The application utilizes Pixi.js for rendering the bridge, which ensures that the visuals are smooth and responsive.

The core functionality of Truss Solver is its ability to compute the forces of tension and compression along the members of the truss bridge. By solving the matrix equation of statics, the application can accurately determine the internal forces acting on each member. This allows users to understand the structural behavior of their designs and make informed decisions about the best materials to use for each member.

{% include image.html image="projects/truss-solver/truss_calculations.png" text="Calculations" %}

In addition to its analytical capabilities, Truss Solver also provides users with suggestions for the best hollow structural sections to use for each member. This feature helps users to optimize their designs and ensure that they are using the most efficient materials possible. Users can also scroll down below the visual area to view the matrix equation used to determine the equations of statics.

{% include image.html image="projects/truss-solver/truss_member_analysis.png" text="Analysis" %}

A truss solver is an essential tool for engineers and students who want to design and analyze truss bridges. With its beautiful visuals, intuitive interface, and powerful analytical capabilities, Truss Solver makes the process of designing and analyzing truss bridges easy and accessible. Built on VueJS framework, it is also easy to use and understand for those wanting to replicate the design.
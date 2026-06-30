---
layout: post
title: "Week 15: Submission Blog Post"
author: "Team 04"
---

# Before We Start
This is our submission blog post for the IBM AI Racing League. 

But we have been blogging throughout the project's development. This post will summarise the previous posts, but for some more technical details see the other posts.

So <a href="https://ai-group-project-group-4.github.io/project-blog/">Click Here</a> to see all development posts.


(Or click the "Team 04 TORCS Racing Blog" title in the top left)

# Introduction and Context

First let us start with an introduction and some context around how we find ourselves in the IBM AI Racing League competition.

We are Team 04 from the University Of Sheffield

Our team consists of the following members:
<ul>
    <li>Jimi Wilson</li>
    <li>Kerem Nur</li>
    <li>Oliver Holbourns</li>
    <li>Rhys Womack</li>
    <li>Lewis Beamond</li>
    <li>Hannah Krebs Rocha</li>
</ul>

We are all studying the Computer Science (Artificial Intelligence) course.

As part of it we take part in the AI Group Project module which is done in collaboration with IBM.

We had multiple projects to choose from and ended up choosing the AI Racing League.

Throughout the module, we work with John McNamara of IBM as our client to provide an AI model which could achieve the fastest standing lap time around the TORCS Corkscrew track.

During the module, we were informed about the optional competition we could enter. From the announcement we knew we wanted to enter, and compete for the fastest possible lap time.

# Development Overview

## The Beginning (Weeks 1-2)
Our project kicked off with project allocation and our first facilitator and team meetings. We quickly set up our first client meeting with John McNamara to start building out our requirements document. Alongside this, we installed TORCS and the team completed multiple IBM SkillsBuild activities to familiarise ourselves with IBM Granite.

## Getting Stuck In (Weeks 3-6)

We hit an early roadblock when we realised the provided seven-year-old codebase relied on deprecated libraries and did not fully implement a Gymnasium Environment, which we required for our Stable-Baselines3 approach.
With the codebase being difficult to understand we turned to IBM Granite, which made the process a breeze, significantly cutting down the hours required to fully understand the system. From then on we rewrote the codebase with assistance of IBM Granite and moved on to setting up a baseline time.

Using IBM Granite we rapidly developed a PID Driver which achieved a baseline lap time of **2:14.67**.

Onwards from the PID Driver, we used behavior cloning to develop a PPO model which cut the lap time down to **1:41.66**.

Alongside our development, we documented our technical and non-technical requirements and risks and started to form our requirements document and risk register.

## Optimising (Weeks 7-8)

As we continued to train PPO models we hit a bottleneck.

PPO is a sample hungry algorithm, and training it was painfully slow. To fix this, we moved away from training and towards our infrastructure.

Whilst bouncing ideas off IBM Granite, we came to the consensus that we needed to try and run TORCS in parallel to significantly decrease PPO training time. However achieving this was no easy feat, TORCS was not designed with reinforcement learning in mind for a start and definitely not parallel instances.

So we had to isolate TORCS into Docker containers, which proved easier than expected.

But the biggest challenge was yet to come. Synchronising up to 64 different TORCS containers was a nightmare. A nightmare that even IBM Granite couldn't solve easily.

After hours of research and digging into the TORCS and SCR path documentation, we found the key details we needed to progress. With this, we implemented an orchestration script that managed the lifecycle of our Docker containers and altered the communication timeout on TORCS.

Now training with this new parallel environment, we broke our lap time again, achieving a 1:39.13 lap.

## Client Presentation (Weeks 9-10)

Moving on into weeks 9 and 10 we started to focus on preparing for our presentation for John McNamara.

Whilst in the process of making slides and practising our delivery we discovered a major configuration issue. During the move from individual TORCS instances to multiple, we completely forgot to copy over the IBM car config, which resulted in us training on the slower car instead of the IBM F1 car. Luckily we spotted this, and with a quick patch on the Docker Image we had the correct car loading and racing.

This small fix instantly dropped our lap time down by 7s to **1:32.30**.

Our presentation went well (barring the numerous technical issues) with both John and our facilitator praising it and giving us excellent feedback.

## Module Deadline (Weeks 11-12)

With the module deadline approaching fast, we moved away from model development and focused on our non-functional requirements, creating our team video, polishing our requirement document and risk assessment.

With the module ending, we took a period of time off to focus on our university exams.

## Final model (Weeks 13-14)

Now with the pressure and distractions of university out of the way for the next few weeks, we could focus on getting the best lap time submission to the IBM AI Racing League. Although a new distraction of the World Cup would arrive during this period.

Despite the football, we made significant progress during this period. We took our parallel environment back to the garage and transformed it into a custom framework called [`pytorcs`](https://github.com/Jimi-Wilson/pytorcs).

With the new IBM Bob being released, while using it in the development of `pytorcs` we could instantly see the gap between IBM Bob and IBM Granite. The quality of output significantly cut down on manual changes and re-prompting.

Now using `pytorcs` as our experimentation framework, we could iterate even faster than before with this new power we expanded to looking at different algorithms.

Soft Actor Critic (SAC) was the main one we experimented with and we got some significant progress.

Our first SAC model achieved a lap time of **1:26.12**. With this success we chose to fully focus on SAC and refined our techniques until we achieved our submission model.

After 27 million timesteps of training, we got our best model which had a standing lap time of **1:19.70**.

### 1:19.70 Lap Time

<div class="video-wrapper">

<iframe width="560" height="315" src="https://www.youtube.com/embed/TAAIgZqrP5Q?si=Gf9LnIM-BCQ2GppY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>


<style>
  .video-wrapper {
    width: 100%;
    max-width: 800px;
    margin-bottom: 2rem;
  }
  
  .video-wrapper iframe {
    width: 100%;
    height: auto;
    aspect-ratio: 16 / 9;
    border-radius: 8px;
  }
</style>


### Lap Time Progression

| Milestone | Time | % Decrease (Previous) | % Decrease (vs PID) |
|------------|-------|----------------------:|--------------------:|
| PID Rule-Based Driver | 2:14.67 | — | 0.0% |
| Initial PPO (Single Instance) | 1:41.66 | 24.5% | 24.5% |
| Docker Parallel PPO | 1:39.13 | 2.5% | 26.4% |
| F1 Car Configuration Fix | 1:32.30 | 6.9% | 31.5% |
| SAC Model 1 | 1:26.12 | 6.7% | 36.1% |
| **Final SAC Model** | **1:19.70** | **7.5%** | **40.8%** |


# IBM Granite and IBM Bob

Before we close out, we just want to give our thoughts on our experience with IBM Granite and IBM Bob.

Tools like IBM Granite are changing how software engineering is done, and we got to see that first-hand throughout this project.

IBM Granite was with us from the very start. It helped us untangle a seven-year-old codebase that would have taken days to understand on our own, and it stayed a constant collaborator as we built out our early models.

One of our biggest challenges was getting our Docker containers to synchronise properly, and even IBM Granite couldn't hand us an instant solution for that one. But working through it together, alongside our own research, we arrived at a solution.

Later in the project, when we built `pytorcs`, we got to try IBM Bob. The difference was noticeable straight away. What would have taken us a lot of back-and-forth with Granite often came out right the first time with Bob.

Having access to both tools throughout the project has been really enjoyable, allowing us to test different development styles.

# Closing Thoughts

We have thoroughly enjoyed working on this project from start to finish. It's been a brilliant opportunity to learn about reinforcement learning.

A huge thank you to IBM for the opportunity, and to John McNamara for being a supportive and engaged client.

Team 04
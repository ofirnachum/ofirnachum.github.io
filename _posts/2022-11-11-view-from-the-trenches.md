---
title: 'Paper Writing: A View from the Trenches'
date: 2022-11-10
permalink: /posts/view-from-the-trenches/
tags:
  - research
---

*You have a great research idea. You run some experiments and get promising results. You think, “Great! I’ll have a research paper in no time!” You run some more experiments, and results start to look a bit strange. You try to dig into the issue more, but end up with even more conflicting findings and new questions. A few weeks turns into a few months until eventually you realize the conference deadline is only two weeks away! What will you do? Was all of your effort a waste?*

The above is an exaggerated but common situation in research. No matter how well you plan your research direction and account for risks, you will sometimes inevitably find yourself a few weeks from a deadline with only partial answers to the research questions you originally started with. How can you take a collection of seemingly disconnected and sometimes conflicting results and turn them into a research paper? In this post, I’ll show how to do so with two examples -- two stories of paper writing direct from the trenches.


## Representation Matters: Offline Pretraining for Sequential Decision Making [[arxiv](https://arxiv.org/abs/2102.05815)]

The research for this paper started a lot like the example at the beginning of this post. We (my co-authors and I) were curious about using offline data for representation learning in a reinforcement learning context. We had initial promising results, but as we expanded the number of settings and methods, the picture became blurry. Sometimes one approach worked, and in other settings it didn’t. Various details seemed to matter a lot, and we had a hard time keeping track of all of them. We continued to run more experiments, but at some point the upcoming conference deadline was too close to ignore. We had to make a decision: Were we going to submit a paper? 

To help us make this decision, we performed an exercise which I like to do in confusing times like this. We made a list of research questions, some that our experiments had already answered and others that remained open. We tried to make the list as exhaustive and detailed as necessary – even if an answer only applied to a specific setting, it was an answer nevertheless. 

While our list contained many unanswered questions, as we reviewed it and looked for patterns and commonalities within the answered questions, we realized that some of our findings were interesting and, arguably, new to the literature. Some of our negative findings – methods which didn’t perform well despite our best efforts – were especially surprising and new. We also realized that a few of the remaining open questions could be answered if we introduced more focus into our experimental protocol. If we could do that, then there was probably a compelling story we could stitch together. 

And so that’s exactly what we did. We outlined a comprehensive but focused set of experiments to run – both to confirm existing findings as well as to answer remaining key questions. We analyzed the results and determined which were the most important to communicate. And finally, we wrote the paper.


## Near-Optimal Representation Learning for Hierarchical Reinforcement Learning [[arxiv](https://arxiv.org/abs/1810.01257)]

For this paper, the research question we wanted to solve was a natural next step after [our previous paper](https://arxiv.org/abs/1805.08296). In our previous paper, we had introduced a method that achieves impressive results but relies on a design choice (a hard-coded representation of goals) that we knew was not ideal and would not generalize to other settings. We hypothesized that if we could find a more general and automated way to make this design choice, we could get even better results. 

Initially, progress was good, and we found a particular approach that got promising results roughly matching our previous paper’s results. We believed that, with a bit more tinkering, we could get the improvements over our previous paper that we were looking for. Well, a bit more tinkering eventually led to a lot more tinkering, and after a significant amount of time, we were in a seemingly bleak situation. All we had was an algorithm that performed about as well as our previous paper, but with perhaps a more “elegant” approach to goal design. 

We knew this was a bad situation to be in. Papers that argue for an approach based on subjective measures (e.g., that the approach is more “elegant” or “principled”) are harder to defend compared to papers that solve a real and quantitatively measurable problem. 

We were saved by a key realization: Our intuition told us that our newly devised approach *should* be more general than the prior one, only that our current results didn’t show this. So we thought, what if we applied the prior approach to a setting where it would surely be unable to generalize? In our case, this was easy. Instead of evaluating on state-based environments, we evaluated on image-based environments. Immediately, we got what we were looking for. The prior approach failed miserably in image-based settings, while our new approach outshined all competitors.

And with that, we had a paper. All it took was evaluating our method the “right” way. From this experience, I learned that, as researchers, we have flexibility over the precise problem we choose to solve. It is important to choose the right metric to highlight our method’s benefits and to avoid unnecessarily constraining ourselves to the choices (metrics, datasets, environments) that previous papers used for their own approaches.


***

*Main Takeaways*

- *When faced with numerous seemingly disconnected results, try the following exercise: Make an exhaustive list of related research questions, as specific and detailed as necessary. Which of these questions have your experiments answered and which remain open? Are there common themes or patterns? Is there a new and interesting story you can stitch together from this list?*

- *Don’t overlook results or solutions that only hold in certain settings. Even if an answer only applies to a specific setting, it is an answer nevertheless.*

- *Avoid unnecessarily constraining yourself to the choices (metrics, datasets, environments) that previous papers used, as these are often (implicitly) biased to highlight the benefits of these previous approaches. Your method’s benefits may require a different evaluation.*

- *As a researcher, you have flexibility over the precise problem you choose to solve. The research question you started with doesn’t have to be the research question you end with.*

***

Thanks to Mengjiao Yang for reviewing an early draft of this post.

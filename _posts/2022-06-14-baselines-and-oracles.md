---
title: 'Baselines and Oracles'
date: 2022-06-14
permalink: /posts/baselines-and-oracles/
tags:
  - research
---

In the recent past, I was working on a research project focused on representation learning. I had achieved initial promising results and was in the midst of continuing to try to improve the representation learning objective, under the assumption that there were still benefits to be gained by learning a better representation. I made numerous attempts at changing various components of my algorithm, but over the course of two months ultimate performance wouldn’t budge. I then decided to try running a test: I would devise an “ideal” representation based on my own knowledge of the task and give this ideal representation directly to my model. Certainly, an ideal handcrafted representation should improve performance! Lo and behold, the performance with this oracle representation was no better than my initial promising results. It was now embarrassingly clear that I had already solved the “representation learning” aspect of my problem and whatever remained to solve was orthogonal to representation learning. Looking back, I wish I could have those two months back....

The above is an example of using an oracle as a tool for doing research. In addition and complementary to oracles, the use of baselines is also key for doing effective research. An **oracle** is a solution to a research question that violates some assumptions of the problem, or a solution that uses privileged knowledge or access to solve the problem. A **baseline** is a naive solution to the problem, a straightforward application of existing methods to solve the problem. Oracles provide a rough ceiling on the best performance one can realistically hope to achieve, while baselines show what performance is achievable using existing methods.

Implementing a few baselines and oracles is one of the first things I recommend doing when tackling a new problem. To implement baselines, you should look through the literature and try to understand how current approaches tackle your research problem or problems similar to it. It also helps to imagine yourself as a practitioner encountering this problem – i.e., someone who is detached from the desire for novelty or a publication and possesses a healthy amount of pragmatism. If you were a practitioner, what would be the first thing you would try? The simpler, the better!

Despite the fact that I use words like “naive” or “simple” to describe baselines, I don’t mean that in a negative way. In most cases (and certainly in my own experience), the eventual solution to your problem will be a modification or combination of these baselines. In some cases, one could even write a paper where the main contribution is one of the baselines, unmodified. Even if the baseline approach already exists in the literature, if no one has applied it to your chosen setting, you could argue that this still constitutes a novel solution (and I’ve certainly done so!). More often, baselines at the very least give you an indication of what types of approaches seem to work and which don’t, and this helps guide the next steps. In the case that none of the baselines make even partial progress, you might want to simplify your problem or experiment setting.

When implementing the baselines for your problem, you should also come up with a few oracles. When determining the oracles, try to break down what you believe are the key difficulties of your research problem, and then come up with solutions that violate problem assumptions in order to circumvent these difficulties. If your problem has strict sample-efficiency requirements, then a natural oracle is one which has access to infinite data. If your problem focuses on generalization to a test domain, then a natural oracle is one which can train on the test domain directly. If your problem centers around learning good representations, then a natural oracle is one which is given the ideal representation.

The benefit of baselines and oracles is through the insights they provide via their achieved performance. Ideally, there should be a gap in performance between the two classes of approaches; baselines provide a rough “floor” while oracles provide an approximate “ceiling”. One of the first checks you should do is to make sure this gap exists! If the baselines and oracles perform similarly, then there exist some key errors in your understanding of the problem. For example, if your problem focuses on sample-efficiency but your baselines perform poorly even with access to infinite data, then something is wrong. Either your problem is not primarily about sample-efficiency or your baselines are limited by other bottlenecks. 

This sort of debugging of your assumptions is critical not only at the beginning but also throughout a research project. In my example above regarding my representation learning project, using an oracle in the middle of a research project was key to showing that the project should advance from focusing on representation learning (which it had already solved) to identifying the next unknown bottleneck. In other instances, oracles helped uncover egregious algorithmic bugs in my code. 

Just like oracles are a useful debugging tool throughout a research project, baselines are also important to keep in mind when encountering issues mid-project. For example, let’s say you’re in the middle of a research project. You’ve already found an approach that gets good results but ends up overfitting massively. A common mistake junior researchers make is concluding that their approach has a fatal flaw and that they have to rebuild it from scratch to handle overfitting. Don’t fall into this trap, and instead think like a practitioner! What would a practitioner do? They would simply try common tools people already use to fix overfitting – weight regularization, early stopping, learning rate decay, etc. – and use whatever works best. 

I hope you will use the concepts of baselines and oracles to accelerate your own research. And if you’ve already been using these tools under different names, let me know! I’d be interested to hear of other instances where these techniques have been critical to doing impactful research.

***

*Main Takeaways*

- *When tackling a new problem, implement a variety of baseline methods to build an understanding of what works and what doesn’t. If nothing works, you may need to reframe your problem.*

- *When tackling a new problem, implement oracles to confirm or refute your understanding of the key challenges in your problem. If results are not what you expected, you need to either change your understanding of the problem or change the problem itself.*

- *Continue to use baselines and oracles throughout your research. When your progress stalls, cleverly designed oracles can help pinpoint the main bottlenecks. By the same token, simple baseline “patches” (think like a practitioner!) can unblock your path.*

***

Thanks to Ben Eysenbach for reviewing an early draft of this post.

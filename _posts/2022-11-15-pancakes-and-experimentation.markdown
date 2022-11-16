---
title: "Pancakes and experimentation: Learning by doing"
date: 2022-11-15
tags: ["experimentation", "culture", "learning"]
original:
  source_name: Vista DnA Blog
  source_url: https://vista.io/blog/pancakes-and-experimentation
header:
  overlay_image: assets/2022-03-09-diagram.jpeg
  overlay_filter: 0.8
  teaser: assets/2022-03-09-diagram.jpeg
excerpt: 'We are [building a culture of experimentation]({{site.baseurl}}{% post_url 2021-12-21-building-a-culture-of-experimentation %}) at Vista. We are taking a [scalable, decentralized approach]({{site.baseurl}}{% post_url 2022-03-09-organising-for-scaled-experimentation %}),  requiring people and teams across the organization to learn new skills and adopt new methods. In this post, Ellen and Lukas will share some of their perspectives and experiences on this journey.'
---

*Ellen Greer is the Product Manager for Vista’s Search features. Lukas Vermeer is Vista’s Director of Experimentation.*

**Ellen**

Not so long ago, I was a product manager who knew experimentation was critical but had never actually done it. I had attempted a few A/B tests here and there on various products and eCommerce UIs but was stymied every time. Some of the hurdles were pollution in our variation and control cohorts, brittleness in homegrown testing tools, and the culture of scrambling to ship as much as possible ASAP.

After a few rounds of frustrating attempts, I have to admit I kind of gave up. I did a few qualitative user interviews to validate my team’s work, but mostly we just shipped blindly and hoped for—assumed—the best.

Then I read The Lean Startup by Eric Ries right around the time I was moving to a fresh new product area. I had new engineering, design, and analytics partners swarming on our primary product: Site Search. I also had the pleasure of meeting Lukas, who had recently joined Vista to lead our Experimentation efforts. To fall into step with a visionary like Lukas on the march toward a true culture of constant, customer-centric innovation was energizing, to say the least. With his encouragement (and his team’s expertise and resources), I was able to persuade my partners that this was the time to start trying.

Even if our first A/B test was going to be a huge time sink with doubtful ROI, I passionately felt we needed to start building that muscle.

**Lukas**

Experimentation involves a great deal of learning by doing. Building muscle is a necessary step in the journey. Part of the role of the Experimentation Hub is to encourage teams to simply start to test, to hold their hand the first few attempts, and to provide critical but constructive feedback that helps teams improve their approach over time.

I have noticed some teams get stuck trying to create the “perfect” first experiment. I think this behavior is counterproductive. We don’t know what we don’t know and won’t know unless we try.

**Ellen**

It’s like making a pancake! The first one is always a trash pancake. The skillet is just heating up; maybe there are more lumps to whisk through in your batter, the fat in the pan isn’t sizzling quite as much as it should, and your timing isn’t perfect because you’re impatient to start cooking breakfast. For all those reasons, the first pancake often turns out ugly, imperfectly cooked, or borderline inedible. But you have to make one trash pancake for pancakes number two through n to be possible, or even to be good.

**Lukas**

The first pancake is a great analogy! Of course, reading a few different recipes is a good idea to get a sense of the different options before you start baking. And, of course, carefully reading those recipes is a good idea to ensure you don’t miss any important ingredients. But it is equally important to accept that one simply cannot read all the recipes. At some point, we will just need to pick a promising recipe and start baking.

There are many different ways to set up an experiment. And there is a lot to learn about each method. It is easy to get lost in the details of one method; or, conversely, to miss the forest for the trees when considering different experiment design options. We need to help teams avoid analysis paralysis and accept that learning by doing requires doing things imperfectly without completely understanding.

Once we have decided on an approach, proper preparation is key when it comes to baking pancakes and running experiments alike. We need to ensure that the pan is nice and hot and the batter is nice and smooth. But again, we should not dally too long. Beating the batter to death (i.e., too long) will ironically make the result worse—it’s something to do with the gluten, I think.

A good experiment requires choosing the right metrics, running a power analysis, and QA’ing the implementation. But as with “reading all the recipes” above, we should be careful not to spend too much time on these things, lest it delay the actual execution of the experiment and slow our rate of learning about experimentation. We build muscle by doing reps, not by reading recipes.

Agonizing over the perfection of the first pancake would be counterproductive. No amount of poring over recipes or beating batter will help us avoid the simple truth of First Pancake: it is always trash.

**Ellen**

That was the theory behind our first A/B test on the Search product. The first A/B test we attempted for a new feature never even got off the ground. We ended up having to look at the performance of a personalized search result experience for returning customers “pre/post” due to technical limitations—we basically didn’t have the correct skillet. The good news is that the post-launch performance seemed incrementally positive, but in reality, that wasn’t a true scientific conclusion. We couldn’t verify if the new feature we’d created was better than the alternative, its absence. We were once again shipping blind. To me, this level of confidence that we were genuinely serving our users wasn’t good enough.

The next attempt was incredibly laborious but also had much higher stakes. My Search Product Team and I had joined up with Victoria Hancock’s Machine Learning Team in our DnA organization to bring the power of ML to radically improve the comprehensiveness of Search. This was a high-profile internal partnership with an ambitious green-field goal. This time around, my team lead, Hannah Clark, and I began strategizing with our partners about the A/B test from day one of solution design and development architecture. With the A/B test in mind, we ensured that everything was built to make experimentation possible. We leveraged help from the Experimentation Hub to get our experiment set up right, and we QA’ed relentlessly.

There were a few bumps along the way: ugly documentation, imperfect naming conventions, and so forth. But finally, we launched the first A/B test of the MVP new infrastructure for Search comprehensiveness!

**Lukas**

First, pancake perfection is not just impossible; it is also totally unnecessary in the grander scheme of things. There are more pancakes in the batch, and what matters is the end result: the full stack.

Experiments often do not stand in isolation; they are part of a longer series of experiments that will help us learn. Experiments actually help us learn on two levels: by doing experiments, we can learn about our customers, and we can learn how to experiment better.

On the first level, experimentation is like baking pancakes because only by running experiments will we learn what questions we should be asking in the first place and what kinds of answers to look for and expect. Every experiment informs the next. We use the things we have learned along the way to form better hypotheses and to predict and measure impact more precisely.

On the second level, experimentation is also like baking pancakes because only through practical experience, making mistakes, and getting feedback can we learn how to experiment better. With practice, we will get better at experimentation over time. There is no shortcut from novice to expert experimenter that does not involve running lots and lots of experiments.

You might look at other people and companies and realize that some of them are really, really good at baking pancakes (or running experiments). You might think that if we were to use their special recipe, we would also be really, really good instantly.

The problem with that idea is that this just does not work; it is often counterproductive. People who are really good at something don’t typically use the easiest or simplest approach to do that thing. Trying to copy experts is not a great strategy if you want to learn a new skill.

The first pancake cannot be avoided.

**Ellen**

It was agony to wait for the full runtime of the test to peek at the results. In the meantime, my analytics partner Ray Echevarria and I brainstormed about a “pre-mortem” plan for how we would interpret and act based on each possible outcome of the experiment. Our results would directly affect the viability of the next A/B test to evaluate the performance of the MVP Machine Learning model, so we needed to iron out and communicate the game plan proactively to all involved.

I am delighted to say that this A/B test was a resounding success! We got accurate, scientifically-gathered, high-confidence data from Vista customers that the new level of comprehensiveness we offered them in Site Search was indeed a much better experience for them. We could show our partners and stakeholders that all the time and effort had been well worth it. We were validated as having been on the right track. We were able to project the future value of the subsequent phases of this radical project and thus stay focused—and resourced—on this goal. I will write to you a few months later when the solution is done, and we’re basically in the global rollout phase of the project. We’re looking at helping potentially tens of millions of customers per year to have a better search experience on the VistaPrint site.

If it hadn’t been for that first trash pancake, the second one wouldn’t have been so good.

**Lukas**

Trash does not have to go to waste. Even though we say the first pancake is always trash, we don’t usually actually throw it in the trash bin. More often, the cook will secretly eat it in the kitchen while working on the rest of the batch. The first pancake isn’t a waste; it is a learning opportunity that feeds the next steps.

Inevitably we will look back at our first attempts and feel pangs of regret and embarrassment—I know I do. These feelings do not mean those first experiments were failures; they were the very things that helped us learn.

It is also important to appreciate that this does not mean we should not do our best. It is important to try hard to succeed in every experiment we do. If we don’t try, we will not learn. But it is equally important to accept that in order to learn, we have to improve, and improvement implies that, at first, we are not as great as we will be.

The first time Ellen mentioned this idea of “first pancake” to me, it immediately struck me as a great way to explain the concept of “experimenting to learn how to experiment”. Building a culture of experimentation requires building a collection of shared norms and ideas about experimentation. I realized that this idea might become one of those shared ideas.

Sharing stories is integral to any culture, and experimentation cultures are no different. Often, these stories will emerge and grow organically, but perhaps they can also be crafted and boosted to speed up the emergence of the culture we would like to see.

For Vista, the ‘First Pancake’ was the first of our experimentation stories, and I hope there will be many more.

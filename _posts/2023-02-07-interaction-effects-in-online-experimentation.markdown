---
title: "Interaction effects in online experimentation"
date: 2023-02-27
tags: ["experimentation", "interaction effects"]
original:
  source_name: Vista DnA Blog
  source_url: https://vista.io/blog/interaction-effects-in-online-experimentation
header:
  overlay_image: assets/2023-02-27-interaction-effects-in-online-experimentation-header.webp
  overlay_filter: 0.8
  teaser: assets/2023-02-27-interaction-effects-in-online-experimentation-header.webp
excerpt: 'Experiments allow us to test how changes to our products affect the behavior of our users. We make many such changes in many experiments running at the same time. As we scale up our experimentation volume at Vista, there will be an increased risk of interactions between experiments occurring.'
---

We say an interaction has occurred when the effects of two—or more—experiments on a metric combined is different from a linear combination of each of those experiments in isolation. For example, two individual changes help customers find what they need more easily, while the two combined have the opposite effect.

In some cases, this interaction might result from a functional conflict between two changes; they are functionally incompatible, causing a difference in effect. In other cases, the changes might be functionally compatible but still interact to change our measurement or user behavior more subtly.

Experience from other organizations suggests that these kinds of interactions tend to be rare in practice. However, since the consequences for the user experience and our learning can be dire, we should still consider their possibility and ensure we take precautions to avoid or detect them.

In this first post in this series, we will define two kinds of interaction effects and their potential consequences. The next post will discuss possible strategies for avoiding interactions and share some of our tools and processes. In the third and last post in the series, we will discuss how we can detect interactions and share code and tools we have built at Vista to address this issue.

# Traffic Interactions

Interactions between two overlapping experiments can be of one of two kinds: traffic or metric interactions. Traffic interactions occur when one experiment treatment causes a different mix of traffic to flow to another experiment. From a statical point of view, these are not interactions but rather a form of sampling bias.

For example, when variation B of experiment one changes the destination of a link on the homepage (page 1) from one product page (page 2) to another (page 3), and the second experiment makes changes on one of those product pages (page 3). In that case, the first experiment will cause less traffic to flow from page 1 into the second experiment. Traffic from page 1 will be underrepresented in the results of the second experiment relative to traffic from other sources. In this case, traffic from page 4 is overrepresented.

![A diagram showing traffic flows between two experiments on four pages.]({{site.baseurl}}{% link assets/2023-02-27-interaction-effects-in-online-experimentation-0.svg %})

Traffic interactions are rarely a problem for users, and traffic interactions are also not necessarily a problem for decision-making. The traffic in experiment two in the example above can still be equally split, and the metrics can still be tracked. There is, however, a risk of bias in the results since the traffic diverted by experiment one might be different from the remaining traffic in some meaningful way.

# Metric Interactions

The second kind of interaction is metric interactions. These occur when the impact on a given metric for a combination of two experiments differs from what we see in either experiment in isolation. Different metrics for any two experiments might have differences in interaction effects.

For example, when experiment one shows an uplift of 5% on conversion and experiment two shows an uplift of 10% on conversion, we would expect the combination of these two to show an uplift of approximately (1,1*1,05)-1 = 15,5%. If instead, we see a drop of 50% for the audience which is exposed to both tests, then we would call that a—in this case— negative interaction. At the same time, for the same experiments, we might not see any such interaction effect on CTR or other metrics.

|                           | Users in A of Experiment 1 | Users in B of Experiment 1 |
|---------------------------|----------------------------|----------------------------|
|Users in A of Experiment 2 | Control                    | +5%                        |
|Users in B of Experiment 2 | +10%                       |-50%                        |

Similar to traffic interactions, metric interactions are not necessarily a problem depending on the nature and severity of the interaction.

# Working Example

The following example of two functionally incompatible experiments would result in an interaction effect. This example is deliberately contrived to simplify the explanation and exaggerate the impact. In practice, functionally incompatible changes such as these will likely be caught during development and Q&A; thus, the interaction would never occur.

Imagine two independent teams have noticed in user research and web analytics tracking that our customers are not signing up for our mailing list. Both teams have identified a lack of contrast in the UI as a potential reason for this observation.

![Business as Usual – The Control Condition for Both Experiments]({{site.baseurl}}{% link assets/2023-02-27-interaction-effects-in-online-experimentation-1.webp %})
 
Both teams hypothesize that signups will increase if we increase the contrast on the “Submit” button. Each group decides to test this hypothesis with a different implementation.
The first team decides to increase contrast by changing the font color to a bright color. The group decided pink would be a good choice.

![The Variation of the First Experiment]({{site.baseurl}}{% link assets/2023-02-27-interaction-effects-in-online-experimentation-1.webp %})
 
The second team decides to increase contrast by changing the background color to a bright color. This group also decided pink would be a good choice.

![The Variation of the Second Experiment]({{site.baseurl}}{% link assets/2023-02-27-interaction-effects-in-online-experimentation-1.webp %})

Both teams decide to test their ideas with an experiment simultaneously. As a result, some visitors to our website will be part of both experiments. Some of those users will simultaneously be exposed to both changes. The resulting experience is obviously not ideal.

![The Variations of Both Experiments Combined]({{site.baseurl}}{% link assets/2023-02-27-interaction-effects-in-online-experimentation-1.webp %})
 
When both changes are combined, contrast drops to zero, and signups decrease dramatically. These experiments are functionally conflicting and, as a result, statistically interacting.

# Consequences of Functional Conflicts

Now that we know what experiment interactions are, we can consider what could be the potential consequences of an interaction. Considering consequences will help us better assess the risks and decide when to avoid possible interactions.

But before we dive into the potential consequences of interactions, we should highlight something which is not a consequence but rather a cause for interactions: functional conflicts.

In our working example above, some visitors to our website were not signing up for our mailing lists because the combined changes were causing the “Submit” button to be unreadable. It is essential to realize that this functional conflict would also exist if the changes were made without any experiments—in fact: four times more users would be affected that way.

We want to avoid experiment interactions partially because of the consequences for measurement and decision-making. But perhaps more importantly, we want to avoid them because they suggest some functional conflict has resulted in a degraded customer experience. From a user experience perspective, it is not the interactions we want to avoid but primarily their cause.

Therefore, any potential solution that addresses experiment interactions should also address functional conflicts. One of the reasons to want to test every change and run experiments in an overlapping fashion is that it is a powerful method to detect interactions. Experimentation does not cause the problem of functional conflicts but rather can help us avoid them or at least identify and solve them when they occur.

# Consequences of Experiment Interactions

Functional conflicts aside, interactions between two experiments can have one of two related detrimental effects: biased measurements and wrong decisions. In product development, we—usually—care much more about inference and decision errors than we care about bias, although one can lead to the other.

## Interactions Can Introduce Bias in the Measurement

Because interactions can affect the estimated effects of both experiments, they might cause us to overestimate or underestimate these effects. We might think an experiment resulted in a -45% drop, when in fact, it had a +10% lift which is biased downwards by an interaction effect with another experiment.

In the example above, users exposed to both treatments would not sign up for our mailing lists. From the perspective of one experiment, half of the users in the treatment would seem to be negatively affected by the change. Since the impact estimate is based on the average treatment effect, this average would be biased downwards as a result.

| Bias Example 1                                   | Effect |
|--------------------------------------------------|--------|
| A of Experiment 2 (50% of users in experiment 1) | +10%   |
| B of Experiment 2 (50% of users in experiment 1) | -100%  |
| Total for Users in Experiment 1                  | -45%   |

As you can see, the total effect for users in experiment one does not reflect the true +10% but is “dragged down” by the severe interaction effect of 100%. As a result, the measured overall effect is biased downwards to 45%. In this instance, the bias would—if not detected—likely also lead to decision errors which we will discuss later separately.

Bias is not always bad. The above example is rather dramatic, but more subtle effects and biases are also possible. If two experiments reinforce each other, we might see a bias that is not counter to the main effects but improves it.

| Bias Example 2 | Effect |
|----------------|--------|
| A of Experiment 2 (50% of users in experiment 1) | +10% |
| B of Experiment 2 (50% of users in experiment 1) | +20% —B doubles the effect of experiment 1! |
| Total for Users in Experiment 1 | +15% |

The bias is less pronounced in this second example, and the measured overall effect is still biased but less so. The bias is also in the “right” direction. In this instance, the bias could be considered a good thing—certainly from the user’s point of view—and would, if not detected, likely lead to fewer decision errors because the bias also increases statistical power.

If an interaction is detected, we can mitigate this bias by ensuring that it is considered when estimating the true effects of the experiments involved. We could do this by only considering users in A of experiment 2 in our effect size estimates, but this would halve our sample size and thus result in less statistical power and more uncertainty about the estimate. A better approach would be to use a regression analysis that includes an interaction term. We will discuss this approach in this series’s third and last posts.

## Interactions Can Cause Inference and Decision Errors

As the examples of bias above show, severe interaction effects might cause us to conclude that the effect of one experiment is negative when in fact, it would be positive were it not for a drastically negative interaction effect. These sorts of directional errors would, if they remain undetected, not only cause us to overestimate or underestimate the size of the effect but also cause us to make wrong inferences—e.g., we conclude the treatment is bad when it is good and wrong decisions—e.g., we stop the test when we should have rolled it out).

These types of errors are much worse from a product development and user point of view. Luckily, they are rarer and easier to detect because much more drastic interaction effects are required for such a decision reversal.

As was the case with bias, when interactions are detected, we can take them into account and ensure we still make the right decision. In some cases, detection might even lead to new ideas and opportunities to explore.

## Interactions Can Be a Good Thing—if detected

As the examples above illustrate, both bias and decision errors can be avoided if experiment interactions are detected. In addition to mitigating most of the negative consequences of interaction effects on decision-making, detection can have additional advantages over avoidance.

If two experiments lead to a very negative interaction effect, that suggests there might be some underlying functional conflict that we were not previously aware of. If two experiments lead to a positive interaction effect, that suggests there are synergies between treatments. In both cases, these observations can lead to new insights and hypotheses to explore.

By detecting interactions, we can learn things that we could not have understood without observational evidence of the interaction. Interactions are thus not necessarily something that should be avoided at all costs. Quite the contrary: interaction effects can give us additional serendipitous insights with little extra effort and investment.

# Avoiding and Detecting Interaction Effects

In this post, we have tried to clarify what interaction effects are and what their consequences could be if they remain undetected. In the next post in this series, we will discuss potential strategies for avoiding interactions and share some of the tools and processes we use at Vista.

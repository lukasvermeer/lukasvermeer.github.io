---
title: "Avoiding Interaction Effects in Online Experimentation"
date: 2023-04-04
tags: ["experimentation", "interaction effects"]
original:
  source_name: Vista DnA Blog
  source_url: https://vista.io/blog/avoiding-interaction-effects-in-online-experimentation
header:
  overlay_image: assets/2023-04-04-avoiding-interaction-effects-in-online-experimentation-header.webp
  overlay_filter: 0.8
  teaser: assets/2023-04-04-avoiding-interaction-effects-in-online-experimentation-header.webp
excerpt: 'In the previous post in this series, we defined interaction effects and discussed the potential consequences if they remain undetected. In this post, we will discuss several approaches to avoiding interaction effects and share some tools and processes we use to enable conflict avoidance.'
---

Some may think the ideal solution is never running multiple experiments simultaneously to avoid all possible interactions. However, this is not always feasible and could be prohibitively costly. Moreover, as explained in the previous post, there are occasionally unexpected benefits to detecting interaction effects, meaning avoiding them altogether may not even be desirable.

# Strategies to Avoid Interaction Effects

First, we will discuss an exhaustive list of strategies for avoiding interaction effects. As far as we know, there are no other options besides the strategies outlined below (and potentially hybrids between them).

We hope this will clarify that wholesale avoidance strategies are likely unrealistic or extremely costly. Instead, we recommend a hybrid strategy in which we selectively apply these techniques only to experiments in which functional conflicts are expected. In the second half of this post, we will explain the tactics we use to identify such potential conflicts.

## The Null Strategy: Not Running an Experiment at All

Although we would never recommend this strategy in good conscience, it is essential to acknowledge that it exists for teams with the proper resources. If experimentation, interaction detection, or the avoidance process introduce excessive friction and costs, teams may do away with experimentation altogether.

Obviously, this approach has several major downsides. Most importantly, it fails to avoid functional conflicts for end users since those exist separately from the experiment, as explained in the previous post. If both teams in that example were to roll out their color changes without an experiment, the button would have remained far too pink for end users to read easily.

**When We Recommend This Approach:** Never.

## The Sequential Strategy: Running One Experiment at a Time

One of the simplest approaches to avoiding functional conflicts and experiment interactions is simply running experiments individually and sequentially. This requires teams to agree on an ordering, usually based on the experiments’ relative priority and expected value. No technical or procedural changes are required; one team simply waits to begin their experiment until the other is done.

The main difficulty in applying this approach is not technical but organizational. It requires agreement and cohesion between teams about priorities that extend beyond the objectives of a single team. The main downside of this approach is that it slows down momentum and progress for some experiments and teams. If applied very broadly, this approach might even lead to a domino effect where several teams are all waiting for a single experiment to finish.

However, there are also cases where this approach has one additional advantage: when learnings from one experiment can be used to inform another—potentially conflicting—experiment. In that case, waiting might delay the execution of one experiment, but at the same time, it can increase that experiment’s quality.

**When We Recommend This Approach:** When teams can fully agree on the need for conflict avoidance and optimal sequencing.

## The Isolation Strategy: Running Experiments in Separated Lanes

This approach involves setting up isolated groups of visitors (in so-called “lanes”) so that each experiment can run on an independent group of visitors without worrying about functional conflicts or interaction effects caused by overlapping with experiments in other lanes. This requires some effort to implement since an additional split must be set up.

The appeal of this approach is mostly that it does not require coordination and agreement on priorities between teams. Instead, you stick to your lane, and they stick to theirs; each team can do whatever they want within those lanes. Apart from that, this approach is inferior to the sequential approach above in many ways, as explained [here in detail by Georgi Georgiev](https://blog.analytics-toolkit.com/2017/running-multiple-concurrent-ab-tests/).

The main downside is that this method reduces the sample size for experiments, as they will each be limited to a single lane. As a result, this can slow down all experiments involved. The total throughput time will be similar to that of the sequential approach above, although the sequential approach has the advantage that some experiments will finish sooner.

It is worth noting that this approach solves both functional conflicts and interaction effects, but only while the experiments run inside their lanes. If both teams decide their experiments are successful and wish to roll out their changes to all users, functional conflicts could still occur. Worse still, because these changes were never tested together, there is no way to check for interaction effects that might indicate whether there are functional conflicts.

**When We Recommend This Approach:** When teams cannot agree on optimal sequencing, and it is unlikely that experiments from different lanes will eventually be rolled out to all users.

## The Combined Strategy: Combining Treatments Into a Single Experiment

Rather than isolating experiments in separate lanes, we could also isolate changes in separate variations. Instead of setting up two experiments (control vs. treatment_1 and control vs. treatment_2), we could set up one A/B/C experiment (control vs. treatment_1 vs. treatment_2 and optionally treatment_3, which combines elements from treatment_1 and treatment_2).

One constraint of this approach is that it only works if the experiments involved have similar audiences. In practice, this is often the case for experiments at risk of interactions, considering that if they do not share a significant amount of traffic, they will unlikely interact in the first place.

As with the isolated lanes approach, this method reduces the sample size available for each variation. However, because the control is shared, this effect is less pronounced. In total throughput time, this approach is more efficient than sequential and isolated lanes approaches.

Although it does require tight coordination between teams to carry out effectively, the combined strategy is usually fairly straightforward to implement. In addition, functional interactions are made impossible when a variation is rolled out to production because no variations have both changes enabled at once (unless treatment_3 is included).

**When We Recommend This Approach:** When teams cannot agree on optimal sequencing but can agree to coordinate their experiments with a large overlap in traffic.

## The Detection Strategy: Not Avoiding Interactions and Choosing Detection Instead

While detection is technically not a strategy for avoiding interactions, it is definitely something to always keep in mind when discussing how to proceed. As explained in the previous post in this series, many consequences of interactions can be mitigated or even prevented, assuming they are detected in time.

Even if we suspect two experiments might interact in some way (but not functionally conflict), running overlapping experiments while closely monitoring for interactions may still be the optimal strategy. When considering this option, it’s crucial to keep the user experience at the forefront. We should always strive to avoid functional conflicts and degraded user experiences.

**When We Recommend This Approach:** When the risk of functional conflicts is low, and we can detect and mitigate interactions quickly.

# Our Suggested Strategy: Avoid Some, Detect Others

When thinking about the potential consequences of interaction effects, the available strategies, and how those aspects should inform our decisions and actions, it can be helpful to start by considering the functional conflicts separately.

Because functional conflicts lead to degraded customer experiences, we should aim to avoid them as much as possible. This is not because we want to avoid interaction effects but because we want to ensure our customers continue to enjoy excellent experiences.

Because interaction effects can lead to biases and inference errors, we must strive to detect severe interaction effects as soon as they occur. We can correct the resulting biases and decisions as long as they are caught early on. This means that avoidance is ultimately less important, and perhaps not worth the cost incurred by the avoidance strategies discussed above.

Thus, at a high level, our recommended strategy is to:

1. Avoid potential functional conflicts.
2. Detect interaction effects.

Put differently, we do not believe that the optimal strategy involves avoiding all possible interactions at any cost. To decide whether a potential interaction should be avoided, we must consider the risks and consequences of an interaction and then weigh those against the potential costs of avoidance. In many cases, this trade-off will need to be discussed with other teams before action can be taken.

# Strategies to Identify Potential Functional Conflicts

To avoid potential functional conflict, we will need to identify which experiments will potentially interact before both experiments go live. There are many ways in which potential interactions can be discovered, all of which rely on some form of information exchange between the various experiment owners.

While writing this post, we asked experimenters for examples of interactions they’ve encountered and how they were discovered. In some cases, semi-random encounters and information sharing resulted in someone outside the team realizing there was a potential interaction. Happy coincidences such as these are one possible way of uncovering potential interactions—simply keep your eyes and ears open, and pay attention to what experiments other teams are running. This also gives one the added advantage of being able to learn from their approach and results.

However, we cannot rely on such serendipity as a general strategy. Instead, we need strategies for more structured ways to discover potential interactions. We use several active strategies at Vista and a significant passive strategy: relying on other people.

## Using EXPO Search to Find Relevant Experiments

At Vista, we use a special Jira board we call “EXPO” to keep track of all our experiments. These EXPO tickets have several fields that can be used to search for experiments that might potentially interact using the Jira search feature. For example, the search in the screenshot below shows all of our EXPO tickets currently in “Design & Development” phase, which will affect the “Category Page” site section.

![A screenshot of a Jira issues search results page]({{site.baseurl}}{% link assets/2023-04-04-avoiding-interaction-effects-in-online-experimentation-1.webp %})

As seen in this example, other fields, such as the “Affected Website Locale,” can also be used.

![A screenshot of a Jira issues search results page]({{site.baseurl}}{% link assets/2023-04-04-avoiding-interaction-effects-in-online-experimentation-2.webp %})

If one of our teams is concerned that their experiment might interact with others, they can use these fields to find potential experiments to review. Afterward, they will need to review the details of each potential conflict to understand whether there is indeed a risk and then decide whether that risk is great enough to consider any of the interaction avoidance strategies outlined above.

## Using Slack Notifications to Set Alerts for Specific Fields

We use Slack for most of our company communications, and Jira allows us to set up notifications for any changes to a selection of experiments to be sent to specific channels in Slack.

When teams regularly run experiments on the same site sections or locales, they can set up automated Slack notifications for potentially interacting experiments on those specific site sections or locales. This will ensure that they are notified of new potential interactions immediately rather than having to periodically review the EXPO search results manually, as explained above.

The same approach can keep stakeholders in other parts of the organization informed by setting up dedicated channels for specific initiatives. By assigning EXPO tickets channel-specific tags, relevant updates will be automatically pushed to the right people.

## Helping Other People Avoid Conflicts

All of the strategies above rely on the relevant EXPO ticket fields being filled out precisely and accurately. This includes fields like “Affected Site Section” and “Affected Website Locale” as well as the inclusion of screenshots and detailed descriptions so that anyone reviewing the ticket can clearly understand what the experiment will do. To effectively work for teams, these strategies rely on people correctly filling out these fields.

However, teams should not be the only ones looking for potential conflicts with their experiments! If one team’s experiment is likely to conflict with some other experiment, then the reverse is also true: that experiment is likely to conflict with theirs. The owner of that other experiment is probably searching for potential conflicts, too, and teams can thus assist one another by filling out their EXPO tickets in detail.

Clearly, documenting experiments is probably one of the most effective methods for the early identification of potential conflicts. By ensuring that all experiments are clearly documented, teams can help each other find and identify potential conflicts before they become more significant issues. Once identified, those other teams can reach out to discuss the resulting risk. The better teams document their experiments, the more likely someone else can help them in this way. This dynamic means that teams will be incentivized to complete the proper documentation.

# Avoid Some, Detect Others

When a potential functional conflict is identified, the experiments involved might be owned by different teams within the organization. Thus, there may be conflicting priorities between the two or more teams when deciding whether or not to employ one of the avoidance strategies. If so, which one: sequential, isolation, or combined?

If the relevant teams cannot agree that there is a potential conflict to be avoided or which avoidance strategy to use, detection remains a valid option. In the upcoming third and final post in the series, we will discuss how we can detect interactions and share code and tools we have built at Vista to address this issue.

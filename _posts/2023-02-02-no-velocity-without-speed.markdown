---
title: "No velocity without speed"
date: 2023-02-02
tags: ["Experimentation", "Velocity", "Agile", "Scrum"]
header:
  image: assets/2023-01-11-velocity-gtgt-speed.webp
  overlay_image: assets/2023-01-11-velocity-gtgt-speed.webp
  overlay_filter: 0.6
  show_overlay_excerpt: false
  teaser: assets/2023-01-11-velocity-gtgt-speed.webp
---

[Speed is not velocity]( {{site.baseurl}}{% post_url 2023-01-11-velocity-gtgt-speed %} ), but this does not mean that speed is not important. In fact, speed is a prerequisite for velocity: without speed, there can be no velocity. We cannot be moving in the right direction if we are standing still.

This might seem too obvious to even mention. Clearly we need to release features (e.g. speed) in order for those features to add value (e.g. velocity). But the connection between speed and velocity is more complicated than it might at first seem. Mantras such as "fail fast" and "rapid iteration" hint at a deeper relationship which I will try to make explicit here.

Every time we release a feature through an experiment, we get feedback from our customers about that feature. This feedback allows us to measure whether this feature will help our velocity and in turn decide  whether to ship this particular release.

The same feedback also allows us to learn and improve future features we develop. Every time we release a feature through an experiment, we might learn something which will improve our chances of developing features that our users will use and love.

If we release more features per sprint, we will not just have more opportunities to ship; we will also have more opportunities to gather feedback and learn. It is this second order learning effect that "fail fast" and "rapid iteration" are referring to. Increasing speed of execution will—through reliable feedback—improve our aim, which will in turn increase our future velocity.

![A causal graph of speed->learning->velocity; speed->velocity.]({{site.baseurl}}{% link assets/2023-02-02-no-velocity-without-speed.webp %})

<!---
DiagrammeR::grViz("
digraph {
  graph [ranksep = 0.5]
  node [shape = plaintext]
    A [label = 'Learning']
    Y [label = 'Velocity']
    C [label = 'Speed']
  edge []
    A->Y
    C->A
    C->Y
  { rank = same; C; Y }
}
")
-->

This second order learning has a compounding effect: any individual release might result in insights that will influence all other releases that will come after it. If we want to optimise  for the long-term, then we should be willing to take (a little or a lot) more risk with each individual feature release—for example by building an MVP rather than a full-fledged product—if we believe it will increases our rate of learning.

Speed is not velocity, but speed is still critically important for velocity. The key phrase missing from both "failing fast" and "rapid iteration" is "… so that we can learn faster".

We want to be running with our eyes wide open.

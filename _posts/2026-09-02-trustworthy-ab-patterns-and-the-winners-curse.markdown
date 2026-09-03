---
title: 'Trustworthy A/B Patterns and the Winner''s Curse: Lessons from Eight Large-Scale
  Replications'
date: 2026-09-02
tag:
- Paper
categories:
- Paper
author: Lukas Vermeer
link: https://dl.acm.org/doi/abs/10.1145/3770855.3818498
---

**Abstract:**
Claims of large lifts in A/B tests are widespread, yet many are only supported by small online experiments that are likely underpowered. Trustworthy A/B Patterns is a community replication effort to evaluate selected patterns at high statistical power. We report on eight A/B tests across four patterns (rounded buttons, page performance, coupon-code field, and sticky call-to-action), with a median of 2.4M users per experiment and 80% power at our pre-selected minimum detectable effects (MDEs) of 0.3% to 2.2%. We find that: (1) even at this scale, we did not have enough power for key business metrics, such as revenue per user and purchase conversion rate, within practical time horizons, and had to resort to surrogate metrics, such as click-through rate, add-to-cart rate, and capped add-to-carts (count); (2) previously reported effects for these patterns are highly exaggerated: across all eight replications, estimated effects were substantially smaller than previously claimed; only two showed statistically significant effects in the expected direction at α=0.05, and one was statistically significant in the opposite direction. While it is possible that some patterns have larger effects in certain conditions, we believe it is more likely that many of the prior estimates came from underpowered experiments (power below 50%), which exaggerate treatment effects. We conclude with lessons from running the community project for over one and a half years.

Published at [KDD 2026](https://doi.org/10.1145/3770855) (32nd ACM SIGKDD Conference on Knowledge Discovery and Data Mining), Proceedings V.2, pp. 7533–7544. Co-authored with Ron Kohavi, Jakub Linowski, Andrey Andreev, Majed Dodin, and Joachim Furuseth.

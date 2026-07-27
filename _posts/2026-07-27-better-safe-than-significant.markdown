---
title: 'Better safe than significant'
date: 2026-07-27
tags:
- Experimentation
- Statistics
- Storytelling
header:
  image: assets/2026-07-27-better-safe-than-significant.webp
  overlay_image: assets/2026-07-27-better-safe-than-significant.webp
  overlay_filter: 0.8
  teaser: assets/2026-07-27-better-safe-than-significant.webp
  alt: 'A dark cave entrance in a forest, seen from a rainy path outside.'
  teaser_alt: 'A dark cave entrance in a forest, seen from a rainy path outside.'
excerpt: When something goes horribly wrong mid-experiment, should you stick to the plan or stop the test? A story about two statisticians, and possibly a bear.
---

In my [previous post](/publications/2026/07/18/the-boy-who-cried-type-i-and-type-ii-errors.html) I argued that shared stories help build a culture of experimentation. Here is another one from my collection. This one is about the awkward tension between statistical rigor and managing risk from unknown harm.

Practitioners are often taught that they should not "peek" at experiment results and stop as soon as they see something they like. Peeking inflates false positive rates and undermines the guarantees a test is supposed to provide. But this advice, taken too literally, can leave people feeling paralysed when something appears to be going badly wrong mid-experiment. Should they wait for the pre-registered sample size to be reached? Or should they pull the plug?

I wrote the following little fable to help practitioners reason about that tension. No statisticians were harmed in the making of it.

## A story about two statisticians, and possibly a bear

Two statisticians—Al-Khalil and Florence—went hiking in the woods together. Long walks away from civilisation are an excellent way to stimulate in-depth conversations about the nature of statistics while also staying physically fit and enjoying the nature of ... nature.

After a few hours of walking and talking, dark stormy clouds start to form overhead. Al-Khalil and Florence begrudgingly interrupt their conversation to review their options for not getting soaking wet. They are too far away from the parking lot to make it back in time, and they forgot to bring rain coats or umbrellas.

Suddenly, Al-Khalil spots a small cave in the distance. He suggests they run over to see if they can shelter there. Florence agrees, and they start to jog.

Once they arrive just outside the cave, Al-Khalil turns to address his companion. "You know, Florence," he says, "this is not Hampshire; this is the great outdoors." The two agree that they have no idea what dangers could be lurking inside that cave. Al-Khalil volunteers to enter first as an experiment and promises to report his findings back to Florence.

Slowly, Al-Khalil starts walking into the cave. After about ten paces, he turns a corner and disappears out of view. Florence, waiting outside while rain starts to fall, can still hear Al-Khalil's footsteps recede into the distance.

Then, suddenly, Florence hears something else. Something which sounds a lot like some big, furry mammal being roused from a deep slumber. Then there is a SLAP, a scream that sounds suspiciously like Al-Khalil, and finally a deafening silence emanating from the cave.

A few minutes pass while rain continues to fall and makes the only sound for miles around.

"Well then," Florence finally says to herself, "that was not really a well designed experiment, now was it? We did not agree to a fixed runtime, so I have no idea how long I should keep waiting here. Also, sample size is really, really small (i.e. 1); and I am not sure Al-Khalil is really representative of the overall population of interest (i.e. me). We did not even clearly formulate any hypothesis we were going to test in the first place!"

With no clear hypothesis being tested, and no clear experiment design to execute against, an increasingly soaked Florence quickly concludes that she has no idea whether the cave contains a bear, a cougar, a dragon, or a snickering statistician having a laugh at her expense. The dangerous, the fantastical, and the innocuous are all still within the realm of possibility.

But even in the absence of a good experiment, reliable data, or a strong conclusion, statisticians are sometimes able to make a clear decision.

Quietly and ever so slowly, Florence starts backing away from the cave. After a few backward steps, she quickly turns around and starts to run into the pouring rain.

## The moral of the story

Florence never learned what was in the cave. She has no data worth publishing, no p-value, no confidence interval. If a colleague back at the university asked her to prove there was a bear, she could not. And yet, running away was clearly the right call.

That is the tension worth sitting with. Statistical rigor is about drawing reliable conclusions from data. Risk management is about acting sensibly when the cost of being wrong is asymmetric. And some risks cannot be quantified at all—there is no metric for "probability of bear"—but they still have to be weighed. These two things usually align. When they don't, protecting users should come first.

In practice, this comes up most often when an experiment appears to be causing serious harm. A checkout flow that seems to be losing revenue at an alarming rate. A feature that is triggering a spike in customer complaints. A change that has broken something you did not think it could break. In each case, the responsible thing to do is stop the experiment, even though doing so means giving up on a clean statistical result.

A few things are worth being clear about when you do this:

1. **You are deviating from the plan on purpose.** The whole point of a pre-registered testing plan is that you follow it. If you stop earlier than planned because you saw a scary number, you are no longer running the experiment you designed. That is fine, but you need to know—and say—that this is what happened.
2. **You cannot claim the scary number was real.** Florence can honestly say she ran away because she was afraid there *might* have been a bear in the cave. She cannot claim there *was* a bear. In the same way, an aborted experiment tells you that you were worried enough to stop; it does not tell you that the harm you feared was genuine.
3. **Document the abort clearly.** Mark the experiment as aborted, not as concluded. Explain in writing why you stopped. Future colleagues (including future you) need to be able to tell the difference between "we tested this and it did not work" and "we got spooked and ran away".
4. **Sequential tests solve peeking, not panic.** Sequential testing methods let you look at results as they come in and stop as soon as the pre-registered criterion is met, without inflating error rates. This makes them a good option for monitoring, though fixed-horizon tests generally have more power and remain a reasonable choice for the primary experiment target. Either way, a sequential test only gives you valid inference about the metrics and stopping rule you designed for. If you abort because of something the test was not built to detect—a spike in complaints, an error rate you weren't tracking, a gut feeling that something is wrong—you are still stepping outside the plan. The statistics on the metrics you did register are fine; the decision to walk away is a judgement call that lives outside the test.

Florence's decision can also be automated. At Booking.com we built a [circuit breaker](/publications/2019/02/21/moving-fast-breaking-things-and-fixing-them-as-quickly-as-possible.html) that watches every new feature release for the first few minutes and aborts it automatically when severe user-facing errors spike. It deliberately cuts statistical corners—looser correction for multiple testing, approximate deduplication—in exchange for stopping bad releases within seconds rather than hours. The tradeoff is the same one Florence made outside the cave: when severe harm is suspected, speed of response can be worth more than waiting for a clean result. Building that kind of automated safety net is a good way to make the "better safe than significant" judgement explicit and repeatable, rather than leaving it to whoever happens to be watching the dashboard.

## Why a story?

I like this story because it separates two things that practitioners often conflate: the quality of the evidence and the quality of the decision. Florence has terrible evidence. Her decision is excellent. Once you have seen that gap clearly in a story about a cave, it is much easier to see it in a dashboard about a checkout flow.

It also gives teams a shared shorthand. "Are we sure there is a bear, or are we just spooked?" is a surprisingly useful question to ask in a war room at 2am. It reminds everyone that stopping is allowed, that stopping is sometimes correct, and that stopping honestly is very different from pretending the experiment concluded.

A good practitioner knows when to trust the procedure and when to override it. Blindly following the plan while the cave growls at you is not rigor; it is just stubbornness with a p-value attached.

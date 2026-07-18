---
title: 'The boy who cried type-I and type-II errors'
date: 2026-07-18
tags:
- Experimentation
- Statistics
- Storytelling
header:
  image: assets/2026-07-18-the-boy-who-cried-type-i-and-type-ii-errors.webp
  overlay_image: assets/2026-07-18-the-boy-who-cried-type-i-and-type-ii-errors.webp
  overlay_filter: 0.8
  teaser: assets/2026-07-18-the-boy-who-cried-type-i-and-type-ii-errors.webp
  alt: 'A young mountain sheep standing alone on a rocky ridge, looking directly at the camera against a blue sky with scattered clouds.'
  teaser_alt: 'A young mountain sheep standing alone on a rocky ridge, looking directly at the camera against a blue sky with scattered clouds.'
excerpt: Practitioners learn the definitions of type-I and type-II errors and then promptly confuse them. Here is a story that might help.
---

I have [previously written](/publications/2022/11/15/pancakes-and-experimentation.html) about how shared stories help build a culture of experimentation. Stories translate abstract ideas into intuitions. They act as mnemonic shorthands that stick where definitions slide off. And—perhaps most usefully—they let you correct a flawed approach without attacking anyone's intelligence. It is much easier to point to a character in a story who made a mistake than to tell a colleague they are wrong.

Type-I and type-II errors are a good example of a concept practitioners learn the definitions of, and then promptly confuse under pressure. I wrote the following little fable to help. It is a retelling of the classic "[The Boy Who Cried Wolf](https://en.wikipedia.org/wiki/The_Boy_Who_Cried_Wolf)".

## A story about a boy and his sheep

Once upon a time there was a boy named Aesop. Aesop lived in a small town in the mountains with his mother, several other villagers, and their flocks of sheep.

One day, the villagers heard a rumour that a fearsome wolf named *The Alternative Hypothesis* was spotted in the area. They worried that one of their sheep might be eaten, so they decided that Aesop should stand watch while the sheep were grazing in the mountains.

"Aesop," the villagers told him "your job will be to guard the sheep". The boy was then handed the ceremonial *Horn Of Significance*. "When you blow this horn, we will all come rush up the mountain" he was told. "Please use it only to warn us when the real wolf appears, because we do not want to come rush up the mountain in error."

Aesop begrudgingly accepted the horn and his new role.

Early the next day, Aesop trudged up the mountain together with the sheep for his first day on the job. Initially, the work seemed easy enough; the sheep grazed while Aesop sat quietly in the shade of a large tree. But after a few hours of watching grass grow, the boy grew increasingly bored.

"What if," Aesop wondered out loud "I had some friends to play with?" The boy stared at the horn in his hands. His friends were in the village below, far away. Suddenly an idea occurred to him. "What if," he mused "I could use this horn to bring all my friends up here, so I would no longer be alone?"

No sooner said than done. Aesop blew with all his might and the significant blare of the *Horn of Significance* filled the valley. Within minutes, all the villagers came running up the mountain hoping to chase away the wolf named *The Alternative Hypothesis* and save their sheep. However, upon arrival they found only a very bored boy.

"Oh, Aesop!" the villagers exclaimed. "How you have fooled us. We heard the significant signal and concluded that there must truly be *The Alternative Hypothesis*, but now we see the error we have made was one of the *First Kind*." Aesop was given a stern talking-to, no supper, and sent to bed early.

Early on the second day of work, the boy trudged up the mountain together with the sheep. Again the sheep grazed while he watched grass grow. The weather was hot and the job tedious. Soon Aesop grew sleepy from counting sheep. As he sat beneath the tree dozing, that fearsome wolf named *The Alternative Hypothesis* crept up on Aesop from behind. With one swift bite, the wolf gobbled up the boy whole.

Down in the valley, the villagers waited for the signal. They perked their ears trying to hear the positive sounds of the *Horn Of Significance*, but all remained quiet. The boy in the belly of the wolf could not blow the horn; the villagers could not hear a sound that was not made.

Later that evening, when Aesop and the sheep failed to return home, the villagers once again rushed up the mountain. There, they discovered the remains of their sheep and the discarded and unused *Horn Of Significance*.

"Oh, Aesop!", the villagers lamented. "How we have been fooled again. We failed to hear the significant signal and concluded that *The Alternative Hypothesis* was not amongst us, but now we see the error we have made was one of the *Second Kind*."

## The moral of the story

The villagers committed both a type-I and a type-II error, in that order.

1. First they heard the boy cry (i.e. got a significant result) and falsely concluded that there was a wolf. This is a *type-I error*, or error of the *First Kind*, also known as a *false positive*.
2. Then they heard no cry (i.e. got an insignificant result) and falsely concluded that there was no wolf. This is a *type-II error*, or error of the *Second Kind*, also known as a *false negative*.

A small terminology trap worth flagging: the words "positive" and "negative" here refer to the result of the significance test (significant: yes or no), *not* to the direction of the observed effect. A result can be both negative (e.g. we observe fewer visitors click a link) and simultaneously a false positive (e.g. the observed difference is significant by chance, while in reality there is no underlying effect).

The deeper point of the story, however, is one that technical audiences too often miss. Some say that "there is no believing a liar, even when he speaks the truth", but this is a mistake. The truth does not care whether it is spoken by a liar or a truth-teller, much like the horn does not care whether it is blown in error or not. We cannot fault a young boy for being bored. Rather we should blame the villagers for believing their error-prone methodology would help them catch *The Alternative Hypothesis*. Type-I and type-II errors are properties of the procedure, not failures of the analyst.

## Why a story?

I have used this story in workshops and conversations for years. People who could not, the day before, reliably tell you which of type-I and type-II is the false positive will happily explain, weeks later, what *The Alternative Hypothesis* is and why we should not trust the *Horn Of Significance*. The story sticks where the definitions slid off.

It also gives us shared shorthand. "Don't be the villagers" is a faster, kinder way to push back on a colleague's overconfident reading of a p-value than re-deriving the definition of significance. And because the mistake belongs to the villagers and their methodology—not to anyone in the room—the story makes it easier to discuss the error without anyone feeling stupid.

That, more than the mnemonic itself, is why I keep telling it.

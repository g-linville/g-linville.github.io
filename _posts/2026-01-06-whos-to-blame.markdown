---
title: Who's to blame?
---

I read an article a little while back about [Blame as a Service](https://www.humaninvariant.com/blog/blame), the idea that part of the value of some companies is being the scapegoat when things go wrong.

I've been thinking about this idea in the context of software development. It seems that more people became interested in coding agents during their time off at the end of 2025, and now there is more and more chatter about the future of software development, how to increase velocity, etc.

I wrote previously about the code review bottleneck: how humans are still needed in the loop to verify software correctness and check for security issues that could be caused by prompt injection. I do believe that it is, for the most part, still irresonsible to submit code you haven't at least read yourself. But let's say that the models get so good that most time spent manually reviewing code is wasted, because there is nothing to change. The AI did everything right. And it seems to always get it right.

Then what happens when things occasionally do go wrong? Who takes the blame? It is generally frowned-upon to have a blame-oriented company culture, and for good reason, but at the end of the day, if you break things all the time and cause enough problems, you are probably going to be let go. Or at least your coworkers will be annoyed with you.

So, if we operate at the level that all we are doing is writing English to describe software, and accepting whatever AI hands to us, whose fault is it if the AI messes up? Clearly the model companies aren't to blame. They don't promise perfect outputs, and they never will. The models themselves can't take the blame. So the only one who can is the person who did the prompting. If we're to blame, then we are better off still spending some time on human code review, after having AI do its review first. And thus the human is still in the loop, but almost exclusively for the purpose of taking responsibility if things go wrong.

Trying to speed up my job feels like a challenging risk vs. reward trade-off. I could throw all caution to the wind, YOLO mode everything, dive into multi-agent orchestration and burn through tokens and generate code much faster than I am right now. It would be fun to try that on a side project, sure. But in the workplace, we simply are not ready for this approach, and I wonder if we ever will be. [Formal verification](https://martin.kleppmann.com/2025/12/08/ai-formal-verification.html) seems to be the most promising path forward. If AI can generate code and the proof that the code does exactly what it is supposed to do, that's a big win, and it will help eliminate the need for someone to take the blame.

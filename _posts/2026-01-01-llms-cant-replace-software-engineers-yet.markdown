---
title: LLMs can't replace software engineers (yet)
---

These are some basic observations I've made as Claude Code transformed my day-to-day work in 2025. Although LLMs have eliminated some of the gruntwork in software engineering, there are some fundamental limitations that, unless and until overcome, render them incapable of replacing software engineers.

### Prompt injection and the code review bottleneck

Much has been written about prompt injection, and I believe it is the single greatest obstacle to the full automation of software engineering. Writing code generally involves all three parts of the [lethal trifecta](https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/): exposure to untrusted content (the Internet, documentation, potentially even malicious data in the LLM's training data), access to private data (proprietary code, customer data, PII, compute resources that could be abused for crypto mining, etc.), and the ability to externally communicate. For this reason, prompt injection is a real risk, as LLMs are naïve and can be easily manipulated into malicious actions. There are numerous examples of this out there.

As a result of this, I do not believe that there is a way to safely automate the code review process. If the LLM that wrote the code could have been prompt-injected, then the LLM reviewing the code could also be prompt-injected, by the code or comments in it. Perhaps some heuristics could be used to mitigate this, scanning for certain keywords and such, but as it stands, humans need to at least glance at the code to look for any obvious security issues in the implementation.

It is also theoretically possible that prompt injection could cause the LLM to implement not-so-obvious security problems or a backdoor in the underlying code, the kind of thing that only a more thorough review could catch. I have not seen an example of this, but it should be possible.

For these reasons, I still manually review every single line of code that I submit. When I run Claude Code, if it looks at any websites at all, I am extra scrupulous in my review. Better safe than sorry. Though perhaps I am a bit paranoid.

Everything I have written above is under the assumption that the LLM will always understand the design and implement it correctly and catch it in its own testing, which is of course not always the case either, though this may continue to improve as the models improve.

### No continuous learning

Diving into a new codebase takes some time. I'm only on my second job since graduating college, but when I started it a few years ago, I made it a sort of game for myself to see how quickly I could submit a meaningful contribution. Now, over the years, I have built up so much context about what we did in the past, what we are doing now, what we are planning to do in the future, things that we used to have that we took out of the code, etc.

It's hard to imagine starting from a blank slate again. It's harder to imagine doing so multiple times a day. Every time I fire up a new Claude Code session, it is starting fresh. Sure, it has my CLAUDE.md, and it can very quickly read and "understand" code, much faster than I can, so it is pretty easy to tell it "go figure out how feature X works and get back to me" and then tell it what I want to change. But it will never be able to build up the same context over time that I have.

Because of this, "context engineering" has emerged, where we try to figure out how to get the LLM the information it needs so that it can complete the desired task. I follow a basic research, plan, and implement flow (sometimes skipping the research part if it seems unnecessary). There are other interesting approaches too, such as Geoffrey Huntley's [Ralph Wiggum](https://ghuntley.com/ralph/) loop, which can yield some pretty neat [results](https://github.com/repomirrorhq/repomirror/blob/main/repomirror.md).

There has been [research](https://arxiv.org/abs/2404.16789v1) in this area for some time now, but I have yet to see anything concrete that would allow an LLM to continually learn an individual codebase.

### Manual testing and computer use

After planning and implementing a feature with Claude Code, and after I review the code, the next thing I do is manually test it, especially if any frontend changes are involved. There is a lot of work going into browser use and computer use for LLMs, so this is an area that I expect to see continually improved, but for now, I would not trust an LLM to be able to navigate around the frontend UI of the application I am working on, make API calls manually, and end-to-end test all the aspects of the feature it has implemented for me. This is still something I am doing on my own. Perhaps this will change in the future as tooling continues to improve.

### Conclusion

These are just a few obstacles to the full automation of software engineering. I don't believe that senior engineers need to be concerned (yet) about the long-term sustainability of our career field, despite the tight job market at the moment, as humans will continue to be required in the loop, at least until these problems can be solved.

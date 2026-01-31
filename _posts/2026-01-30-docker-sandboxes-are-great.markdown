---
title: Docker Sandboxes Are Great
---

Since writing my [previous post](https://blog.grant.place/2026/01/23/coding-agent-sandboxes-with-lima.html), I have ditched my custom sandboxing scripts for Lima in favor of Docker Desktop's new [sandbox feature](https://docs.docker.com/ai/sandboxes). It allows me to very quickly and easily set up micro VMs and sync my current project directory to them. It also installs Claude Code for me. I haven't even needed to create a custom template or wrap it in a script; just the normal `docker sandbox create` and `docker sandbox run` commands have sufficed for me.

I think my favorite feature it has, despite having not used it yet, is the private Docker daemon inside the VM. It basically comes with its own Docker inside, still completely isolated from the host. Given that [Obot](https://obot.ai) can use Docker to deploy MCP servers, this is great for me. My current workflow still uses the sandboxes almost exclusively for code generation (and not for actually running anything), but I am going to try to find ways to change that, and this will make it easier.

Occasionally, the git index in my repo gets corrupted while using Docker sandboxes. This is the only problem I have had with it. It's a simple fix: just a quick `rm -rf .git/index && git reset` and everything is good again. I assume it's a bug related to the file syncing.

Anyway, I recommend giving this feature a shot if you are interested in a safe environment to run your coding agents.

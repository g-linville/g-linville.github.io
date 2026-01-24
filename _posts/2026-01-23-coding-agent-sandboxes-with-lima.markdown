---
title: Coding Agent Sandboxes with Lima
---

Most of the repos that I work on at my job are open source, so there aren't any proprietary data concerns associated with them. This leaves me with freedom to accelerate my adoption of AI in software engineering. For a while, I struggled with figuring out how to easily create sandbox environments to run Claude Code in "YOLO mode" (`--dangerously-skip-permissions`). At first I tried devcontainers, but I was having trouble getting that properly integrated with Zed (which only recently shipped devcontainer support). Eventually, I came across a blog article explaining how the author used his coding agent to set up scripts to manage sandboxes with Vagrant. I looked into using Vagrant, but it looked like many of their base images had not been updated since 2024, so I decided not to adopt it.

After consulting AI, I came across [Lima](https://lima-vm.io/). I had heard of it before but thought it was more for running containers, but it turns out that with `limactl` you can easily set up VMs. It supports macOS and Linux. I use macOS at work (but Linux almost everywhere else), so I figured this would be a good option.

I used Claude Code to help me create a script called `sb` that acted as a mini CLI wrapper for `limactl` to easily set up Ubuntu VMs and sync files between the VM and my current code repo, and automatically install Go, Node.js, Claude Code, and other dev tools. My `sb` script provides simple commands like `sb create`, `sb list`, `sb shell`, `sb start`, `sb stop`, and `sb delete` to help me manage these sandbox VMs. Now I have disposable environments where I can run Claude Code, sign in, and then fire and forget a YOLO mode session while I go do something else. It is **so** nice not having to babysit the agent and approve commands like I do when it is running on my main system.

I'm not sharing any code here because I don't need to. This is easy to build yourself, once you know what tools to use. And my script is tailored to our main repo anyway. Go give this a try with your coding agent of choice!

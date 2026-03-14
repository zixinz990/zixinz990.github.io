---
title: "I've Made Peace with Vibe Coding"
date: 2026-03-14 18:14:00 -0500
categories: [Blog]
tags: []
---

## Falling Back Down the Rabbit Hole
On New Year's Day this year, I downloaded Cursor again and started a paid subscription.

Actually, during summer break last year, I used my .edu email to freeload off Cursor for a while, but I was just messing around with it then. The coding agents from early to mid-last year just weren't powerful enough. The generated code was often bloated, completely mangled my codebase, and still couldn't fully implement what I needed, so I uninstalled it pretty quickly.

Last spring, I used the web version of ChatGPT Codex to write a prototype for an iOS app. While the results were decent, Codex was way too slow, and configuring a runtime environment for a codebase on a web interface was an absolute pain. So, I retreated to my old workflow: hand-rolling code with web-based LLMs as an assist.

However, starting last fall, discussions around coding agents absolutely exploded. I figured maybe their capabilities had actually reached an incredibly high level, so why not give it another shot?

Once I tried it, there was no going back.

In January, I used Cursor to modify an open-source reinforcement learning codebase and wrote a solver in JAX, knocking out a ton of work in just two or three weeks. After starting my internship at RAI, I've been heavily using the company's Copilot Pro subscription every day—I simply can't stop. Gradually, Cursor and the Copilot plugin in VS Code weren't enough for me anymore. I started using CLI tools heavily to interact with coding agents, going back to basics straight to the command line. I even upgraded my personal Claude Code account to the $100/month Max tier, burning through tokens like crazy.

## The Thrill, the Exhaustion, the Nihilism, and the Programmer's Addiction

After more than three months of heavy use, the thrill is definitely there, but honestly, deep down, I mostly feel an indescribable sense of exhaustion and nihilism.

I used to be someone who loved reinventing the wheel because having absolute, total control over the entire process was a major reason programming brought me joy. I enjoyed typing out lines of code by hand, translating the symbols in my head into automated algorithms. In that process, you are an absolute god. But now, AI has stripped away that fun. A few lines of prompting can generate complete, runnable algorithm code. Not working well? Just feed it more prompts. That agonizing yet exhilarating experience of programming where you control everything seems to have devolved into useless "garbage time" in this era.

Programming used to be more than just a tool to me. But now, it has degraded into a purely utilitarian, semi-black-box tool. I've gone from being a Creator who enjoyed hands-on programming to a Manager who spends 99% of their time reviewing AI-generated code. This passive shift in identity is one of the reasons I feel so drained.

In the era of "artisanal programming," when we started building a large codebase, we'd usually spend a lot of time reading and understanding excellent open-source code first. Next, we'd mentally construct the rough architecture, write down the foundational boilerplate, and then stuff in various features bit by bit. When encountering a highly mathematical feature, we had to carefully study the underlying principles first, then implement it by hand. After going through that whole process, we'd have a profound understanding of the codebase's structure and details.

But now? If the goal is just the final deliverable, 90% of that process can be solved with a few lines of prompts. You don't need to understand it deeply; Lord AI will figure it out. This workflow that completely decentralizes the "self" makes me feel empty.

Even though my mindset can't adapt as fast as coding agents are evolving, I haven't dialed back my usage at all—because they are basically a hard drug engineered for programmers.

Even if you feel an inner emptiness, even if your brain feels like it can't spin anymore, you know that as long as you toss out a vague idea, the AI will quickly help you refine it, whip up a detailed plan that looks legit, and then put its head down to write and run the code. If the old programming experience was delayed gratification, then using coding agents now is like injecting drugs. This addiction is gradually draining my energy. Since I started using coding agents heavily, my actual daily working hours have noticeably increased.

What's worse is that using coding agents doesn't mean your brain gets a break. On the contrary, my brain is being whipped by the AI every day, forced into massive amounts of high-intensity thinking.

Writing a good prompt takes a lot of effort. If you want a coding agent to act completely according to your will, you have to think your requirements through clearly, use your knowledge and intuition to point it toward possible methods and directions for exploration, and simultaneously standardize your workflow completely. It's just like managing a subordinate: if you don't pave the way and explain the requirements thoroughly, what they deliver will rarely fully meet your expectations.

Take a specific example. A few days ago, I exported a policy trained and validated in Isaac Sim as an ONNX model and ran it in MuJoCo. The results were an absolute dumpster fire. This kind of failure obviously wasn't caused by a sim2sim gap; it was a configuration issue. At times like this, if you just simply tell the agent, "I ported the policy to MuJoCo and it sucks, quickly help me fix the bug," it's just going to stare blankly and start burning tokens trying random possibilities. What's more annoying is that the agent can't see the visual simulation results in MuJoCo; it can only read the generated data. It might be able to find clues in the data, but that burns a massive amount of tokens and wastes a lot of time.

This is where human experience and intuition become crucial. After watching the simulation video, I made an initial judgment that there might be an issue with reading the pose and coordinate system of specific objects in a certain environment, and the robot's walking control was super weird. So, I pivoted my strategy. I had the agent generate a ton of documentation based on my needs for me to read and compare. I stared at these docs to deepen my understanding of the task while interacting with the agent, until we finally smoked out and squashed the bugs one by one.

With AI's help, this process was absolutely faster than in the artisanal programming era. Since the company's codebase is massive with hundreds of contributors, if I had to find these tiny bugs all by myself, I'd probably be looking until my internship ended. However, during the entire interaction, knowledge flooded my brain at a speed far exceeding anything before. The brain isn't a machine, after all. Being washed over by such a massive torrent of information every day—it'd be weird if I wasn't exhausted.

Additionally, standardizing the workflow is extremely important for the stability of a coding agent's output quality, which is what many developers are working on right now. In recent months, skills and plugins have developed incredibly fast, and there are many highly powerful, ready-to-use workflows. But if you want to tackle a project with very specific goals, you still need to customize the workflow yourself, which is a very time-consuming and energy-draining process.

## What Changes and What Doesn't
After going through all this, I realized that the logic of software engineering is changing, but some things remain the same.

What constitutes "code quality" needs to be re-litigated. With the boost from coding agents, the speed of adding new features is faster than ever, and the cost of refactoring a codebase has drastically decreased. The old pursuit of certain qualitative metrics might ultimately become a stumbling block for product delivery.

A codebase's architecture, scalability, and maintainability are still absolutely crucial. This places even higher demands on a software engineer's foundational system design skills.

"Intuition" is very important; without good intuition, you can't use tools well. Cultivating intuition is a somewhat mystical process, but it's usually directly tied to engineering experience.

Workflow standardization. Workflow standardization. Workflow standardization. Important things bear repeating three times. You must use robust workflows to constrain the behavior of coding agents.

Personally, I feel the biggest impact of powerful coding tools is that the importance of the "human" is infinitely magnified. Only capable people can wield capable tools. Coding agents give everyone a dragon-slaying sword. People's baseline execution ability for building new things has been leveled up to the same starting line, and the gap created by engineering experience and education is gradually shrinking. Because of this, the importance of a person's intrinsic qualities, taste, and execution ability has been magnified like never before. This is a massive dividend for a small minority, but perhaps not for the vast majority, because most people lack these traits.

## Don't Be a Dinosaur

Sometimes, looking at the stuff I've built with AI's help, I can't shake the feeling that I didn't actually make it. My sense of accomplishment takes a massive hit, and I even get a guilty pang of impostor syndrome. But I have to change my mindset.

Back in the ancient times, programmers had to punch holes in paper tape to code. Then programming languages came along, and people started communicating with computers using human characters. Later, high-level languages became increasingly powerful and abstract—like the rise of Python, or the auto keyword flying all over the place in modern C++. Alongside the evolution of languages, programming tools have also advanced: from paper tape to computers, from pure CLI to IDEs, from flipping through manuals to code auto-completion, to AI auto-completion, eventually evolving into today's "vibe coding."

The ultimate goal of all this technological evolution is to make programming easier, to let humans converse with computers more naturally and quickly, and to have computers precisely execute what humans want to do. Fundamentally, they are all the same.

If I resist the revolution brought on by coding agents now, I'd be no different from those dinosaurs decades ago who insisted "clothes washed by hand are cleaner than those washed by a machine." Ultimately, I'd just be a laughingstock. The tide of technological progress never stops. Sticking to the old ways will only get you crushed on the beach by the waves.
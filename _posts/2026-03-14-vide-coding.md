---
title: "I've Made Peace with Vibe Coding"
date: 2026-03-14 19:08:00 -0400
categories: [Blog]
tags: [AI, Programming, Personal]
---

## Falling Back Down the Rabbit Hole

On New Year's Day, I reinstalled Cursor and finally made up my mind to purchase the subscription.

I'd used my .edu email to score a free trial last summer, but I was just messing around with it then. The coding agents from early-to-mid last year just weren't powerful enough. The generated code was often bloated, it would completely mangle my codebase, and it couldn't quite nail down my actual requirements. I uninstalled it pretty quickly.

Last spring, I used the ChatGPT Codex web interface to hack together a prototype for an iOS app. The results were decent, but Codex was painfully slow, and trying to configure a runtime environment for a codebase in a browser was a massive pain in the ass. So, I fell back into my old routine: hand-coding from scratch while keeping a web-based LLM open on the side for help.

However, starting last fall, the hype around coding agents absolutely exploded. I figured maybe their capabilities had actually gotten as insanely good as people claimed, so I decided to give it another shot.

And just like that, I was hooked.

In January, I used Cursor to modify an open-source reinforcement learning codebase and wrote a solver in JAX, knocking out a massive amount of work in just two or three weeks. After starting my internship at RAI, I've been heavily relying on the company's Copilot Pro subscription every single day—I literally can't stop. Eventually, Cursor and the Copilot VS Code plugin weren't enough. I started going hardcore with CLI tools to interact with coding agents, bringing everything full circle right back to the command line. I even upgraded my personal Claude Code account to the $100/month Max tier, burning through tokens like crazy.

## The High, the Burnout, the Emptiness, and the Programmer's Drug

After three months of heavy use, the high is definitely there, but honestly, what I feel most is an indescribable mix of exhaustion and emptiness.

I used to be someone who loved building things from scratch. Having total, absolute control over the entire process was a huge part of why programming brought me joy. I loved manually typing out lines of code, translating the logic in my head into automated algorithms. In that flow state, you're practically playing God. But now, AI has stripped that fun away. A few prompts can spit out fully functional algorithms. Not getting the results you want? Just feed it more prompts. That masochistic thrill of writing every line and controlling everything now feels like pointless busywork.

Programming used to be more than just a tool to me. But now, it’s degraded into a purely utilitarian, semi-black-box utility. Instead of a creator who loves the craft of writing code, I'm now a manager who spends 99% of my time reviewing AI output. This passive shift in my identity is a major reason why I feel so drained.

In the "old-school" days of programming, when starting a large project, we'd spend a lot of time reading and digesting excellent open-source code. Then, we’d sketch out the architecture in our heads, write the foundational boilerplate, and slowly stitch in the features. If we hit a mathematically complex feature, we’d have to study the underlying principles first, then implement it by hand. By the end of that process, we had a profound, intimate understanding of the codebase.

But now? If all that matters is the final deliverable, 90% of that grunt work can be wiped out with a few prompts. You don't even need to fully understand the mechanics; the AI will magically handle it. This workflow decenters the human element, and it leaves me feeling hollow.

Despite the fact that my mindset hasn't adapted as fast as these coding agents are evolving, I didn't dial back my usage at all—because they are basically a hard drug made for developers.

Even if you feel empty inside, even if your brain feels totally fried, you know that all you have to do is throw out a vague idea and the AI will quickly refine it, draft up a legit-looking plan, and crank out the code until it runs. If the old way of coding was about delayed gratification, using a coding agent is like shooting up. This addiction is slowly draining my energy. Since I started using them heavily, the actual number of hours I work every day has noticeably gone up.

And the worst part is, using a coding agent doesn't mean your brain gets to rest. On the contrary, the AI is basically acting as a taskmaster, constantly whipping my brain into overdrive.

Writing a solid prompt takes serious mental bandwidth. If you want a coding agent to do exactly what you want, you have to think your requirements all the way through, use your knowledge and intuition to point it toward the right approach, and rigidly standardize your workflow. It's exactly like managing a junior dev: if you don't lay the groundwork and explain the requirements crystal clear, whatever they deliver is going to miss the mark.

Take a specific example. A few days ago, I exported a policy trained and validated in Isaac Sim as an ONNX model and ran it in MuJoCo. It completely bombed. This obviously wasn't a sim2sim gap; something was messed up. In a situation like this, if you just tell the agent, "I ported this to MuJoCo and it sucks, fix the bug," it's just going to blindly guess and burn tokens trying random fixes. To make things worse, the agent can't see the visual simulation in MuJoCo; it can only parse the data logs. It might find clues in the data eventually, but that burns a massive amount of tokens and wastes time.

This is where human intuition and experience kick in. After watching the simulation video, my gut told me there was an issue with how the pose and coordinate system of specific objects were being read, and the robot's walking logic looked super weird. So, I pivoted. I had the agent generate a ton of documentation and logging based on my hypothesis. I stared at these docs to deepen my understanding of what was happening under the hood, bouncing ideas back and forth with the agent until we finally tracked down and squashed the bugs one by one.

With AI's help, this was undeniably faster than the old-school way. Because the company's codebase is massive with hundreds of contributors, if I had to hunt down these edge cases entirely on my own, I'd probably be at it until my internship ended. But during that whole back-and-forth, the sheer volume of information being shoved into my brain was unprecedented. The brain isn't a machine. Being blasted by a firehose of information like that every day—it'd be weird if I wasn't exhausted.

Furthermore, standardizing your workflow is absolutely critical if you want consistent output from coding agents. A lot of developers are realizing this right now. Over the last few months, the ecosystem of skills and plugins has exploded, and there are plenty of powerful, out-of-the-box workflows. But if you're tackling a highly specific project, you still have to build custom guardrails for your workflow yourself, which is incredibly time-consuming and draining.

## What Changes and What Doesn't

Going through all of this made me realize that the core logic of software engineering is changing, but some fundamentals remain untouched.

- **"Code quality" needs to be redefined.** With coding agents, the speed of shipping new features is off the charts, and the cost of refactoring has plummeted. Obsessing over old, rigid quality metrics might actually become a bottleneck for shipping products.
- **Architecture, scalability, and maintainability are more critical than ever.** This places an even higher premium on a software engineer's foundational system design skills.
- **Intuition is everything.** If you don't have good developer intuition, you can't leverage these tools effectively. Cultivating intuition is hard to pin down, but it almost always comes from raw engineering experience.
- **Standardize your workflow.** Seriously, standardize it. I cannot stress this enough. You have to build strong guardrails to constrain how the coding agent behaves.

Personally, I think the biggest impact of these powerful tools is that they infinitely magnify the importance of the human behind the keyboard. Only highly capable people can wield highly capable tools. Coding agents give everyone a cheat code. The baseline execution barrier for building new things has been leveled out, which is rapidly shrinking the gap created by traditional education and experience. Because of this, a person's intrinsic traits—their taste, judgment, and drive—matter more now than ever before. This is a massive advantage for a small minority of people, but probably not for the vast majority, simply because most people lack those qualities.

## Don't Be a Dinosaur

Sometimes, I look at the things I've built with AI and feel like I didn't really make them. The sense of accomplishment is muted, and the impostor syndrome hits hard. But I know I need to change my mindset.

Back in the stone age, programmers used punch cards. Then programming languages came along, and we started using human-readable text. Over time, high-level languages became increasingly powerful and abstract—look at the dominance of Python, or the auto keyword being thrown everywhere in modern C++. Tools evolved right alongside the languages: from paper tape to computers, from raw CLIs to IDEs, from reading physical manuals to autocomplete, then AI autocomplete, finally evolving into today's "vibe coding."

The endgame of all this technological evolution is exactly the same: making programming easier. It's about letting humans communicate with computers more naturally and having the machine precisely execute our intentions. At their core, these shifts are all fundamentally the same thing.

I totally get why people are cautious about using AI for production-level software development. Personally, I still can't fully trust AI-generated code. Plus, I'm the type of developer who obsesses over details that no one else will ever see or use, so I always review what the AI writes. I've actually caught it trying to "cheat" quite a few times just to satisfy my prompts—like the time Codex tried to pass a test by cranking up the tolerance a ten thousandfold...

But if I'm being completely honest with myself: has AI coding actually boosted my productivity? For me, the answer is a definite yes. To get the AI to write better code, I was forced to standardize my development workflows and code architecture, both of which are incredibly beneficial in the long run. On top of that, AI has drastically sped up how quickly I can understand other people's code, and it's made things like Git merges and rebases much more efficient. That's huge for team collaboration, especially since those processes used to drag on forever.

Every new technology has its fair share of unreliability when it first comes out, but over the years, those holes will get patched up one by one. I belive that if I resist this AI revolution now, I'm no different from the boomers decades ago who insisted "clothes washed by hand are cleaner than those washed by a machine." I'll just end up looking ridiculous. The wave of technological progress never stops. Refusing to adapt just means you're going to get left in the dust.
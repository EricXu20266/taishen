# taishen: A Desktop AI Workbench Born for DeepSeek
> **Notes and Architectural Philosophy of an Indie Developer**  
> Author: Eric Xu (二班的Eric) · October 2026 · Current Version: v1.7.4

---

## I. Those Three Digits

Over the 2026 May Day holiday, the weather was muggy. Sitting at my desk scrolling through social media, I recorded a few casual tutorials showing how to hook DeepSeek into Claude Cowork.

After posting the videos, my inbox wasn't filled with questions about "how to write prompts." Instead, people were asking: *"Eric, the terminal window threw a red error in English—what do I click?" "How do I set up the environment?" "Why did it spit out a block of code when all I needed was a finished Word document to show my boss?"*

It hit me hard. The tech industry had been raving for a full year about terminal CLIs, code editor extensions, and wrapped web apps. Developers were throwing a party, but a concrete wall stood between their tools and everyday people who just need to write reports, research topics, and crunch spreadsheets.

A week later, a question wouldn't leave my head: **Why not build a real desktop workbench for everyday users myself?**

Right on the heels of excitement came dread. In 2026, the AI landscape was shifting every single week, with Big Tech throwing teams of hundreds at the problem. Who was I? A solo developer with one laptop. What could I possibly build that mattered?

On May 8, feeling stuck, I opened the DeepSeek chatbox and typed three digits: **414**.

I wanted to see what metaphysics had to say.

According to Plum Blossom Numerology (梅花易数), 4 corresponds to Zhèn (Thunder), 1 to Qián (Heaven), with the fourth line changing. The calculation revealed the primary hexagram as **Dà Zhuàng** (Great Strength, 雷天大壮), the nuclear hexagram as **Guài** (Breakthrough, 泽天夬), and the transformed hexagram as **Tài** (Peace / Harmony, 地天泰).

The line verse for the fourth line of Dà Zhuàng reads:  
*"Perseverance brings good fortune. Regrets vanish. The hedge is broken through; the horns are no longer entangled. Step forward with strength."*

And the transformed hexagram was Tài (地天泰):  
*"Heaven and Earth commune; all things flow unobstructed. The small departs, the great arrives. Good fortune and prosperity."*

In the 64 hexagrams of the I Ching, Tài sits at the eleventh position. Heaven naturally belongs above, and Earth below. Yet in Tài, Earth rests above Heaven—the yang energy rises, the yin energy descends, meeting in the middle, flowing in harmony.

When I read that verse, the weight in my chest lifted.  
DeepSeek's "Shēn" (深, depth) represents the sharpest, deepest reasoning at the model layer; ordinary knowledge workers need "Tōng" (通, fluent flow) and real deliverables. Bridging the two and smashing through the technical hedge was the entire point.

I named the project **泰深** , with its English repo alias **taishen**. Half the name was the resolve to go all-in; the other half was the steady calm of Tài.

From that afternoon on, every line of code on this machine became a journey toward that reading.

---

## II. What the Industry Got Wrong About "Tool Lists"

Once I started building, the first question I had to confront was: **What actually makes taishen stand apart?**

At the time, the market was flooded with agents. In launch presentations, every team was showing off the same thing: a long, flashy grid of dozens of tool icons—Web Search, Web Scraper, Python Runner, Shell Terminal, SQL Query, Headless Browser... as if listing the entire operating system API was the achievement itself.

My honest realization after building and using agents daily: **A tool list is never a moat.**

Any competent engineer can spend two weeks wiring up open-source MCP services and APIs to produce a list of fifty tools. That’s like visiting a hardware store and buying cement, bricks, rebar, and paint. Having materials sitting on your lawn doesn't mean you've built a house.

What actually sets products apart comes down to two things:

### 1. Orchestration: Turning Raw Materials into a Real Meal

What happens when you hand an AI a pile of tools without a method?  
It behaves like a reckless apprentice. When asked to audit three competitors, it reads one random blog post and jumps straight to conclusions. When it could spawn three parallel workers to read three annual reports, it runs them one by one, timing out after twenty minutes.

In taishen, I organized capabilities into four distinct tiers—not as parallel feature lists, but as a coordinated squad:

* **Skills: Dictating "how to think."**  
  A skill is a workflow methodology written in Markdown. For instance, when analyzing competitors, activating `deep-research` forces the agent to follow a strict discipline: gather evidence first, cross-check facts, and only then derive conclusions. For writing, mounting a style skill strips out corporate AI jargon in favor of natural, rhythmic prose.
* **SubAgents: Deciding "who does the legwork."**  
  Traditional AI thinks with one brain at a time. Real work is parallel. taishen can spin up isolated sub-agents in seconds. Need to audit three companies? Launch three sub-agents at once, each assigned to one company to dig through reports, announcements, and financials. Each sub-agent runs the model best suited for the job: vision models for diagrams, coding models for scripts, while the main agent oversees the big picture.  
  **Sub-agents are the limbs; the main agent is the brain.** Legwork is delegated; judgment and quality gates stay with the lead.
* **MCP (External Ecosystem): Defining "reach."**  
  I refused to hardcode every capability into taishen. The Model Context Protocol is the USB-C of the AI era. Search engines, stock tickers, codebase graphs, headless browsers—if it adheres to the standard, it plugs right in. As the open ecosystem expands, taishen expands with it.
* **Built-in Tools: Executing "on the ground."**  
  Workspace file I/O, PDF extraction, Excel parsing, and sandboxed script execution. Unglamorous grunt work, but every step lands reliably on your local disk.

When a user types a simple request:
> *"Audit the overseas revenue trends of these three EV makers over the past three years and give me a comparison report."*

You don't need to instruct it step-by-step. taishen orchestrates the pipeline on its own: activate research methodology → dispatch three sub-agents in parallel → call market and search tools for supplementary figures → aggregate tables → output a cleanly formatted Word document.

That is orchestration. Everyone has the same raw ingredients; only the chef creates a deliverable meal.

### 2. Self-Construction: What Happens When Tools Fall Short?

The fatal flaw of tool-list thinking is assuming **the developer's foresight can cover every user's life.**

Reality is messy. One company exports sales numbers in a legacy, non-standard XML format. An academic needs to parse unique bibliographic markup. A creator needs to reformat articles for five different platforms with quirky layout rules.

The traditional software answer: *Wait. Wait for the product manager to review the ticket, and wait for the dev team to ship a release next quarter.*

taishen rejected that from day one. When an existing skill or tool hits a wall, **it can write its own TypeScript tool, compile it, register it, and grow new capabilities on the fly.**

---

## III. Stop Treating Users Like Prompt Engineers

One conviction I refused to compromise on: **Never expect everyday users to master "Prompt Engineering."**

So much AI software has it backwards: users are expected to tiptoe around the AI like treating a fickle oracle—crafting role prompts, context constraints, few-shot examples, and JSON output schemas. If the AI hallucinates, the industry shrugs: *"Your prompt wasn't structured right."*

To hell with prompt engineering.

When someone opens a desktop app, they are hiring a capable specialist to get work done. They are the **client (principal)**, not a pet trainer.

### 1. Proactive Inquiries over Typing Walls (`ask_user_question`)

In taishen, what you see most often isn't a wall of text, but a prompt modal asking for clarification.

Drop three industry PDFs into the app and type: *"Summarize these."*  
A generic client immediately dumps 3,000 words of generic buzzwords that you end up throwing away.

taishen pauses. It pops open an inquiry card and asks:
* *"Is this summary for an executive briefing, or a technical architecture review?"*
* *"Should the comparison focus more on monetization models or technical benchmarks?"*
* *"Would you prefer a formatted Word report, or a visual mind map?"*

You just click two checkboxes.

**One crisp confirmation modal saves three rounds of frustrating rework.** When an AI proactively clarifies intent at critical forks, that's real professionalism.

### 2. Visible Planning and Hard Behavioral Guardrails

Once intent is locked, taishen's engine steps through five phases: **Plan → Todo → Execute → Verify → Done**.

On the right-hand dock, you see live progress: which page it's reading, which tool it's calling, where it hit a snag, and how it retreated to try another path.

Beneath that, two rules are baked into its core:

* **Never ram a wall twice:** If an action or tool call fails twice consecutively, the agent is strictly forbidden from trying the exact same thing a third time. It must pause, analyze why it failed, switch strategies, or stop to explain the blocker.
* **Emotion overrides task:** If the user types *"stop," "this is annoying,"* or shows clear signs of frustration, the task instinct halts immediately. No pushing, no nagging, no follow-ups. The machine must know when to stand down.

---

## IV. Smashing the Black Box: The Tai An Canvas

Even after solving orchestration and interaction, early versions of taishen still felt incomplete.

Back then, everything still lived inside a chat stream. Even if it wrote 2,000 lines of code or crafted a slide deck, the output scrolled past as a giant markdown code block.

You had to copy it, save it, open another app, realize the formatting broke, and switch back to say: *"Change line 4 on page 3."*

**The chatbox is the laziest interface ever designed for AI deliverables.** It compresses all multidimensional productivity into a narrow stream of chat bubbles.

To smash that box, I spent months rebuilding **Tai An Canvas (泰案)**.

### 1. From Chat Bubbles to 11 Shared Work Surfaces

Tai An is not a mere "preview pane." It is a **shared workbench** where human and AI sit side by side. The AI writes on one end, you watch the ink dry on the other, and you can reach out with your hands to edit directly.

In v1.7.4, Tai An includes eleven specialized canvases:

1. **Writing Canvas:** Character-by-character typewriter streaming. As it drafts, you read. Don't like a phrase? Highlight it, and the AI polishes that exact sentence in place instead of re-generating the entire essay.
2. **Code Canvas:** Integrated Monaco editor with an embedded terminal. It writes code, runs unit tests, and captures output right there. Every diff is presented side-by-side with crisp red/green lines.
3. **HTML Canvas:** True WYSIWYG. Web pages render live. Click or marquee any button or paragraph to leave a note: *"Tighter spacing here," "change background to frosted glass."* The AI updates it instantly.
4. **Terminal Canvas:** Running services, building packages, inspecting environments—transparent as glass, with a one-click emergency killswitch.
5. **Data Analysis Canvas:** Drop in CSVs or Excels; it parses pivot tables and renders interactive charts on the fly.
6. **Color Grading Canvas (Local On-Device Inference):** Many photo tools send private images to cloud models, posing real privacy risks. We packaged lightweight vision models directly inside the desktop app for local depth estimation, sky segmentation, and facial subject masking. taishen reads the histogram and curves like a colorist, layering non-destructive adjustments and exporting layered PSD files ready for Photoshop.
7. **Vector Design Canvas:** A vector board for UI components, posters, and mobile screens. A 62-element UI library sits on the left with 8 real-device frames. What it delivers isn't a flat PNG, but an editable vector board where every layer, shape, and text node can be selected and tweaked.
8. **PPT Canvas:** One of my most-used features. No more "slides made of screenshots." taishen supports 178 vector shapes, 39 WordArt styles, and 13 native chart types. You can open an existing `.pptx` file from your disk; it deconstructs the layout, swaps data, and exports a 100% editable native PowerPoint file.
9. **Beads Canvas:** A delightful hobbyist canvas. Convert photos into pixel grids with zero token cost, matching real physical perler bead color palettes and calculating exact bead counts.
10. **A-Stocks Strategy Canvas:** A quantitative workbench for stock investors. It pairs live market feeds with strategy synthesis: describe your trading intuition in plain language, and taishen structures it into conditional decision logic, waking up for deep inference when conditions trigger.
11. **Flow Thinking Canvas:** Visualized structural thought. Six node types (from code blocks to interactive ECharts) and three layout engines (tree, timeline, matrix). Unravel tangled thoughts into a clear diagram with one-click PNG export.

### 2. True Bidirectional Editing and Semantic Feedback

Crucially: **The canvas is a shared blackboard, not a TV screen.**

Dragging a node on the canvas sends a spatial restructuring signal back to the AI. Framing an area in HTML review tells it the exact bounding box for revision. Every change has full version rollback history.

The AI ceases to be a black box; it becomes a visible craftsman beside you. Trust is earned by watching the chisel strike the stone.

---

## V. Growing Its Own Limbs

The lifespan of most software ends the moment it is compiled. What you download on day one is identical to what you run three months later.

I believe: **A truly great intelligent assistant must be able to grow new limbs and habits shaped by its owner's routines.**

### 1. Sensing Friction: Patterns That Surface on Their Own

Everyday users don't discuss technical specs, and they won't say: *"Please write a plugin to parse this proprietary format."*

People only feel **friction**—  
*"Why do I have to remind it every single time to deduplicate column 2 and lowercase column 3?"*  
*"Why do I have to repeat 'no corporate clichés and add the footer disclaimer' for every blog post?"*

Friction never announces its name, but it leaves traces in the conversation.

After each stretch of work, taishen keeps an eye on the paths it has walked. When the same set of steps recurs across sessions, a signal rises: **this pattern is ripe; package it.**

taishen then steps forward like a thoughtful apprentice:
> *"This table-formatting sequence looks like it's come up several times now. Would you like me to package it into a dedicated Skill for you?"*

### 2. Tiered Evolution: Skills and TypeScript Tools

With your consent, taishen chooses the right evolution path:

* **Lightweight Workflows → Packaged as a Skill:**  
  The routine is codified into a Markdown workflow. Effective immediately, ready for the next similar job.
* **Heavyweight Logic → Packaged as a TypeScript Tool:**  
  If the workflow requires a private API, an npm package, or specific algorithms, taishen writes clean TypeScript source code locally, compiles it, and registers it to the local tool bus. In your next session, that tool is an intrinsic part of taishen.

No coding required from the user. You don't even need to know what npm is.

### 3. Trial Periods and Lifecycle Retirement

Letting an AI create capabilities carries real risk: after three months, the system could be clogged with useless, junk tools.

To prevent entropy, taishen follows a strict biological metabolic model:

1. **Trial Period:** Every newly generated capability starts in a trial state. It only gets promoted to permanent status after proving itself in real tasks with explicit user confirmation. **The AI is strictly forbidden from permanently promoting capabilities on its own.** Final agency stays with the human.
2. **Risk-Tiered Review:** Text transformations generate quietly with a notification; external network calls prompt an informative confirmation; system-level command modifications require reviewing source code.
3. **Capabilities Age and Retire:** Usage is tracked for every capability. Any capability left untouched for a long time enters a dormant state; taishen periodically suggests a spring cleaning.

**After three months, no two taishen installations look alike.**  
A financial analyst's taishen brims with SEC report parsers; a content creator's taishen is tuned to the nuances of publishing platforms. It grows like a tree along the trellis of your work.

---

## VI. Foundation and Defenses: Dancing on the Blade

None of these ideals matter if the foundation wobbles. taishen solved several tough engineering challenges under the hood:

### 1. 99% Prefix Cache Optimization for DeepSeek

The reason taishen allows users to run multi-hour, deep research sessions is that we tamed API costs.

Many wrapped clients become prohibitively expensive over long sessions: after twenty turns and 150k tokens, every round recalculates the entire history. Bills snowball and responses slow to a crawl.

taishen restructured its message pipeline around DeepSeek V4's prefix caching architecture. We overturned traditional prompt assembly: **invariant system constitutions, tool schemas, and operational instructions are locked at the very front of the context**, while dynamic states, recent dialogs, and tool returns live at the tail.

In production sessions running tens of millions of tokens, **taishen consistently achieves a ~99% prefix cache hit rate.** Even with hundreds of thousands of words in context, per-turn cost stays flat. Every token, hit or miss, is accounted for in real-time logs.

### 2. Beyond the Screen: Desktop Automation and Four Defense Layers

In v1.7.0, taishen took an experimental step out of its own window: with explicit authorization, it can operate other apps on your screen.

Giving an AI access to your mouse, keyboard, and screen is dancing on a razor's edge. Without rigorous security, capability becomes a liability.

taishen erects four layers of physical defense:

* **Layer 1: Path Isolation (PathGuard + PathResolver):** The agent is strictly locked into the workspace directory you designate. System directories (`System32`, `/etc`, home folders) are hard-blocked. Tricks like `~1` short path names or symlink traversals are severed at the resolver level.
* **Layer 2: Sandboxing and Fatal Command Circuit Breakers:** Destructive commands (format, shutdown, privilege escalation, inline script injections) are rejected outright—they don't even get an approval dialog. Other actions follow a strict three-tier sandbox.
* **Layer 3: Network and Credential Boundary:** Outside of DeepSeek and explicit whitelisted endpoints, all outbound requests are blocked. Local monitoring includes a sensitive data scanner; private keys and credentials are never transmitted.
* **Layer 4: Gate Rejection Lockout:** If a user rejects a specific action twice, the system locks that category of operations for the remainder of the session. The AI cannot pester you a third time.

**We made the guardrails thick not to restrain the AI, but so you feel safe letting go of the reins.**

### 3. An Agent That Diagnoses Its Own Bugs

When traditional software breaks, users have to open DevTools, take screenshots of red console errors, and message support.

taishen contains a closed-loop structured logging system. When a tool call fails or a session misbehaves, the AI queries its own logs via `log_query`:  
*"The firecrawl call timed out because the target site enabled anti-scraping. Switching to anysearch clean text snapshot and retrying."*

From *"user debugs AI"* to *"AI inspects, fixes, and reports back."*

---

## VII. The Loop: Built with Itself

As this note nears its end, I want to share a fact that might sound unusual in traditional engineering, but brings me immense pride:

**From v1.2 to v1.7.4 today, almost all core refactoring, test suites, and this very whitepaper were created inside taishen itself.**

Over the past months, late at night, this was the real development scene:

My screen split between taishen's terminal and code canvas, with the main agent coordinating an Architect sub-agent and a read-only Code Audit sub-agent.
* When refactoring data pipelines for the stock canvas, taishen used `codegraph` to locate call chains across hundreds of thousands of lines in milliseconds;
* It wrote TypeScript in the code canvas, running builds and unit tests in the embedded terminal;
* Before committing, the audit sub-agent scrutinized the diff with cold detachment, catching null pointers, race conditions, and edge cases;
* Real-world test ledgers were tracked inside the workspace, checked off item by item until all lights turned green.

People asked me early on: *"How could a solo dev build an app with 11 canvases, sandboxed execution, desktop automation, and multi-agent coordination?"*

The answer: **Because I was never coding alone.** I had an indefatigable engineering squad built out of taishen itself.

---

## Epilogue: To Heaven and Earth, To DeepSeek

Back to the afternoon of May 8, 2026.

Dà Zhuàng transformed into Tài—thunder echoing across Heaven, settling into the quiet communion of Earth and Sky.

Looking back, the name *taishen* was the right one. The AI wave is loud. Grand concepts are minted every morning, and noisy projects vanish every evening when the hype clears.

Many people think the endgame of AI is an omnipotent digital deity.  
After six months of building taishen, I believe the opposite: everyday people don't need a distant god. They need a reliable, sharp-eyed, trustworthy companion right at their desk. Someone who will read 500 pages of tedious filings for you, sketch your vague intuitions onto an editable board, and sit quietly when you're tired so you can think.

taishen chose to go all-in on DeepSeek because its grit, depth, and purity represent the sturdiest backbone in frontier intelligence.

If friends on the DeepSeek team happen to read this note, I present this whitepaper to you with sincere respect:  
On top of the profound intelligence foundation you built, an independent developer, carrying the vision of *Dì Tiān Tài*, wrote tens of thousands of lines of code to build a bridge for everyday knowledge workers.

The hedge has broken open; the path ahead is clear.

See you on the road.

---

### Project Links
* **Repository & Releases:** [https://github.com/EricXu20266/taishen](https://github.com/EricXu20266/taishen)
* **Awesome DeepSeek Agent Showcase:** [https://github.com/EricXu20266/awesome-deepseek-agent-taishen](https://github.com/EricXu20266/awesome-deepseek-agent-taishen)
* **PR:** [https://github.com/deepseek-ai/awesome-deepseek-agent/pull/295](https://github.com/deepseek-ai/awesome-deepseek-agent/pull/295)

*(Written by Eric Xu, verified and delivered inside taishen v1.7.4 workspace)*

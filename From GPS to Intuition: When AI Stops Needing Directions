# From GPS to Intuition: When AI Stops Needing Directions

*Why the next AI advantage won't come from better prompts — and what to build today so you're ready when the shift arrives.*

---

If you're an engineer or tech lead who hasn't started structuring your team's domain knowledge into machine-consumable formats, every AI interaction you run is paying a tax you can't see yet. Every prompt you write, every AI workflow you ship, is doing extra work to compensate for a missing foundation.

And if you're outside R&D — in operations, product, finance, CEO-level leadership — and you're treating AI adoption as a small initiative that a few engineers will handle: you're underinvesting at the worst possible time. The most valuable AI asset your organization has isn't a model or a framework. It's the knowledge in your people's heads — your domain experts, your veteran operators, your decision-makers who carry years of compressed judgment. That knowledge doesn't structure itself. It requires dedicated time from your best people, across departments, not just in engineering.

Here's the uncomfortable truth: every person you add to this effort *now* has a disproportionate impact compared to adding them later. Domain knowledge extraction compounds — each structured artifact makes the next one faster to produce and more valuable in context. The teams that staff this work seriously today are building a lead that gets harder to close with every quarter that passes. And the humans doing this work are not a temporary bridge to automation. They are the irreplaceable pillar in this equation — a point this article returns to.

This article maps where the industry is right now, where the trajectory leads, and what's worth building today regardless of which AI model, framework, or paradigm dominates tomorrow.

---

## Why Coding Models Feel Magical — And What That Tells Us

To understand where this is heading, it's worth starting with why AI feels so much more capable at coding than at most other professional domains.

The answer isn't model architecture. It's training data. Coding models were exposed to decades of extraordinarily dense, structured, public material: open-source repositories, technical documentation, RFCs, postmortem reports, design debates, and implementation details from millions of projects. That concentration of high-quality signal is nearly unique among professional domains.

This raises a practical question. If the reason AI is "better at code" is that it absorbed decades of structured human knowledge about code, what would happen if it absorbed the same density of structured knowledge about *your* specific domain — your business logic, your architectural constraints, your decision patterns, your failure playbooks?

Most organizations look at the magic of coding models and conclude: "We need better prompts" or "We need a better model." But the deeper lesson is about the knowledge beneath the model. The magic wasn't in the architecture. It was in what the architecture learned from.

---

## The GPS Era: Where We Are Now

The industry's current answer to this gap has a name, even if nobody agrees on which name: context engineering, knowledge priming, harness engineering. Call it what you want. The mechanics are the same.

You take your team's knowledge — conventions, architecture decisions, naming patterns, anti-patterns, domain rules — and you structure it into machine-consumable documents. Then, before every AI interaction, you feed those documents into the context window. The model reads the briefing, and its output quality improves dramatically.

This is the GPS era of AI adoption. And it's converging fast.

Martin Fowler's team calls it "Knowledge Priming." Boris Cherny, creator of Claude Code, describes how his team maintains a shared `CLAUDE.md` file checked into git, updated multiple times a week. Dex Horthy gives a talk called "No Vibes Allowed," arguing that solving hard problems in complex codebases requires obsessive context curation. Viv Trivedy at LangChain writes about "Harness Engineering" — encoding your team's knowledge into the scaffolding around AI agents. Different people, different terminology, same discovery: **the quality of what you feed the model matters more than the model itself.**

Think about what GPS actually does. Before you drive anywhere, you enter your destination. The system loads the relevant map data. It calculates the route. And then, turn by turn, it tells you exactly where to go. You don't need to know the city. You don't need to understand the traffic patterns or remember which streets are one-way. The system compensates for your ignorance by feeding you directions in real time.

`CLAUDE.md` files, knowledge priming documents, and harness configurations are GPS for AI. They work. They represent a genuine leap over the previous era of "just prompt it and hope." Teams that are disciplined about this — teams that treat context as infrastructure rather than improvisation — are producing meaningfully better results than teams that aren't.

I don't want to diminish this. The GPS era is real, it matters, and if you're not doing this work yet, you should start immediately. Everything that comes later depends on it.

But GPS has a fundamental limitation that becomes obvious the moment you name it.

---

## The Tourist Problem

Every time you start a new session, the model arrives as a tourist.

It doesn't matter how brilliant the tourist is. It doesn't matter that they have access to the best maps ever drawn. Every single trip starts with the same ritual: load the map, read the directions, orient to the current position, begin navigating. The model has no memory of the last hundred trips it took through your codebase. It doesn't recognize the neighborhoods. It can't feel when something is off about a route because it has no accumulated sense of how your system breathes.

This is what practitioners are experiencing right now, even if they haven't articulated it in these terms. The `CLAUDE.md` gets longer. The knowledge priming documents grow. The harness configurations become more elaborate. Each session requires more tokens just to re-teach the model the basics of your world before you can get to the actual work.

Fowler's team calls this "manual RAG." They're right. It is. Every session is a retrieval operation: pull the relevant knowledge, inject it into context, hope the window is large enough, begin.

And it works. Like GPS works. You get where you're going. But you're paying a tax — in tokens, in latency, in the accumulated cost of re-teaching — that a local would never pay.

---

## The Deeper Question

*Note: This section touches on how transformer-based models process information under the hood. I keep it concise here to maintain the article's flow. For readers who want the full technical exploration — attention mechanisms, weight distributions, and why these architectural details matter for the thesis — I'm preparing a companion deep-dive.*

Here's where my thinking diverges from the current conversation.

The common assumption is that the solution to the tourist problem is more context: larger windows, better retrieval, smarter priming. Feed the model more, and it performs better. This is true, but I think it's treating a symptom.

The deeper issue is about how these models represent knowledge internally — and it starts with an uncomfortable fact about how transformers actually work.

Today's LLMs are built on the transformer architecture. Transformers don't "understand" text the way a human brain does. A human builds a mental model — a rich, interconnected web of causality, spatial reasoning, and lived experience. A transformer processes sequences of tokens through attention mechanisms, computing statistical relationships between every token and every other token in the context window. It's extraordinarily powerful pattern matching, but it isn't reasoning in the human sense. There's no persistent world model being maintained between sessions. There's no spatial intuition. There's a probability distribution over what token comes next, shaped by patterns seen during training.

This distinction matters for our thesis.

LLMs were trained on human-written artifacts — documentation, code, conversations, articles. These artifacts were written *by humans, for humans*. They use human narrative structures, human abstractions, human ways of encoding meaning. When we do knowledge priming, we're essentially translating our domain knowledge into better-formatted human-readable documents and feeding them into a system that processes information in a fundamentally different way.

When a coding model "understands" a design pattern, it doesn't carry a mental narrative about that pattern. It holds statistical weights — probability distributions over token sequences — that make domain-appropriate completions more likely. That's not a weakness to dismiss. It's a different kind of knowledge, and it's remarkably effective. But it means that the model's "native format" for knowledge is not human language. Human language is the input it was trained to process. Its internal representation is something else entirely.

So here's the question: **what if the first generation of AI knowledge curation — the GPS era — is us translating our knowledge into formats that are better for humans to write, when what we actually need is knowledge restructured for how models actually process information?**

The first wave of large language models was trained on human knowledge in human formats. That was the only option — it was all that existed. But the next wave might need something different: knowledge representations that were shaped by, or at minimum adapted for, the model's own statistical machinery. How exactly that restructuring works is still an active area of research. But the direction is clear — and it has practical implications for what we build today.

---

## From GPS to Knowing the City

Think about what happens when you actually *know* a city. You don't carry a map. You don't think in turn-by-turn instructions. You have a spatial model — an internal representation of the city that includes distances, neighborhoods, traffic patterns, shortcuts, vibes. When someone gives you a destination, you don't calculate a route step by step. You *feel* the direction and make fluid adjustments as you go.

This internal model looks nothing like written directions. It's not a more efficient version of GPS. It's a fundamentally different kind of knowledge — one that emerged from experience and reorganized itself into the brain's native format.

Now — a transformer doesn't develop spatial intuition in the human sense. That's not what I'm claiming. But it *does* develop something functionally analogous: shifted probability distributions that make domain-appropriate responses the default rather than the exception. The mechanism is different. The practical outcome — a system that no longer needs to be briefed on the basics — is the same.

That's the trajectory I believe we're on with organizational AI.

Imagine a model that was trained not just on your codebase, but on your company's business concepts, architectural invariants, decision patterns, failure playbooks, and the language your team actually uses when debating trade-offs. Not a generic model with a large context briefing — but a model whose default assumptions already reflect your reality.

In that world, the model doesn't start every task from a public-internet prior and then get corrected by a long prompt. It starts closer to the right mental frame. Its "first instinct" is already calibrated to your domain.

What changes?

Higher first-pass correctness on internal decisions — because domain constraints are part of the model's prior, not injections it needs to parse.

Better tool selection and task decomposition — because your domain's specific patterns exist in the model's internal representations.

Lower context overhead — fewer tokens spent re-teaching internal basics every session.

Faster convergence in ambiguous situations — because the model's default assumptions align with your organizational reality rather than the average of the internet.

The model stops being a tourist with excellent GPS. It becomes a local.

---

## You Can't Skip Drawing the Map

Here's where I need to be direct about sequencing, because the destination I just described is not where most teams should be focused right now.

The path to organizational priors runs through context engineering, not around it. You can't fine-tune a model on knowledge you haven't articulated. You can't adapt a model to your domain if your domain knowledge exists only in the heads of three senior engineers who've been there since the early days.

The map-drawing phase — turning tribal knowledge into structured, machine-consumable representations — is not a stepping stone to rush past. It *is* the work. And it has compounding value at every stage:

**For the organization itself:** Reduced bus factor. Faster onboarding. Traceable architectural decisions. Better code reviews. This value exists even if AI disappeared tomorrow.

**For the GPS era:** Every piece of structured domain knowledge you produce immediately improves your context engineering. Your `CLAUDE.md` gets better. Your knowledge priming documents become more effective. Your AI tools produce higher quality output today.

**For the future:** If and when organizational model adaptation becomes economically feasible, the teams that already have rich, structured, machine-consumable domain knowledge will be the ones who can move. Everyone else will be starting from scratch.

The investment compounds forward. That's what makes it defensible regardless of which direction the AI landscape takes.

One more thing worth saying explicitly: this isn't only an R&D story. The same logic applies to any department where expert knowledge drives decisions — operations, finance, legal, customer success. The organizations that recognize this early and begin structuring domain knowledge across the business — not just in engineering — will have a compounding advantage that purely technical teams can't match. But the same discipline applies everywhere: this knowledge must be maintained like code, with ownership, review cycles, and staleness checks. The moment it becomes "update the knowledge base when you have time," it dies — whether the team writes Python or spreadsheets.

---

## The Evolution Path

The journey has three phases. They're sequential in logic but overlap in practice:

**Phase 1: Draw the map.**

Build durable, machine-consumable knowledge about your domain. Not API docs or architecture diagrams — the deeper stuff. Why a system exists in business terms. What invariants must never break. What non-obvious decisions were made and their rationale. What external changes would force the system to evolve. What diagnostic reasoning experts follow when things break.

This knowledge should be stored as structured artifacts in the repo, next to the code it describes. Reviewable in PRs. Maintained with the same discipline you apply to code. Tagged as either ephemeral or durable so investment decisions are explicit.

The extraction process itself is hard — experts often can't articulate what they know, because their expertise has been compressed into intuition over years of experience. AI-assisted extraction (structured interviews where a model asks follow-up questions and reflects back for validation) can help surface knowledge that traditional documentation efforts miss.

**Phase 2: Use the GPS.**

Feed your structured knowledge into AI workflows. Measure the difference. Does the AI respect documented invariants? Does it avoid mistakes that only context-holders previously caught? Do code reviews find fewer AI-generated issues?

In this phase, AI also begins helping maintain the knowledge itself — flagging potential inconsistencies when code changes, drafting updates for human validation, detecting when documentation may have drifted from reality.

This is where most of the industry should be focused right now. The GPS era isn't a waiting room. It's where real value is created, real patterns are discovered, and real feedback loops are established.

**Phase 3: Learn the city.**

Fine-tune or continue-train on the curated internal corpus. Then evaluate rigorously: does the adapted model outperform a generic model with the same knowledge available in context? If yes, you've measured real internalization — the model has begun encoding your domain knowledge into its own weight distributions.

This phase carries real challenges beyond cost. Catastrophic forgetting — where a model gets better at your domain while losing general capability — is a genuine risk. Versioning and maintaining fine-tuned models as your knowledge corpus evolves adds operational complexity. Determining how much domain data is "enough" without overfitting requires careful experimentation.

But it's worth noting how fast this landscape moves. Techniques like LoRA and QLoRA have made parameter-efficient fine-tuning dramatically more accessible in just the past year. Problems that felt fundamental twelve months ago are becoming engineering challenges with known solutions. This is the rhythm of AI infrastructure: what seems like a research blocker today becomes a commodity tool tomorrow.

The question isn't whether to do it now — for most teams, the answer is not yet. The question is whether you'll be ready when the curve bends.

---

## The Governance Requirement Most People Skip

There's a trap in Phase 2 that deserves explicit attention.

When AI becomes both producer and consumer of internal knowledge — reading your domain artifacts to do its work, and also drafting updates to those same artifacts — you've created a feedback loop. Without governance, that loop can silently amplify errors. A small inaccuracy in a knowledge file gets reinforced by AI-generated code that embeds the inaccuracy, which then validates the original error when the AI later checks for consistency.

The control plane must include contradiction checks, staleness signals, confidence traces, and human approval on high-impact updates. This isn't bureaucratic overhead. It's the immune system your knowledge organism needs to stay healthy.

Design governance before autonomy. Not after.

---

## How to Test Whether the Model Actually Learned the City

If you ever reach Phase 3, here's the evaluation principle that separates real internalization from prompt leakage:

Keep a baseline — a generic model with access to the latest internal docs at inference time. It gets the full GPS treatment: all your knowledge priming documents, all the context you'd normally provide. Then test your adapted model on the same tasks, *without* providing those documents in context.

If the adapted model still outperforms the baseline despite not having the documents in its context window, you've measured something real. The model isn't just reading directions better. It has developed its own internal map.

If it doesn't outperform, you haven't achieved internalization — you've just shifted where the tokens live. That's useful information too. It tells you to keep investing in context engineering rather than model adaptation.

---

## Closing

General models will keep getting better. Larger context windows will arrive. Retrieval systems will improve. The GPS will get more sophisticated.

A reasonable counter-argument: maybe the GPS gets *so* good that internalization becomes unnecessary. If context windows grow to millions of tokens and retrieval becomes near-perfect, perhaps the gap between "excellent GPS" and "knowing the city" narrows to the point where model adaptation isn't worth the investment.

Maybe. But I don't think so — for two reasons.

First, knowledge encoded in a model's weights is fundamentally different from knowledge injected into its context window. Weights shape the model's default behavior — its reflexes, its first instincts, its pattern recognition. Context competes for attention with everything else in the window. A local's navigation isn't just faster than GPS. It's qualitatively different — it integrates with peripheral awareness, gut feelings, and the ability to improvise when something unexpected happens. Larger context windows don't change this dynamic. They just give the tourist a bigger map.

Second, I believe we're heading toward a world where organizations don't rely on a single massive general-purpose model for everything. Just as a builder doesn't use one tool for every job — they carry a toolkit, each tool shaped for a specific purpose — teams will increasingly work with smaller, domain-specific models tuned for particular tasks alongside general models for broad reasoning. The economics of smaller specialized models are fundamentally different from fine-tuning a frontier model, and they're getting more favorable every quarter.

But here's what matters most: regardless of which future arrives — the "GPS gets good enough" world or the "specialized models" world — the map-drawing work remains essential. In *both* scenarios, structured domain knowledge is the prerequisite.

We're not there yet. Most of us are still drawing the map, and that's exactly the right place to be. The map-drawing is not wasted work waiting for a better future. It's the foundation that makes every subsequent stage possible — and it pays dividends today.

So draw the map carefully. Use the GPS deliberately. And prepare for the day when the model doesn't need directions anymore — not because you stopped providing them, but because it learned the city.

---

*This article is part of the NiviGating AI series exploring how engineering teams can navigate the AI revolution with strategic clarity.*

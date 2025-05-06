# Agent Storming: A Strategic Design Practice for AI Architectures

> "Before the prompt comes the purpose. Before the code, the choreography."
> 

## Introduction

In the rapidly evolving field of AI agent design, we often rush to implementation details—selecting models, crafting prompts, and configuring tools—before establishing a clear architectural vision. This approach can lead to inefficient systems that fail to properly decompose complex cognitive tasks.

**Agent Storming** is a collaborative, visual, and strategic practice for designing AI systems, particularly those based on agentic workflows. Drawing inspiration from the Event Storming technique popularized in Domain-Driven Design, this practice helps teams break down complex AI-powered tasks into coherent, purpose-driven agent flows *before* diving into implementation specifics.

## Why "Agent Storming"?

The name was deliberately chosen to evoke multiple meanings:

- It captures the **brainstorming** and **structural decomposition** essence of the practice
- It suggests the convergence of **multiple minds (agents)** around a common mission
- It acknowledges the sometimes chaotic but ultimately clarifying nature of the process
- It maintains a connection to its Event Storming roots while focusing on agent-specific concerns

## The Six-Step Ritual of Agent Storming

When faced with a complex problem you want to solve using AI agents, follow these six steps. This process doesn't presuppose whether you'll ultimately implement a single-agent or multi-agent system—it allows the **task characteristics to shape the architecture**.

### 1. Define the Prime Intent

Begin by articulating the *core outcome* the AI system must achieve. This serves as your equivalent of a bounded context in DDD—it sets clear boundaries for the design exploration.

**Example:** "Help a finance team reconcile payment mismatches with minimal human involvement."

**Key Questions:**

- What constitutes success for this system?
- What is explicitly out of scope?
- Who are the primary stakeholders and users?

### 2. Deconstruct the Cognitive Workflow

Break the task into the **mental steps or phases** that a human expert would follow when performing this task. These are not technical functions or API calls—they are *reasoning chunks* that represent distinct cognitive operations.

**Example:**

1. Detect anomaly in transaction data
2. Classify type of mismatch (timing, amount, entity, etc.)
3. Research potential causes
4. Suggest resolution approach
5. Communicate status to stakeholders

**Key Questions:**

- What information is needed at each step?
- Where does uncertainty enter the process?
- Which steps require specialized domain knowledge?

### 3. Map Agent Roles to Cognitive Tasks

Now evaluate whether a single agent should handle the entire workflow or if the task would benefit from specialization across multiple agents.

**Guidelines for Single-Agent Architecture:**

- Tasks are sequential and tightly integrated
- Domain knowledge is unified
- Consistency of voice/approach is critical
- Context sharing between steps is extensive

**Guidelines for Multi-Agent Architecture:**

- Tasks require deep specialization in different domains
- Parallel processing would significantly improve performance
- Different reasoning patterns are needed for different steps
- Natural breakpoints exist where complete context transfer is possible

**Important Note:** Even in multi-agent setups, single-agent flows should exist within each agent. The "Episodic Memory Model" described in "The AI Agent Designer's Mindset" applies at both levels.

### 4. Define Interaction Contracts

For each agent (or between cognitive phases in a single agent), clarify what information must be passed, in what format, and with what guarantees.

Think of these as API contracts, but at the **cognitive reasoning** level:

- What inputs does each agent expect?
- What outputs must they produce?
- How do they signal confusion or request clarification?
- What error handling patterns should they follow?

**Example Contract:**

```
AGENT: Finance Reconciliation Specialist
RECEIVES:
  - Transaction record pairs with discrepancy
  - Current reconciliation policy document
PRODUCES:
  - Discrepancy classification
  - Proposed resolution with confidence score
  - List of questions if confidence below threshold
ERROR HANDLING:
  - If data incomplete, request specific missing fields
  - If pattern unrecognizable, escalate to human with explanation

```

### 5. Design Iterative Memory Anchors

This step directly applies the "Static High-Level Task, Dynamic Iterative Workflow" mental model I explored in depth in my article "The AI Agent Designer's Mindset: A Comprehensive Guide." As explained there:

> Think of the agent's goal as a static, high-level task that persists throughout the session. However, the workflow to achieve it is dynamic, since our context window is limited.
> 
> 
> You can imagine this as a human working on a problem in cycles:
> 
> - We **work for 10 seconds**
> - **Summarize our current progress** and what needs to be done next
> - **Close our eyes** (reset dynamic memory)
> - **Open our eyes again** with the high-level task still in mind
> - Read what we previously wrote, and **continue iterating**

This powerful metaphor, originally shared by the Anthropic team, captures the essence of how we must design agent memory systems. During Agent Storming, you'll translate this model into concrete memory anchors—deliberate checkpoints where your agents will:

- Generate context-efficient summaries
- Re-orient based on the prime intent
- Assess progress and determine next steps
- Maintain awareness across context boundaries

These memory anchors are critical for addressing the fundamental limitation of context windows in LLMs, helping your agents maintain coherence across multiple "episodes" of processing.

**Example Memory Anchors:**

- After data collection: "I've gathered transaction records from system A and B, identified 3 discrepancies in dates and 2 in amounts. Next, I'll classify each discrepancy type."
- After resolution: "I've recommended adjustments for all 5 discrepancies with 90%+ confidence. Next, I'll prepare the explanation report for the finance team."

Each memory anchor serves as a deliberate "eye-opening" moment where the agent reconnects with its prior work and the overall mission before continuing forward.

### 6. Test the Choreography Before Implementation

Before writing a single line of code or crafting prompts, simulate the agent interaction flow using pen and paper, whiteboards, or simple text exchanges.

This "dry run" should answer questions such as:

- Who initiates the process?
- What does each message contain?
- When does an agent escalate to humans?
- How are errors detected and handled?
- What happens if an agent goes off track?

Consider this a stage rehearsal before the software premiere—identify blocking issues, awkward transitions, or redundant steps before they become embedded in your implementation.

## Case Study: Research Paper Analysis System

Let's apply Agent Storming to design a system that helps researchers quickly extract insights from academic papers.

### 1. Prime Intent

"Enable researchers to understand the key findings, methodology, and limitations of academic papers in their field within minutes instead of hours."

### 2. Cognitive Workflow

1. Parse and understand the paper's structure
2. Extract core research questions and hypotheses
3. Identify methodology and experimental design
4. Summarize key findings and statistical significance
5. Analyze limitations and potential biases
6. Connect findings to the broader research landscape
7. Generate follow-up questions for deeper exploration

### 3. Agent Role Mapping

After analysis, we determine this would benefit from a multi-agent approach:

- **Document Specialist Agent**: Handles parsing, structure identification, and extraction (tasks 1-2)
- **Methodology Analyst Agent**: Examines research design and statistical approaches (tasks 3-4)
- **Research Context Agent**: Places findings in broader context and evaluates limitations (tasks 5-6)
- **Orchestrator Agent**: Coordinates the specialists and generates the final report with follow-up questions (task 7)

### 4. Interaction Contracts

Example contract between Document Specialist and Methodology Analyst:

```
FROM: Document Specialist
TO: Methodology Analyst
PAYLOAD:
  - Paper sections identified as "Methodology" and "Results"
  - Extracted research questions and hypotheses
  - Statistical tests mentioned in the paper
  - Key figures and tables with their captions
RESPONSE EXPECTATIONS:
  - Methodology classification and assessment
  - Validity of statistical approaches for the hypotheses
  - Key findings with confidence levels

```

### 5. Memory Anchors

For the Methodology Analyst:
"I've analyzed the A/B test methodology using a sample size of 500 participants. The statistical approach (ANOVA) is appropriate for the research question about differences between groups. The key finding of p<0.01 for the primary outcome is statistically significant. Next, I need to evaluate potential confounding variables mentioned in the limitations section."

### 6. Choreography Testing

A quick simulation reveals that the Document Specialist may struggle with heavily technical papers where domain knowledge is required to properly extract research questions. We adjust the design to include a preliminary domain classification step and domain-specific extraction strategies.

## Implementation Considerations

After completing the Agent Storming process, you'll be well-positioned to make informed decisions about:

1. **Framework Selection**: Choose between LangChain/LangGraph, CrewAI, or other frameworks based on your architecture needs
2. **Prompt Design**: Craft system and task prompts that align with your cognitive workflow
3. **Tool Integration**: Identify where external tools are needed to support agent reasoning
4. **Memory Systems**: Implement appropriate persistence mechanisms for your memory anchors
5. **Testing Strategy**: Develop scenario-based tests that validate your agent interactions

## Conclusion

Agent Storming isn't about drawing flowcharts or writing pseudocode—it's about **thinking like a team of thinkers**. By deliberately deconstructing complex tasks into cognitive workflows before implementation, you create agent systems that are more robust, maintainable, and effective.

Whether you're working with Claude, GPT, or any other LLM, remember that you're designing workflows of cognition. By giving your agents clarity of purpose and carefully designed interaction patterns, you'll unlock their full potential.

## Further Reading

If you found this Agent Storming methodology valuable, I recommend exploring my companion article **"The AI Agent Designer's Mindset: A Comprehensive Guide,"** which delves deeper into the mental models and design patterns that underpin effective agent systems. That guide explores additional concepts like:

- The Episodic Memory Model
- Prompt as Interface Design
- Tool-First Thinking
- Adapting traditional software engineering practices to agent design

Together, these resources provide a comprehensive framework for approaching AI agent design with the same rigor and thoughtfulness we've traditionally applied to software architecture.

---

*Note: Agent Storming works best as a collaborative process involving both domain experts and AI engineers. Consider running dedicated workshops with stakeholders to ensure the resulting architecture aligns with real-world needs and constraints.*


# 🤖 Claude + n8n Prompt: Auto-Generate AI Agent Workflows

This prompt helps you use Claude (or another capable LLM) to automate the generation of complete, production-ready n8n workflows using the AI Agent module. These prompts are based on the strategy demonstrated in the [referenced video](https://youtu.be/u2NluvotA80?si=Ol14JuL5kkEAr13c) and are optimized for generating valid, functional JSON workflows for AI-powered automations.

---

## 🧩 Step 1: Conceptualize Specialized AI Agents

**Prompt:**

> “I’m designing a multi-agent AI system using n8n. Please help me conceptualize a list of specialized agents for the following business use case:  
>
> [Insert business scenario here — e.g., lead qualification, support triage, social media sentiment response].
>
> For each agent:
> - Describe its purpose and key functionality.
> - Recommend public APIs and data sources it should use.
> - Focus on **verifiable and trusted APIs** to avoid hallucinations (e.g., OpenWeather, Stripe, Google Sheets, Twilio).”

---

## 🧠 Step 2: Generate JSON Workflows (Master + Sub-Agents)

**Prompt:**

> “Based on the list of agents and APIs, generate complete JSON workflow definitions compatible with n8n:
>
> - One **master orchestrator agent** that coordinates the execution and task routing
> - One workflow per **sub-agent**, handling its specific task
>
> Please ensure:
> - The output is **fully valid JSON**
> - Each agent workflow uses the **AI Agent node** in n8n (LangChain-based)
> - JSON includes all required fields: `nodes`, `connections`, `name`, `settings`, etc.
> - Workflows include **start triggers**, decision logic, and tool invocations where needed
> - JSON is safe to copy/paste into the n8n JSON import panel without modifications”

💡 *Optional instruction:* “Break long JSON into multiple parts if token limits are hit and label them Part 1, 2, etc.”

---

## 🧭 Step 3: Import into n8n

To use the workflows in n8n:

1. Open your n8n instance
2. Go to **Import Workflow**
3. Paste the valid JSON output into the editor
4. Click **Import**
5. Validate nodes and run test executions

---

## 🧱 Step 4: Add Multi-Level Agent Architecture (Advanced)

**Prompt:**

> “Extend this architecture to support **multi-level agent systems**, where:
>
> - Sub-agents can invoke **their own sub-workflows**
> - Each level still maintains clear control and logging
>
> Return updated JSON workflows and show which nodes have changed or were added.”

---

## 🧰 Technical Notes & Best Practices

- **n8n AI Agent Node**: Uses [LangChain framework], enabling tool use, memory, context passing
- **Tool/Function Selection**: Use `functions`, `API`, and `AI Agent` nodes together
- **Avoiding Hallucinations**: Only select **real, verifiable APIs** Claude is aware of
- **Error Handling**: Include fallback paths and logging in generated workflows
- **Maintain Modularity**: Each workflow should be standalone/testable

---

## ✅ Summary Workflow

1. Define the business use case
2. Prompt Claude to design agents + tools
3. Generate valid JSON for master + subs
4. Import into n8n
5. Test and iterate
6. Optionally nest agents for more complex flows

This prompt-based workflow can dramatically reduce your development time for LLM-based automation systems using n8n.

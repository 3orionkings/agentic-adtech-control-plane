# Agentic AdTech Vision

## Guiding Question

How do we evolve from manual, channel-centric campaign management to an **agentic control plane** that:

- understands auction mechanics and pricing/elasticity,
- automates search and performance channels safely,
- and continuously learns from attribution & measurement feedback,

while remaining **aligned with human goals and constraints**?

---

## Core Principles

1. **Objectives and guardrails first**  
   The system should be driven by explicit business objectives and constraints, e.g.:
   - “Maximize net subscriber LTV within a 6–9 month payback window.”
   - “Respect channel-level budget caps and brand safety rules.”
   - “Keep blended ROAS within [1.2, 1.5] while exploring new inventory.”

2. **Separation of planes**  
   - **Data plane** – events, identity, features, and measurement.
   - **Decision plane (agentic control)** – policies, bidding, budget allocation, experimentation.
   - **Execution plane** – downstream platforms (search, social, programmatic, onsite placements).
   - **Human plane** – strategy, oversight, constraint tuning, interpretation.

3. **Measurements are inputs, not truth**  
   Attribution, MMM, and experiments are lenses on reality. The control plane uses them as **inputs** to decisions, not as unquestioned truth.

4. **Exploration is a feature, not a bug**  
   Under uncertainty and information asymmetry, the system must:
   - explore bids and creatives,
   - run controlled experiments,
   - and surface learnings in a way that humans can understand.

5. **Human-in-the-loop by design**  
   Even when decisions are automated:
   - humans specify objectives and guardrails,
   - can simulate proposed changes,
   - can overrule the system with clear, auditable reasons.

---

## Three Horizons

### Horizon 1 – Automate search & performance channels

- Stabilize data foundations for search, social, and other performance channels.
- Introduce structured **policies** instead of ad-hoc rules:
  - target ROAS / CPA policies,
  - budget pacing,
  - keyword / audience tiering.
- Add simple learning mechanisms (e.g., bandits, bidding optimizers) while keeping humans in control.

Outcome: **Channel-level automation** that is robust and explainable.

---

### Horizon 2 – Unify measurement & decision-making

- Upgrade attribution to a **service** (multi-touch, MMM, experiments) with clear APIs and contracts.
- Build ICP and personalization infrastructure:
  - segment-level LTV & responsiveness,
  - audience-level ROAS and elasticity.
- Feed measurement outputs into a unified **decision plane**:
  - budget allocation across channels,
  - creative and audience selection,
  - pricing & promo levers when appropriate.

Outcome: **Cross-channel, cross-lever optimization**, grounded in a shared measurement fabric.

---

### Horizon 3 – Agentic control plane

- Introduce an **agentic interface**:
  - Humans set goals in higher-order terms:
    - “Grow active subscribers 20% YoY with neutral margin impact.”
    - “Ramp into channel X without degrading blended payback beyond Y months.”
  - The agent translates goals into constraints, experiments, and policies.

- The agent:
  - proposes plans (bids, budgets, experiments),
  - simulates impact based on learned models,
  - executes in controlled increments,
  - reports back in human language with **rationales and caveats**.

Outcome: A **closed-loop system** that continuously optimizes auctions, spend, and personalization across channels, with humans firmly setting the direction and constraints.

---

## Non-goals (for clarity)

- This is **not** about removing humans from the loop.
- This is **not** about blindly trusting a single model or KPI.
- This is **not** a vendor pitch or a specific implementation recipe.

It is a blueprint for **how to think** about agentic AdTech systems that can be safely deployed in scaled environments.

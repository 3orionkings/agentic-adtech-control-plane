# Automating Search & Performance Channels

Search and performance channels are the most natural starting point for automation and agentic control, because:

- the feedback loop is tight (impressions → clicks → conversions),
- the auction mechanics are explicit,
- and the cost of small, reversible experiments is relatively low.

This document outlines a phased approach.

---

## Phase 1 – Codify policies over manual knobs

**Goal:** Move from “optimizing by instinct” to **explicit policies**.

- Define channel-level objectives:
  - target ROAS ranges,
  - acceptable CAC and payback windows,
  - scale targets by market.
- Standardize metadata:
  - consistent naming for campaigns, ad groups, keywords/audiences,
  - clear mapping between business initiatives and campaign structures.
- Implement basic controls:
  - budget pacing and capping,
  - guardrails on max CPC / bid ceilings,
  - rule-based pausing of obviously underperforming elements.

Outcome: a system where humans still pull the levers, but the levers are **structured and observable**.

---

## Phase 2 – Learning policies and auction-aware optimization

**Goal:** Introduce learning systems under clear guardrails.

- Per-keyword / per-audience **value-per-click** estimation:
  - based on historical performance and cohort LTV where possible.
- **Bidding policies** that:
  - bid near estimated value-per-click (simple VCG-compatible logic),
  - explore occasionally to test new price points and inventory,
  - respect budget and ROAS constraints.

- Introduce **policy evaluation loops**:
  - counterfactual analysis where possible,
  - A/B tests between rule-based and learning-based policies,
  - safety monitors for anomalous spend, CPC, or conversion rates.

Outcome: channel-level optimization starts to scale beyond manual capacity.

---

## Phase 3 – Agentic orchestration across keywords, markets, and channels

**Goal:** Treat search and performance channels as a **portfolio** optimized by an agentic control plane.

- The agent:
  - ingests measurement signals (attribution, experiments, MMM),
  - updates beliefs about value-per-click and marginal returns,
  - proposes allocations:
    - **within** a channel (keyword, audience, creative),
    - **across** channels (search vs social vs display).

- Humans:
  - define global constraints (budget, ROAS bands, brand safety),
  - approve or adjust the agent’s proposed plans,
  - request simulations:
    - “What if we shift 10% from branded search to mid-funnel video?”
    - “What if we enforce a stricter payback bound on market X?”

Outcome: search and performance automation is no longer a collection of channel-specific tricks, but part of a unified, agent-driven control system.

---

## Agentic behavior in this context

An agentic system for search and performance:

- **Perceives**:
  - auction outcomes,
  - spend and performance by keyword/audience,
  - LTV by cohort,
  - measurement outputs (incremental lift, MMM).

- **Decides**:
  - how aggressively to bid,
  - where to shift budget,
  - what experiments to run next.

- **Acts**:
  - pushes updated bids and budgets,
  - triggers experiments,
  - updates campaign structures if necessary.

- **Explains**:
  - why it made those decisions,
  - what assumptions it relied on,
  - what would falsify those assumptions.

This mirrors how a strong human performance marketer operates, but at a scale and granularity that is impractical manually.

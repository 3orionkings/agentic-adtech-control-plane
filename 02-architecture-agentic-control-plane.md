# Architecture: Agentic AdTech Control Plane

This document describes a modular architecture for an **agentic AdTech control plane** that can:

- ingest and reconcile signals from multiple channels,
- run attribution and measurement,
- make auction-aware optimization decisions,
- and expose a human-centric interface for objectives and oversight.

---

## 1. High-Level Layers

### 1.1 Data & Identity Layer

**Responsibilities:**

- Capture events from:
  - web & app tracking,
  - CRM / lifecycle systems,
  - ad platforms (impressions, clicks, conversions, costs),
  - offline or 3P sources where applicable.
- Maintain an **identity graph**:
  - device ↔ user ↔ account ↔ household (where allowed),
  - channel and platform IDs mapped to internal IDs.
- Provide **feature stores** for:
  - user / account features (ICP, RFM, cohorts),
  - campaign / keyword / creative features,
  - contextual features (time, location, device, etc.).

**Outputs:** clean, queryable tables and feature sets with clear schemas and SLAs.

---

### 1.2 Measurement Layer (Attribution & Experiments)

**Responsibilities:**

- Offer attribution as a **service**:
  - last-touch, position-based, time-decay,
  - data-driven / model-based attribution,
  - clear versioning and configuration.
- Implement **MMM / MMM-lite** for:
  - cross-channel, including upper-funnel and offline,
  - diminishing returns and saturation.
- Run and manage **incrementality experiments**:
  - holdouts, geo experiments, lift studies,
  - experiment registry and metadata.

**Outputs:**

- Channel / campaign / audience level metrics:
  - incremental lift estimates,
  - attribution-based ROAS,
  - MMM-based marginal returns,
  - confidence intervals and stability signals.

---

### 1.3 Decision / Agent Layer (Control Plane)

**Responsibilities:**

- Encode **objective functions**:
  - maximize LTV subject to payback constraints,
  - blend ROAS, growth, and margin,
  - respect hard constraints (budgets, legal, brand safety).
- Maintain **policies** per domain:
  - search & performance (bidding, budget allocation),
  - lifecycle / CRM (send frequency, audience selection),
  - onsite placements (ranking, recommendations, promos).
- Implement **learning mechanisms**:
  - bandits and RL for bidding and budget shifts,
  - response & elasticity models for price / promo,
  - active experimentation design.

- Orchestrate **agentic behaviors**:
  - propose plans, run simulations,
  - decide what to change, when, and how fast,
  - escalate anomalies to humans.

**Outputs:**

- Concrete actions:
  - bids / bid modifiers,
  - campaign budgets and caps,
  - channel mix changes,
  - experiment designs (who, when, how long).

---

### 1.4 Execution Layer (Channels & Surfaces)

**Responsibilities:**

- Interface with downstream systems:
  - search engines and app stores,
  - social & display platforms,
  - programmatic DSPs,
  - internal ad servers / recommendation systems.
- Ensure:
  - correctness of API calls,
  - rate limiting and throttling,
  - monitoring and rollback hooks.

**Outputs:** real-world changes to spend, bids, targeting, and placements.

---

### 1.5 Human Interface Layer

**Responsibilities:**

- Provide surfaces for:
  - setting objectives and constraints,
  - reviewing recommended plans,
  - running simulations (“what happens if we…”),
  - monitoring performance and risk.
- Make decisions **explainable**:
  - “Why did we increase bids on keyword X?”
  - “Why did we reduce budget on channel Y?”
  - “What evidence supports this change?”

This is where a **GenAI/agentic UI** can add huge value:
- turn semi-technical queries into model calls,
- narrate decisions in business language,
- propose experiments and highlight blind spots.

---

## 2. Data Flow (Simplified)

1. **Collect & unify:** events and costs flow into the data layer; identity stitching creates a person-level or account-level view.
2. **Measure:** attribution, MMM, and experiments produce calibrated performance metrics and marginal return curves.
3. **Decide:** the agentic control plane:
   - reads measurement signals,
   - applies objectives and constraints,
   - computes updated bids, budgets, and tests.
4. **Execute:** channel APIs and internal systems execute changes.
5. **Observe:** outcomes (spend, response, LTV) feed back into measurement and learning.

Over time, this becomes a **closed loop** with humans supervising the loop rather than manually performing every step.

---

## 3. Design Considerations

- **Versioning & auditability**  
  - Every policy and model configuration should be versioned.
  - Decisions should be traceable: _which version of which policy produced this change_?

- **Safety & guardrails**  
  - Hard constraints for spend, bids, and exposure.
  - Kill switches and rollbacks for automated changes.
  - Safeguards against feedback loops and overfitting to short-term signals.

- **Interoperability**  
  - Measurement tools and bidding systems must speak a common language (shared entities and IDs).
  - New channels or surfaces should be “plug-in” additions to the decision layer.

- **Latency vs fidelity**  
  - Some decisions require near-real-time response (auction-level bidding).
  - Others can be done in slower loops (budget reallocation, ICP updates).
  - Architecture should support **multiple decision horizons**.

This architecture is intentionally abstract, but can be instantiated with concrete technologies (e.g., specific clouds, MLOps tools, or ad platforms) without changing its core principles.

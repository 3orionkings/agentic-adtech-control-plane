# Attribution, ICP, Personalization – Becoming Agentic

Automating auctions and bids without upgrading measurement and personalization is dangerous. This document outlines how attribution, ICP (Ideal Customer Profile), and personalization need to evolve to support an **agentic control plane**.

---

## 1. Attribution as a Service

### 1.1 From dashboards to APIs

Attribution should move from:

- “a report you look at once a week”

to:

- a set of **APIs** and **tables** that:
  - expose multiple attribution views (rules-based and model-based),
  - are versioned and documented,
  - can be consumed programmatically by the control plane.

### 1.2 Multiple lenses, one contract

- Support:
  - last-touch, position-based, time-decay for operational needs,
  - data-driven or Shapley-style models for better path understanding.
- Surface:
  - channel and campaign contribution,
  - audience / segment contribution,
  - stability and confidence metrics.

The agentic control plane treats these as **inputs with uncertainty**, not as ground truth.

---

## 2. MMM and Experiments – Anchors for Reality

Attribution is often biased. MMM and experiments are how we anchor back to reality.

- **MMM**:
  - captures cross-channel interactions and saturation,
  - provides marginal return curves by channel.
- **Experiments (incrementality)**:
  - geo tests, holdouts, or user-level RCTs where possible,
  - answer “what would have happened without this spend?”.

The control plane uses:

- MMM for medium-horizon budget shifts,
- experiments to validate and recalibrate,
- attribution for fine-grained operational allocation.

---

## 3. ICP and Personalization

### 3.1 ICP as a first-class object

Define **Ideal Customer Profiles** not just as a slide, but as:

- feature vectors and cohorts in the identity graph,
- with estimated:
  - LTV / payback,
  - channel responsiveness,
  - churn propensity.

### 3.2 Personalization and segment-level ROI

For each segment / ICP:

- estimate:
  - LTV by acquisition channel,
  - incremental response to offers and creatives,
  - sensitivity to frequency and cadence.

The agent can then:

- preferentially acquire high-ICP customers,
- adjust bids and budgets by segment,
- tailor creatives and offers at the edge of what’s operationally feasible.

---

## 4. Making Measurement & Personalization Agentic

An “agentic” measurement & personalization layer:

- **Surfaces uncertainty**:
  - confidence intervals,
  - stability indicators,
  - known blind spots.
- **Suggests experiments**:
  - “We are over-indexed on cohort X; run a holdout on channel Y to validate marginal impact.”
- **Advises the control plane**:
  - “De-prioritize channel Z for ICP A; MMM+incrementality both show low incremental value.”

Eventually, a GenAI interface can:

- answer questions like:
  - “Why did ROAS drop in market M last week?”
  - “Which ICPs are driving profitable growth in channel C?”
- propose actions:
  - “Consider shifting 5–10% of budget from channel C to D for ICP B; simulations suggest improved LTV at similar payback.”

Measurement and personalization, in this vision, are not static reports. They are **agents in their own right**, contributing recommendations and constraints to the control plane.

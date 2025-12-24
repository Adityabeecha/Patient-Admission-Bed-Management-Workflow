# Decision Logic – Patient Admission & Bed Management Workflow

This document explains the decision logic used in the TO-BE workflow and how automation, rules, and human oversight work together.

---

## Core Decision Objective

Determine whether a patient can be admitted immediately, should be placed in a smart waiting state, or requires human approval before proceeding.

---

## Key Inputs Used for Decisions

- Admission source (ER / OPD / Referral)
- Admission urgency level
- Required ward type
- Current bed availability
- Expected discharges in the near term
- Housekeeping turnaround time (mocked)
- Predicted time-to-bed availability

---

## Step-by-Step Decision Flow

### 1. Admission Trigger
An admission request is received via webhook, representing ER, OPD, or referral intake.

---

### 2. Context Preparation
Patient admission data and operational bed data are fetched (mocked using Set nodes).

---

### 3. Bed Availability Evaluation
A rule-based function evaluates:
- Whether a bed is available immediately
- Whether a bed is expected to become available shortly

**Logic summary:**
- If available beds > 0 → bed available now
- Else if expected discharges > 0 → predict ETA
- Else → no availability

---

### 4. Allocation Decision

- **If bed is available now**
  - Proceed with auto bed assignment

- **If bed is not available**
  - Place patient in a smart waiting state
  - Provide predicted ETA for availability

---

### 5. Human-in-the-Loop Check

Human approval is required when:
- Admission urgency is high
- AND predicted wait time exceeds a defined threshold

This ensures that edge cases and critical scenarios are reviewed manually.

---

### 6. Finalization

- Upon approval (or if approval is not required), the admission status is updated
- The workflow completes with a confirmed or pending admission state

---

## Role of AI in Decision Logic

AI is used as a decision-support tool, not as an autonomous decision-maker.

AI assists by:
- Explaining decisions
- Estimating confidence
- Supporting consistent reasoning

Final authority always remains with human coordinators.

---

## Design Principles Followed

- Rule-first, AI-assisted approach
- Human override for exceptions
- Transparency in decision flow
- Operational realism over technical complexity

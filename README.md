# Patient Admission & Bed Management – AI-Assisted Workflow (n8n)

This repository contains an AI-assisted, human-in-the-loop workflow for hospital patient admission and bed management, implemented using n8n.

The goal of this project is to demonstrate how operational workflows in healthcare can be redesigned using automation and decision support to reduce manual coordination, admission delays, and bed underutilization.

---

## Overview

Hospitals often rely on manual, reactive processes to manage patient admissions and bed allocation. This workflow demonstrates a future-state (TO-BE) approach where admission requests are orchestrated using rule-based logic, predictive signals, and human oversight.

The workflow is designed for clarity and realism rather than production deployment.

---

## Workflow Highlights

- Event-driven admission request handling (ER / OPD / Referral)
- Automatic fetching of patient and bed context (mocked data)
- Rule-based evaluation of bed availability and near-term capacity
- Smart waiting state with predicted ETA when beds are unavailable
- Human-in-the-loop approval for high-risk or urgent cases
- Final admission status update once a decision is confirmed

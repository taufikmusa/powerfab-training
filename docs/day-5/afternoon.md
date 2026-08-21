# Day 5 — Afternoon Session

- **Focus** — Automated events and full workflow review
- **Chapters** — 9 and 4.12
- **Modules** — Automated Events, Project Management

---

## 1. Automated Events

The **Automated Events (AE)** module runs scheduled tasks without anyone being logged in. It depends on the Remote Server service, which is why this section belongs with the system administrator rather than the general audience.

### 1.1 Report events

**Steps**

1. Open the **Automated Events** module.
2. Create a new report event.
3. Set the schedule — weekly on a Monday morning is a common pattern.
4. Select the report. Overdue RFIs and shipping summaries are the two customers request most.
5. Choose the output: save to a network folder, or email directly to project managers.

### 1.2 Email and failure notifications

**Steps**

1. Configure **Outgoing Email Settings** with the customer's SMTP details.
2. Set up **Failure Notifications** so the administrator is told when a scheduled task fails.

!!! warning "Automated events depend on the Remote Server service"
    If the Remote Server service is not running, scheduled events do not fire — and without failure notifications configured, nobody finds out. Confirm the service is set to start automatically with the server, and always configure failure notifications at the same time as the first event.

---

## 2. Full workflow review

This is the moment to connect the whole week back together.

**Steps**

1. Return to the **Project Management** module.
2. Open the **Project Summary Reports**.
3. Walk through how each section of the report was produced by something the participants did during the week — the estimate from Day 2, the purchase orders from Day 3, the production tracking from Day 4, the inventory movements from this morning.

!!! tip "Close the loop deliberately"
    Participants have spent five days working in separate modules. Showing that all of it converges into one report is what makes the system feel coherent rather than fragmented. Do not rush this — it is the summary that people remember.

---

## 3. Practice and open questions

Give the remaining time back to participants.

1. Let each participant work in the sandbox database unassisted.
2. Set the challenge: take one job from estimate through to shipping ticket.
3. Circulate, answer questions, and note anything that needs follow-up support after the training.

!!! tip "Use the implementation exercise as the practice script"
    The [Implementation workflow](../implementation/index.md) provides a complete 18-step path for exactly this purpose, including the roles involved at each stage.

---

## Wrap-up checklist

- [ ] One automated report event created and scheduled
- [ ] SMTP settings and failure notifications configured
- [ ] Project Summary Report reviewed against the week's work
- [ ] Each participant has attempted a full job in the sandbox
- [ ] Follow-up items recorded and support contacts handed over

## Exercise

!!! info "To be completed"
    Add the afternoon exercise steps and supporting screenshots.

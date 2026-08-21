# Day 3 — Morning Session

- **Focus** — Project Management and Combining
- **Chapters** — 4 and 5
- **Modules** — Project Management, Combining

---

## 1. Initialising the project

The **Project Management** module is the hub that ties everything together. It pulls data from Estimating, Combining, and Production Control, and it is where project managers spend most of their time.

**Steps**

1. Create a new **PRJ** job.
2. Add the relevant firms — client, detailer, engineer, erector.
3. Link the estimate created on Day 2 to this project.

Linking the estimate matters more than it appears. It is what allows the project summary reports on Day 5 to compare estimated against actual.

---

## 2. Document control

### 2.1 Drawing logs

**Steps**

1. Open the drawing log for the project.
2. Use **Batch Insert – From Files** to import detailing and design drawings in bulk rather than one at a time.

### 2.2 Transmittals, RFIs, and change orders

**Steps**

1. Create a transmittal and issue it to a firm from the Address Book.
2. Raise an RFI, set the required response date, and attach supporting files.
3. Close the RFI once a response is received.
4. Create a change order and note how it links back to the project cost.

!!! tip "The Address Book pays off here"
    Every document in this section pulls its recipients from the Address Book configured on Day 1. If firms were entered with the wrong Firm Type, participants will discover it now — which is a useful teaching moment rather than a problem.

---

## 3. Scheduling and contracts

**Steps**

1. Apply a schedule template, such as the **Structural** template.
2. Adjust task durations on the Gantt chart to match the real programme.
3. Set the **Initial Baseline** so future progress can be measured against the original plan.
4. Create a Schedule of Values and raise a single invoice against it.

!!! warning "Three known behaviours to warn participants about"
    **Edit mode times out at 180 seconds.** Changes not saved within that window are lost without warning. Save frequently.

    **Date typos are silent and destructive.** A mistyped year turns a four-month programme into a four-year one, and the Gantt chart will happily display it. Verify each date after entry.

    **Apply Template is not idempotent.** Clicking it a second time silently duplicates every task in the schedule. If the task list suddenly looks twice as long, this is why.

---

## 4. Combining and the Advance Bill of Materials

The **Combining (CMB)** module exists to solve a timing problem: mill lead times are long, but detailing takes weeks. Combining lets the company order main members early, off a preliminary model, before connection design is finished.

**Steps**

1. Import a CMB job via IFC or KISS.
2. Review the resulting Advance Bill of Materials.
3. Load the material to a purchasing requisition.

!!! info "Why this module exists"
    Without an advance bill, the shop waits for detailing to finish before ordering steel, and the mill lead time then sits entirely on the critical path. Ordering main members early can pull weeks out of a programme — this is usually the clearest ROI story in the whole system.

---

## Wrap-up checklist

- [ ] PRJ job created with firms attached and estimate linked
- [ ] Drawings batch-imported into the drawing log
- [ ] One transmittal issued and one RFI raised, attached, and closed
- [ ] Schedule template applied once, dates verified, baseline set
- [ ] Advance Bill imported and loaded to a requisition

## Exercise

!!! info "To be completed"
    Add the morning exercise steps and supporting screenshots.

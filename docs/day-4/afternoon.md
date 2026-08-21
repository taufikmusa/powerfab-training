# Day 4 — Afternoon Session

- **Focus** — Quality control, shipping, and change management
- **Chapters** — 7.4 – 7.6
- **Modules** — Inspection, Load Tracking, Production Control, Trimble Connect

---

## 1. Inspection and quality control

The **Inspection** module can run tests against assemblies, parts, equipment, and even employee certifications.

**Steps**

1. Configure an inspection test in the office.
2. Run the test from **Tekla PowerFab Go**.
3. Deliberately fail a piece — a missing cope is a realistic example.
4. Attach a photograph taken on the mobile device.
5. Demonstrate that the failed piece now blocks piece tracking and shipping.
6. Run a **Follow-up Test** to clear the failure and release the piece.

!!! tip "Inspection requirements can exist independently of routes"
    A quantity mismatch between a QC station and a cut list is not always an error. During a live session, a QC station showed 19 items against an expected 17. The cause was a UC column main mark carrying a standalone inspection requirement pointing at *Sample - Quality Control*, entirely independent of any route assignment. It was confirmed by matching weights exactly.

    When quantities disagree, check the main mark for standalone inspection requirements before assuming the route is wrong.

---

## 2. Load tracking and shipping

### 2.1 Basic shipping

**Steps**

1. Go to **Production Control > Load Tracking**.
2. Create a new load and assign a trailer.
3. Add material to the load.
4. Generate the shipping ticket.
5. Repeat the same process in PowerFab Go to show the yard workflow.

### 2.2 Shipping calendar

**Steps**

1. Open the **Shipping Calendar** dashboard.
2. Drag a load to a different delivery date and observe the schedule update.

Dispatchers respond well to this screen — it replaces the whiteboard most yards are still running on.

### 2.3 Intermediate shipping

**Steps**

1. Configure a **Shipping Route** that sends material to a third party, such as a galvaniser.
2. Ship material out to the third party, then onward to the final job site.

!!! warning "Office does not enforce route completion before shipping"
    Confirmed live: **Tekla PowerFab Office** will allow a load to ship even when route stations are incomplete. **Tekla PowerFab Go 2026** does enforce the requirement that all route stations be complete.

    This asymmetry means an office user can ship steel that the shop has not finished. If shipping discipline matters to the customer, the control has to come from process — or from routing shipping through Go — because Office will not stop it.

---

## 3. Change management

Revisions are inevitable, and how a shop absorbs them determines how much rework it eats.

**Steps**

1. Import a revised `.pfxt` or `.xml` file into the active job.
2. Open the **Change Summary Screen** and identify what has changed — modified lengths, added parts, deleted assemblies.
3. Use the **Model Comparison** tool in Trimble Connect to see old and new assemblies side by side.
4. For each change, decide whether to **Accept**, **Prevent**, or **Save for Later**, based on how far the shop has already progressed.

!!! info "The decision is a production decision, not a data decision"
    A change to a piece that has not been cut is trivial to accept. The same change to a piece already welded and painted is a rework order. This screen is where production knowledge has to meet the model, which is why the production manager should be the one driving it — not the detailer.

---

## Wrap-up checklist

- [ ] Inspection test configured, failed with a photo, and cleared by follow-up test
- [ ] Load created, material added, shipping ticket generated
- [ ] A load rescheduled on the Shipping Calendar
- [ ] One shipping route configured through a third party
- [ ] Revision imported and each change accepted, prevented, or deferred

## Exercise

!!! info "To be completed"
    Add the afternoon exercise steps and supporting screenshots.

# Day 4 — Morning Session

- **Focus** — Cut lists, work packages, and piece tracking
- **Chapters** — 7.0 – 7.3
- **Modules** — Production Control, Tekla PowerFab Go

---

## 1. Cut lists

A cut list converts combined material into a specific, actionable batch of work for one machine operator on one shift.

### In Tekla PowerFab Office

**Steps**

1. Go to **Review > Cut Lists**.
2. Create a new cut list and save it with a meaningful name, such as *Monday Morning Saw Batch*.
3. Use the **Prioritization** tool to sequence the work in the order the shop should tackle it.
4. Generate the cut list report for the operator.

!!! warning "Common navigation error"
    New users frequently go to **Dashboards > Cut List Management** when trying to create a cut list. That screen manages cut lists that already exist. Creation happens under **Review > Cut Lists**.

### In Tekla PowerFab Go

**Steps**

1. Log in to PowerFab Go on the tablet.
2. Tap **Cut Lists** and open the assigned list.
3. Select the heat number of the stock being cut.
4. Process the cut.
5. Record the **drop location** for any remnant.

!!! tip "Drops are money"
    A remnant recorded with a location goes back into inventory as usable stock. A remnant processed without one is effectively written off. Make this point on the shop floor, not just in the classroom — operators are the ones who decide whether it happens.

---

## 2. Work package management

**Steps**

1. Open the **Work Package Management** dashboard.
2. Release a package to the shop floor, making it visible to operators in PowerFab Go.
3. Place a different package **On Hold** and confirm it disappears from the operator view.

Release control is what stops the shop from starting work that engineering has not cleared. Production managers usually grasp its value immediately.

---

## 3. Piece tracking

Piece tracking moves material through the stations and routes configured on Day 3. This is where that setup work proves itself.

### In Tekla PowerFab Office

**Steps**

1. Open the piece tracking screen.
2. Track a single assembly through one station.

### In Tekla PowerFab Go

**Steps**

1. Tap **Production Tracking**.
2. Use **Add Batch** to move an entire work package through a station in one action.
3. Repeat at the next station in the route.

Then show the results in two places simultaneously:

- The **Production Status** screen in the office, updating live
- The 3D model in Trimble Connect, recolouring as statuses change

!!! warning "Production Status is a report, not a configuration screen"
    Participants often open **Production Status** expecting to change station settings there. Station configuration lives in **Fabrication Maintenance**. Production Status is read-only progress reporting.

!!! warning "Blank Station Summary usually means a missing route"
    If tracking appears to work but the Station Summary stays empty, the material almost certainly has no route assigned. Return to the routing step from Day 3 rather than troubleshooting the tracking screen.

---

## Wrap-up checklist

- [ ] Cut list created under **Review > Cut Lists** and prioritised
- [ ] At least one cut processed in PowerFab Go with a drop location recorded
- [ ] One work package released and one placed on hold
- [ ] A batch tracked through two stations from a tablet
- [ ] Production Status and Trimble Connect both confirmed updating

## Exercise

!!! info "To be completed"
    Add the morning exercise steps and supporting screenshots.

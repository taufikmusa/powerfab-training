# Day 3 — Afternoon Session

- **Focus** — Production Control setup and Purchasing
- **Chapters** — 6.0 – 6.15
- **Modules** — Production Control, Purchasing, Inventory

---

## 1. Importing the final Bill of Materials

**Steps**

1. Create a new **Production Control (PDC)** job.
2. Import the final BOM through **PowerFab eXchange** — a `.pfxt` or `.xml` file produced by the detailer.
3. Map user-defined attributes (UDAs) from the model to Tekla PowerFab fields.
4. Import the associated CNC files.
5. Upload the model to **Trimble Connect** for visualisation.

!!! tip "UDA mapping is worth doing properly"
    UDAs are how model information that has no native Tekla PowerFab field — erection sequence, finish requirements, client part references — survives the handover. Mapping them once during setup avoids manual re-entry for the life of the project.

---

## 2. Project breakdown and routing

### 2.1 Sequences and lots

**Steps**

1. Assign sequences and lots to assemblies manually in the grid.
2. Repeat the exercise using the Trimble Connect model interface, selecting assemblies visually.

Show both methods. Office staff generally prefer the grid; project managers reviewing erection order almost always prefer the model.

### 2.2 Work packages

**Steps**

1. Group assemblies into work packages.
2. Use the **Smart Create** tool to generate packages based on sequence, lot, or other criteria rather than building them by hand.

### 2.3 Stations and routes

A route defines the path a piece takes through the shop — for example, Saw → Fit → Weld → Paint → Ship.

**Steps**

1. Build a fabrication route from the available stations.
2. Apply the route to the imported material.

!!! info "Menu change in PowerFab 2026"
    **Station and Route Setup** moved from directly under *Maintenance > Production Control* into a new **Fabrication Maintenance** submenu in Tekla PowerFab 2026. Older reference material points at the previous location.

!!! danger "Assign routes before building cut lists"
    This is one of the most costly sequencing mistakes in the system, and it was confirmed live during a technical enablement session.

    If material is cut and processed *before* a route is assigned, applying the route afterwards does **not** back-fill completion credit for the cut station. The Station Summary remains blank even though the cuts were genuinely processed, and the only remedy is to add completed entries manually, piece by piece.

    Make route assignment part of the setup routine, not something done later when someone notices it is missing.

!!! warning "Check the TFS Station default"
    Routes can default their **TFS Station** to the *last* station rather than the first. On a Sample SP route this appeared as *Sample - Erection* instead of *Sample - Cut/Saw*. Material taken from stock is then credited at completely the wrong point in the route. Verify this field on every route before processing any cut list.

---

## 3. Linking the advance bill and completing procurement

### 3.1 Linking CMB to PDC

**Steps**

1. Link the Advance Bill (CMB job) to the final BOM (PDC job).
2. Run the comparison report.
3. Review the **Critical Differences** — most commonly, a detailed length that exceeds the length actually ordered.

This comparison is the safety net for early procurement. It answers the question every purchasing manager asks: *did what we ordered early actually match what got detailed?*

### 3.2 Requisitions to purchase orders

**Steps**

1. Send all unlinked material to a requisition.
2. Combine it using **Mult** and **Nest**.
3. Push the requisition through to a purchase order.

!!! warning "Load Material Into Purchase Order is not on the list screen"
    Right-clicking the *Select Requisition/Purchase Order* list gives only generic grid and export options — Select All, Export to Excel. The command that actually converts a requisition lives on the **Requisition** ribbon tab **inside the opened requisition**.

    Participants reliably lose time here. Show them the detail screen, not the list.

!!! warning "A requisition is not an order"
    Material sitting on a requisition that was never converted to a purchase order will never arrive and will never appear in inventory — and nothing in the system flags it. This exact gap was traced during a live session on requisition RQ-001. Build a habit of reviewing the open requisition list at the end of each procurement cycle.

### 3.3 Receiving

**Steps**

1. Receive the purchase order into inventory.
2. Attach heat documents.
3. Record heat numbers against the received material.

Heat traceability is a contractual requirement on most structural projects. Capturing it at the point of receipt is the only realistic option — reconstructing it later from supplier paperwork is a significant undertaking.

---

## Wrap-up checklist

- [ ] PDC job created and final BOM imported with UDAs mapped
- [ ] Sequences, lots, and work packages assigned
- [ ] Route built, applied to material, and TFS Station verified
- [ ] CMB linked to PDC and critical differences reviewed
- [ ] Requisition converted to a purchase order
- [ ] Material received with heat numbers and heat documents attached

## Exercise

!!! info "To be completed"
    Add the afternoon exercise steps and supporting screenshots.

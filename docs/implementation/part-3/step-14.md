# Step 14 — Apply the fabrication route


**Role:** Production Control Coordinator / Shop Planner · **Module:** Production Control

**Why this matters**

A route is the ordered list of stations — Cut/Saw, Layout/Weld, Quality Control, Paint, Erection — that a piece is expected to travel through in the shop. Until a route is assigned to an item, Tekla PowerFab has no station list to track progress against. Piece Tracking will have nothing to show, even after material has been cut.

This normally happens once Purchasing has received material against the job's purchase orders.

**How to do it**

## Part A — Verify the route is configured correctly

1. Go to **Maintenance** ribbon tab **> Production Control > Fabrication Maintenance > Station and Route Setup**.
2. In the *Stations* dialog, click **Route Maintenance** to open *Routes*.
3. Select the route you intend to use and verify three settings before relying on it:
    - **TFS Station** — must be the *first* station in the sequence, usually Cut/Saw.
    - **Route Type** — Assembly, Part, or Assembly & Part.
    - **In Route** list — every station you need, in the correct order.
4. Click **Save (F4)**, then close the *Routes* and *Stations* dialogs.

## Part B — Apply the route to the job items

1. Back in the Production Control job, select the items to be routed.
2. Go to **Production Control** ribbon tab **> Modify Data > Global Edit Selected** for manually highlighted rows, or **Global Edit** for a filter-based selection such as by Finish or Category.
3. Tick the **Route** field checkbox and choose the route from the dropdown.
4. Click **Update**, then **Yes** to confirm.

<!-- SCREENSHOTS — Step 14
     Drop files into docs/assets/images/implementation/ named:
       impl-step14-01.png, impl-step14-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../../assets/images/implementation/impl-step14-01.png)
    <figcaption>Figure 14.1. Caption text.</figcaption>
-->

**You should now have:** every main assembly carrying a defined fabrication route, with a verified TFS Station.

!!! info "Menu change in PowerFab 2026"
    **Station and Route Setup** moved from directly under *Maintenance > Production Control* into a new **Fabrication Maintenance** submenu in Tekla PowerFab 2026. Older reference material points at the previous location — update it accordingly.

!!! danger "Routes must be applied before Step 15 — this cannot be fixed later"
    Confirmed live during a technical enablement session: if the cut list is built and processed before routes are assigned, applying routes afterwards does **not** back-fill completion credit for the Cut/Saw station.

    The Station Summary stays blank despite the cuts having genuinely been processed, and the only remedy is manually adding completed entries piece by piece. This is why Step 14 sits where it does in the sequence.

!!! warning "Verify the TFS Station on the route"
    Routes can default their **TFS Station** to the last station in the sequence rather than the first. On the sample SP route this appeared as *Sample - Erection* instead of *Sample - Cut/Saw*. Material taken from stock is then credited at entirely the wrong point. Check this field before processing anything.

!!! warning "Fixing a route does not apply it"
    Correcting a route's settings in Route Maintenance changes the route. It does not attach the route to anything. Part B — Global Edit — is a separate and mandatory step.

    Opening **Production Status** instead of Fabrication Maintenance is the other common wrong turn here. Production Status is read-only progress reporting.

??? question "Frequently asked questions"
    **My Station Summary is completely empty even though I already cut material via TFS — why?**

    The cut list and TFS process works independently of routing. If the item never had a route assigned via Global Edit, there is no station list for Piece Tracking to display, regardless of how much material has already been cut.

    **I assigned the route after I already processed TFS — why did Cut/Saw not show as complete automatically?**

    The automatic TFS-station credit only fires at the moment of cutting. Assigning a route retroactively does not back-fill that completion. It has to be logged manually using **Add Completed** at Step 17.

    **What does Route Type control?**

    Whether the route applies to assemblies, to individual parts, or to both. Set it to match what is actually being routed.

??? note "Field notes — from the live test run"
    Tekla PowerFab 2026, Trimble Malaysia install.

    - The out-of-the-box **SP** sample route had **TFS Station** set to *Sample - Erection*, the last station, instead of *Sample - Cut/Saw*. Always check TFS Station before relying on a copied or sample route.
    - Global Edit is a separate, mandatory step. On `TRN-001`, items were cut via TFS before Global Edit was ever run, leaving Station Summary completely blank until the route was retroactively assigned.
    - After assigning the route post-cut, Cut/Saw still showed 0 Completed Qty. The completion had to be entered manually via **Add Completed**.

---

Next: [Step 15 — Create a cut list](step-15.md)

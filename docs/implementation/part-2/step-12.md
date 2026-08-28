# Step 12 — Send balance material to requisition and purchasing


**Role:** Material Planner / Purchasing Agent · **Modules:** Production Control, Purchasing

**Why this matters**

Same logic as Step 6: getting material priced and committed via a vendor before it can be received and used in production. This step is also where the practical mechanics of converting a requisition into a real purchase order get exercised for the first time.

**How to do it**

1. From Step 11's **Save Displayed Results & Close**, choose **Requisitions**, select an existing one or **Add** a new one, and click **Save**.
2. Open **Purchasing > Requisitions** tab and confirm material landed correctly, with a full **Linked to PDC** ratio per item.
3. To convert to a real purchase order, open the requisition itself — double-click into the detail screen, do not just select it in the list.
4. On that detail screen, find the **Requisition** ribbon tab and click **Load Material Into Purchase Order**.
5. Pick an existing PO or create a new one, click **OK**, and work through the **Purchasing Import Filters** dialog — skip filtering to include everything, or filter selectively.
6. Confirm. Items transfer to the PO and disappear from the Requisition view.
7. Open **Purchasing > Purchase Orders** tab, open the PO, and confirm items and cost are populated correctly.

<!-- SCREENSHOTS — Step 12
     Drop files into docs/assets/images/implementation/ named:
       impl-step12-01.png, impl-step12-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../../assets/images/implementation/impl-step12-01.png)
    <figcaption>Figure 12.1. Caption text.</figcaption>
-->

**You should now have:** a purchase order covering the beams and connection hardware, with the items cleared from the requisition view.

!!! warning "Load Material Into Purchase Order is not on the list screen"
    Right-clicking on the *Select Requisition/Purchase Order* list gives only generic grid and export options — Select All, Export to Excel, and so on. The actual command lives on a ribbon tab **inside the opened requisition**, not on the list screen.

    This cost real time during the live session. Open the requisition first.

!!! info "Items disappearing from the requisition is expected"
    Once loaded into a PO, the transferred items clear from the Requisition view because they have moved across. The requisition record itself remains for history and reference. This is not an error.

!!! warning "Check Linked to PDC per item"
    Same principle as *Linked to ABM* at Step 6 — do not assume the whole requisition is complete without checking the ratio on each line.

??? question "Frequently asked questions"
    **Where exactly is the option to convert a requisition into a PO?**

    Open the requisition itself, not just select it in the list, then use the **Requisition** ribbon tab and **Load Material Into Purchase Order**.

    **What is the difference between *Linked to PDC* and *Linked to ABM*?**

    Same concept, different source module. ABM means reconciled back to the Advance Bill; PDC means reconciled back to Production Control. Check whichever matches where the combine actually ran.

    **Can I load only some items from a requisition into a PO, not all?**

    Yes. There is a separate **Load Selected Material Into Purchase Order** command, and the Purchasing Import Filters dialog lets you filter which items go across.

    **Does the requisition disappear once everything is loaded into a PO?**

    The transferred items disappear from the Requisition view since they have moved across, but the requisition record itself typically remains for history and reference.

??? note "Field notes — from the live test run"
    Tekla PowerFab 2026, Trimble Malaysia install.

    - Meaningful time was spent hunting for **Load Material Into Purchase Order** in the wrong place — the *Select Requisition/Purchase Order* list's right-click menu, which only offers generic grid and export options. Official documentation confirmed the command is a ribbon-tab action inside the opened Requisition detail screen.
    - Once found, the conversion worked cleanly. Items transferred into an existing, already-named PO — `TRN-001`, apparently auto-created via an earlier Connector submission attempt — correctly populating it with 5 items and £2,148.69 total cost.

---

Next: [Step 13 — Receive the material](step-13.md)

# Step 13 — Receive the material


**Role:** Purchasing Agent / Yard Foreman · **Modules:** Purchasing, Inventory

**Why this matters**

Receiving is the literal gatekeeper before material can be cut on a cut list at Step 15. When a truck arrives, someone has to unload it, check it against the packing slip, and record what actually turned up. It is worth demonstrating on both PowerFab Office and Go, since shop floor staff may use either.

=== "In PowerFab Office"

    1. Open the purchase order — `TRN-001` — in the **Purchasing** module.
    2. Click **Switch to Receive Mode** at the top of the PO detail window.
    3. Select the line item or items.
    4. Enter the **Received** quantity per line. Match the ordered quantity for a clean practice run, or enter a partial quantity to simulate a short shipment.
    5. Optionally complete the **Receiving Fields** — heat number, country of origin, bill of lading — via the left-hand filter tree category.
    6. Click **Save (F4)**.
    7. Repeat per line, or select multiple lines at once.

=== "In PowerFab Go (tablet)"

    1. Sign in to PowerFab Go.
    2. Go to **Inventory > Receive**.
    3. Select the job.
    4. Batch edit, or mark items individually received.
    5. Sync.

<!-- SCREENSHOTS — Step 13
     Drop files into docs/assets/images/implementation/ named:
       impl-step13-01.png, impl-step13-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../../assets/images/implementation/impl-step13-01.png)
    <figcaption>Figure 13.1. Caption text.</figcaption>
-->

**You should now have:** material in inventory, tagged with heat numbers, and eligible for a cut list.

!!! warning "Receive Mode exists only at purchase order level"
    The Requisition screen has a visually similar toggle in the same position, but it reads **Switch to Manual Combine Mode**. Only the purchase order offers Receive Mode.

    The two screens look close enough that it is easy to assume they work interchangeably. They do not.

!!! danger "Unreceived material silently blocks cut lists"
    Material that has not been received cannot go onto a cut list at Step 15 — and Tekla PowerFab does not throw an error when it happens. It simply excludes the rows, which looks like a bug if you are not expecting it.

!!! tip "Attach heat documents at the point of receipt"
    **Check Heat Documents** can find missing certification later, but chasing a supplier for paperwork six weeks after delivery is a different job to asking the driver for it at the gate. Capture it while the delivery is happening.

??? question "Frequently asked questions"
    **Why can I not find a Receive button on my requisition?**

    Because receiving happens at the purchase order level, not the requisition level. Convert to a PO first — Step 12.

    **What happens if only part of an order is received?**

    The Received quantity simply reflects what actually arrived. **Rejected** and **Cancelled** are separate fields for tracking discrepancies such as damaged goods or cancelled lines, so quantities can legitimately differ from what was ordered.

    **Do I need to receive in both PowerFab Office and Go, or is one enough?**

    Functionally, one is enough — both write to the same shared database. Testing both is a trainer exercise to confirm parity between platforms, not a requirement for every real receiving event.

    **What is the practical impact of skipping heat number and country of origin?**

    No functional blocker for most workflows, but it matters for material traceability and certification on structural steel projects. It is a good habit to build with customers in regulated industries.

??? note "Field notes — from the live test run"
    Tekla PowerFab 2026, Trimble Malaysia install.

    - **Switch to Receive Mode** sits at the top left of the open Purchase Order detail screen — visually in the same spot and style as the Requisition's *Switch to Manual Combine Mode* toggle. Easy to assume the two screens work interchangeably since they look so similar, but each toggle is specific to its own module.
    - Receiving completed cleanly for all 5 beam items against PO `TRN-001` once the correct screen was found.

---

Next: [Step 14 — Apply the fabrication route](../part-3/step-14.md)

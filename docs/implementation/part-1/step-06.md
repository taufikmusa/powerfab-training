# Step 6 — Send to requisition and purchasing


**Role:** Material Planner / Purchasing Agent · **Modules:** Advance Bill, Purchasing

**Why this matters**

After combining material into stock-length groups, the requisition is where the material planner sends material out for vendor pricing before committing to a purchase order. This protects against over-committing to one supplier before quotes are compared. The purchase order itself typically comes later, once pricing is back.

**How to do it**

1. Following on from Step 5's **Save Displayed Results & Close**, choose **Requisitions** when prompted.

    ![Combining Run Results with the save prompt open and arrows pointing at the Requisitions button and Save Displayed Results and Close](../../assets/images/implementation/impl-step06-01.png)
    <figcaption>Figure 6.1. The hand-off point from Step 5. The combined stock lengths on screen are what lands in the requisition.</figcaption>

2. In the *Select Requisition* dialog, click **Add**, enter a **Requisition #** — `RQ-001` — and click **Save**.

    ![Select Requisition list with a Requisition Edit window open over it showing the requisition number field](../../assets/images/implementation/impl-step06-02.png)
    <figcaption>Figure 6.2. Creating the requisition. Existing requisitions stay listed behind it.</figcaption>

3. The combined material populates into the new requisition automatically.
4. Open the **Purchasing** module, go to the **Requisitions** tab, and open the requisition just created.

    ![Select Requisition slash Purchase Order window on the Requisitions tab, with an arrow pointing at the Purchasing module button](../../assets/images/implementation/impl-step06-03.png)
    <figcaption>Figure 6.3. Purchasing opens on two tabs — Requisitions and Purchase Orders. Everything up to Step 6 lives on the first.</figcaption>

5. Confirm each line shows the correct profile, grade, quantity, length, base price, and cost.
6. Check **Linked to ABM** at the bottom of the line item detail. It should show a full ratio — 4/4 — confirming every piece is reconciled back to the original Advance Bill line.

    ![Requisition detail screen with an arrow pointing at Linked to ABM reading four of four, and a Switch to Manual Combine Mode toggle at the top left](../../assets/images/implementation/impl-step06-04.png)
    <figcaption>Figure 6.4. Linked to ABM: 4/4 — check this per line, not once per requisition. Note the toggle top-left reads <em>Switch to Manual Combine Mode</em>; the purchase order screen has a lookalike that reads Receive Mode instead (Step 13).</figcaption>

7. Once vendor pricing is confirmed, and only then, open the requisition itself, go to the **Requisition** ribbon tab, and click **Load Material Into Purchase Order**. Pick or create the PO, then **OK** to formally commit.

    ![Requisition ribbon menu open with Load Material Into Purchase Order highlighted and Load Selected Material Into Purchase Order beneath it](../../assets/images/implementation/impl-step06-05.png)
    <figcaption>Figure 6.5. The command lives on this ribbon tab, inside the opened requisition — not on the list screen, where right-clicking offers only Select All and Export to Excel.</figcaption>

    ![Select Purchase Order window with a Purchase Order Edit dialog open, the Job number field arrowed](../../assets/images/implementation/impl-step06-06.png)
    <figcaption>Figure 6.6. Creating the purchase order the material transfers into.</figcaption>

    ![Purchase order detail screen listing the transferred material, with a Switch to Receive Mode toggle at the top left](../../assets/images/implementation/impl-step06-07.png)
    <figcaption>Figure 6.7. The material has moved across. Received, Rejected and Cancelled all read zero until Step 13 — and this is the screen that offers Receive Mode.</figcaption>

    ![Purchase Orders tab listing the new purchase order with its item count and total cost](../../assets/images/implementation/impl-step06-08.png)
    <figcaption>Figure 6.8. The PO now appears on the Purchase Orders tab, carrying its item count and total cost.</figcaption>

**You should now have:** requisition `RQ-001` holding the combined columns, every line fully linked back to the Advance Bill.

!!! warning "Check the Linked to ABM ratio on every line, not just the first"
    A ratio that is not a full match — 2/4 rather than 4/4 — means part of the order is incomplete even though the requisition appears to exist. Nothing flags this.

    The same applies across material types: if a job has both columns and beams, each filter combination run separately needs its own check. Do not assume combining one Reference # covered the others.

!!! danger "Requisitions that never become purchase orders simply disappear"
    Material sitting on an unconverted requisition will never be ordered, never arrive, and never appear in inventory — and nothing prompts you about it.

    It also silently excludes that material from cut lists at Step 15. This exact gap was traced on requisition `RQ-001` during a live session. Review the open requisition list at the end of every procurement cycle.

??? question "Frequently asked questions"
    **What is the actual difference between a requisition and a purchase order?**

    A requisition is an internal request used to shop pricing across vendors. A purchase order is the formal commitment to buy from a specific vendor at a specific price.

    **Can one requisition span multiple jobs?**

    Yes. The Select Requisition/Purchase Order dialog can list items across different job numbers — requisitions are not strictly limited to a single job.

    **What does *Linked to ABM* mean?**

    It shows how many of the requisition's stock pieces are reconciled back to the original Advance Bill line items. A less-than-full ratio means some pieces were not captured in this requisition.

    **Does the Drop % shown in the requisition matter?**

    Yes. It reflects material waste from the combining run. 0% drop, as in a clean training example, means stock lengths were used perfectly. In real projects some drop is normal and is factored into cost.

    **What happens to the requisition once the PO is created?**

    Materials transfer from the requisition to the purchase order and the requisition's line items clear. This is what prevents double-ordering the same material.

??? note "Field notes — from the live test run"
    Tekla PowerFab 2026, Trimble Malaysia install.

    - After fixing the shape and grade issue from Step 5, both column types — the smaller and the larger UC profile — showed **Requisition: X/X** fully linked when checked individually from the Advance Bill material list. Repeat that check for every line item, not just the first, before assuming the whole job is covered.
    - The Requisition screen displayed the combined stock groups exactly as predicted from the Combining Run Results — same quantities, lengths, grade, price, and total cost. That is a quick way to spot-check that nothing was lost in the hand-off between Combine and Requisition.
    - **Drop: 0 mm (0.00%)** showed on the requisition once the correct UC profile and stock lengths were used. Point out to trainees that this is a genuine material-efficiency metric, not a formality.

---

Next: [Step 7 — Complete the connections in Tekla Structures](../part-2/step-07.md)

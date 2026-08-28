# Step 11 — Combine the balance material in Production Control


**Role:** Estimator / Material Planner · **Module:** Production Control

**Why this matters**

Same combining logic as Step 5, but now run against whatever was not already locked into the Advance Bill — the beams, since only the columns were combined earlier. This closes the procurement loop for the rest of the structure, now that final connections and marks exist.

**How to do it**

1. Open the Production Control job, click the **Production Control** ribbon tab, and then **Combine**.
2. In *Select Combining Run*, choose **Mult** — the beams are linear shapes.
3. In *Combining Run Filters*, click the **Main Mark** or **Reference #** row in the Type list, click **Select**, click **`<<`** to clear, Ctrl+click the items to include, click **`>`**, and click **OK**.
4. Click the combine button — **MULT (F4)**.
5. Review *Combining Run Results* and confirm a real **% Combined** and **Cost** for the steel sections.
6. Click **Save Displayed Results & Close**, choose **Requisitions**, add to a new or existing requisition, and save.

<!-- SCREENSHOTS — Step 11
     Drop files into docs/assets/images/implementation/ named:
       impl-step11-01.png, impl-step11-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../../assets/images/implementation/impl-step11-01.png)
    <figcaption>Figure 11.1. Caption text.</figcaption>
-->

**You should now have:** the balance steel combined onto stock lengths and sitting on a requisition, with the hardware correctly left uncombined.

!!! info "Hardware under *Not Combined* is correct, not a failure"
    Bolts, nuts, and washers are not run through stock-length optimisation the way steel sections are — they are counted and ordered as discrete pieces. Seeing `BOLTM`, `NUTM`, and `WASHERM` in the Not Combined branch is expected behaviour.

    Telling this apart from the genuine 0% / $0.00 failure at Step 5 is the point of this step. There is nothing to fix here.

??? question "Frequently asked questions"
    **Why do bolts, nuts, and washers show as Not Combined — is something wrong?**

    No. Hardware is not run through stock-length combining like steel sections are. It is simply counted and ordered as discrete pieces.

    **Can combining beams here reuse the same requisition as the earlier column combine from Step 5?**

    Yes. You can add to the existing requisition number, or keep them separate. Both are valid organisational choices.

    **Does combining here affect the columns already combined back in Step 5?**

    No. That combine is already complete and untouched. This step is purely additive, covering only the previously uncombined material.

??? note "Field notes — from the live test run"
    Tekla PowerFab 2026, Trimble Malaysia install.

    - The beams (UB shapes, grade S27JR — the UC columns carry S275JR; both grades genuinely exist in the SEA database) combined cleanly on the first attempt — 5 stock bars, real per-bar costs, genuine drop percentages, total £2,148.69. That confirmed the SEA database fix from Step 5 held for beam shapes too, not just columns.
    - The *Not Combined* branch in this run legitimately listed `BOLTM`, `NUTM`, and `WASHERM`. It is a good moment to teach the distinction between a genuine combining failure — the UC zero-cost incident at Step 5 — and expected, normal hardware behaviour.

---

Next: [Step 12 — Send balance material to requisition and purchasing](step-12.md)

# Step 3 — Model in Tekla Structures, assign preliminary marks, and export


**Role:** Steel Detailer / BIM Modeller · **Software:** Tekla Structures

**Why this matters**

Connections are usually not finalised at this stage, but purchasing needs to start ordering long-lead material now rather than in three weeks. Preliminary marks let Tekla PowerFab recognise and group material before final assembly marks exist, so the fabricator can buy steel early. Get this step wrong and everything downstream — Advance Bill, Requisition, Purchasing — either fails to import or imports unreliable data.

**How to do it**

=== "Path A — Tekla PowerFab Connector"

    Recommended where available. Introduced in the 2025 release, so verify it on each customer install.

    1. Link the model directly to the fabricator's Tekla PowerFab project.
    2. The Connector validates against the real material catalogue.
    3. Submit a preliminary list for advance purchasing.

=== "Path B — Manual IFC export"

    Still fully supported, and the safer fallback.

    1. Build the model without finalised connections — main members only.
    2. Select the parts to mark, go to the **Drawings & reports** tab, click **Numbering settings**, and choose **Save preliminary numbers**. Every part to be exported needs one — this is non-negotiable.

        ![Numbering settings menu open in Tekla Structures with Save preliminary numbers highlighted and its tooltip showing](../../assets/images/implementation/impl-step03-01.png)
        <figcaption>Figure 3.1. Save preliminary numbers, on the Drawings &amp; reports tab. The tooltip states it overwrites any previously saved preliminary numbers.</figcaption>

    3. Confirm the mark landed: it appears as **Preliminary mark** on the part's **Parameters** tab, among the user-defined attributes.

        ![Column properties dialog with the Parameters tab open and the Preliminary mark field showing C2](../../assets/images/implementation/impl-step03-02.png)
        <figcaption>Figure 3.2. The saved mark on a column — this is the `PRELIM_MARK` UDA that Advance Bill reads on import.</figcaption>

    4. Go to **File > Export > IFC** and export using the **Steel fabrication view** or **2x3 EM11** format.

        ![Export IFC dialog with Export type set to Steel fabrication view and the Tekla PowerFab property set selected](../../assets/images/implementation/impl-step03-03.png)
        <figcaption>Figure 3.3. Export type is the field that matters — Steel fabrication view, not Coordination view. Property sets should read Tekla PowerFab.</figcaption>

    5. Later, when importing to Advance Bill, map at least `PRELIM_MARK` to **Reference Number**.

**You should now have:** an IFC file containing main members only, with a preliminary mark on every part.

!!! warning "Two habits to build here"
    **Forgetting `PRELIM_MARK` entirely.** The IFC still imports and nothing appears to fail, but Tekla PowerFab cannot reconcile the list against the real production BOM later.

    **Using the Coordination view out of habit** instead of the Steel fabrication view. It still works — it simply carries less information.

??? question "Frequently asked questions"
    **Do we need a separate Tekla Structures licence?**

    No. A Tekla PowerFab subscription includes one licence of Tekla Structures.

    **Can we re-export after connections are finalised?**

    Yes — that is Steps 9 and 10 later in this workflow. IFC import supports revision detection.

    **What if PowerFab shows an unrecognised shape or grade on import?**

    The *Translate Shapes/Grades* dialog opens. Map the entry carefully — see Step 5's field notes for what happens when this goes wrong.

    **Does preliminary marking affect final assembly marking later?**

    No. Preliminary marks are throwaway identifiers for early procurement only.

??? note "Field notes — from the live test run"
    Tekla PowerFab 2026, Trimble Malaysia install.

    - For experienced Tekla Structures users this step moves quickly. The only new habit is filling in the preliminary mark on every part before exporting.
    - A six-part model — two columns and four beams — exported and imported cleanly: **453 IFC instances, 0 errors, 0 warnings**, once every part had a preliminary mark assigned.
    - A shape or grade mismatch on import will not always throw a visible warning. A British profile can be silently mapped to the wrong US shape. See Step 5.

---

Next: [Step 4 — Import the IFC into the Advance Bill](step-04.md)

# Step 8 — Create drawings and export NC files


**Role:** Steel Detailer · **Software:** Tekla Structures

**Why this matters**

A welder at a workbench cannot use a 3D model — they need a 2D drawing. A saw or drill line needs machine-readable instructions, not geometry. This step packages both so they can be exported together in Step 9.

**How to do it**

1. Create assembly drawings and single part drawings for the finalised model, using the standard Tekla Structures drawing workflow.
2. Print the drawings first: right-click in **Document Manager** and choose **Print Drawings** — assembly drawings first, then single parts.
3. If the model has changed since the drawings were created, run **Update Drawings** before proceeding.
4. Go to **File > Export > Tekla PowerFab** settings, confirm **Generate CNC files** is ticked, and click **Save** on that settings panel.

<!-- SCREENSHOTS — Step 8
     Drop files into docs/assets/images/implementation/ named:
       impl-step08-01.png, impl-step08-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../../assets/images/implementation/impl-step08-01.png)
    <figcaption>Figure 8.1. Caption text.</figcaption>
-->

**You should now have:** assembly drawings, single-part drawings, printed PDFs, and the CNC setting saved ready for export.

!!! danger "Ticked is not saved"
    This is a real, repeatable trap. The **Generate CNC files** checkbox can appear correctly set, but if **Save** is not clicked on that settings panel, the next export silently produces zero NC files with no upfront warning.

    Tick it, save it, then export.

!!! warning "Print the drawings before exporting"
    In the classic export plugin path, Tekla PowerFab sources the PDF files from wherever they were printed or saved — not directly from the live drawing inside Tekla Structures. Drawings that were never printed produce a *No files loaded* warning at Step 10.

    Two settings govern this and they are separate: the **Include drawing files** toggle in the export settings, and the **Drawing Default Directory** path matching where the files were actually printed.

!!! warning "Create both drawing types"
    It is easy to produce assembly drawings, move on, and forget the single-part drawings — or the reverse. Both are needed.

??? question "Frequently asked questions"
    **Do drawings need to be 100% final before this step?**

    Ideally yes, but they can be revised later. Steps 9 and 10 support revision detection on re-import.

    **What is the actual difference between an assembly drawing and a single part drawing?**

    An assembly drawing shows the whole built-up piece with all its parts and welds. A single part drawing is for an individual unattached plate or member that needs its own shop drawing for cutting and drilling.

    **Why print drawings before exporting, instead of exporting directly from the live drawing?**

    In the classic export plugin path, Tekla PowerFab sources the PDF files from wherever they were printed or saved — not from the live drawing inside Structures.

??? note "Field notes — from the live test run"
    Tekla PowerFab 2026, Trimble Malaysia install.

    - Documented incident from the original enablement session: an export returned *no CNC files* with zero NC data, traced back to the **Generate CNC files** checkbox showing ticked but never actually saved on the settings panel. Re-checking, saving, then re-exporting fixed it.
    - A second, related incident on this practice run: a later export reported *No files loaded for 6 drawings* even though drawings had been printed. Most likely cause is the separate **Include drawing files** toggle — distinct from CNC generation — being unchecked, or the **Drawing Default Directory** path not matching where the files were actually printed. Confirmed as an open item to fix in a follow-up revision import.

---

Next: [Step 9 — Export to PowerFab as `.pfxt`](step-09.md)

# Step 10 — Import the `.pfxt` into Production Control


**Role:** Production Control / Steel Detailer · **Module:** Production Control

**Why this matters**

This is the formal handover from engineering to production. The issued-for-fabrication package becomes a real, trackable job in the shop's system, converting drawings, NC data, and the BOM into something the shop floor can actually work from.

**How to do it**

1. Go to **File > Import**, expand **Production Control**, and select the file type matching `.pfxt`. Browse to the file, click **Open**, then **Import**.
2. If no Production Control job with this job number exists yet, confirm **Yes** to auto-create and link one. This ties it back to the Project Management job from Step 1.
3. In **Import Field Map**, select the `PRELIM_MARK` row — or the equivalent reference — set **Tekla PowerFab Field: Reference #**, and click **Set Field Mapping**.
4. Resolve any **Translate Shapes/Grades** prompts carefully. Confirm the New Shape/Grade genuinely matches the Old Shape/Grade before clicking **Set Shape/Grade**, rather than accepting whatever default appears.
5. Review the **Change Summary** dialog. Scroll through the full list to confirm it is consistently *Add*, which is expected on a first import. Anything showing *Delete* or *Modify* unexpectedly is worth investigating before clicking **Continue**.
6. Read the full import log, not just the final Successful/Unsuccessful count.
7. Confirm the job now appears under **Production Control > Select Production Control Job**.

<!-- SCREENSHOTS — Step 10
     Drop files into docs/assets/images/implementation/ named:
       impl-step10-01.png, impl-step10-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../../assets/images/implementation/impl-step10-01.png)
    <figcaption>Figure 10.1. Caption text.</figcaption>
-->

**You should now have:** a live production job carrying drawings, machine files, and the final material list.

!!! danger "Successful does not mean clean — read the whole log"
    Real issues sit inside imports that technically succeeded. One live import reported **Successful: 79 / Unsuccessful: 0** while the log carried three genuine failures: missing drawing PDFs, an invalid grade in five NC files, and four NC files silently overwritten.

    Warnings and failure are not the same thing in this dialog. Read the log every time.

!!! warning "Set Field Mapping — again"
    The same trap as Step 4's Advance Bill import. Selecting a value in the dropdown does not commit it; **Set Field Mapping** has to be clicked.

!!! info "Not every shape or grade prompt is the UC/WT incident repeating"
    If the New Shape/Grade genuinely matches the Old one, the prompt is registering a combination for the first time, not silently substituting something wrong. Read it, then decide — do not reflexively treat every prompt as a problem, and do not reflexively click through either.

??? question "Frequently asked questions"
    **Why are there more part marks now than in my original Advance Bill — C1 to C6 instead of just C1 to C2?**

    Step 7's added connections create new parts — clips, plates, bolts — that pick up additional marks in the same numbering series. This is expected once detailing is more complete.

    **What does *No files loaded for X drawings* mean if the import still reports Successful?**

    The drawing records still get created, but the underlying PDF content did not attach. This needs a separate fix and will not block other progress, but those specific drawings cannot be opened until it is resolved.

    **What does an *Invalid grade* error inside a specific NC1 file mean?**

    The grade value encoded inside that one CNC file is not accepted by PowerFab's reader, even if the same grade works fine elsewhere in the same import. It usually points to a malformed Material/Grade property on that specific part in Tekla Structures.

    **Why would two very similar part marks — M1 and m1 — cause one to vanish?**

    Windows file systems are case-insensitive. Tekla Structures treats `M1` and `m1` as different marks, but writes both as `.nc1` files with the same filename on disk. The second write overwrites the first before Tekla PowerFab ever tries to read it.

??? note "Field notes — three failures inside one successful import"
    Tekla PowerFab 2026, Trimble Malaysia install.

    A single import log surfaced three separate genuine issues at once:

    1. *No files loaded for 6 drawings: C1–C6* — the drawing PDFs were missing.
    2. *Error reading F1–F5.nc1: Invalid grade (S275)* on five connection-plate NC files.
    3. *No CNC files loaded for m1–m4* — despite those exact files, as `M1–M4`, appearing successfully read earlier in the same log.

    The third was diagnosed with confidence as a Windows filename case-collision, created back at Step 7.

    Despite all three warnings, the import completed successfully — **Successful: 79, Unsuccessful: 0** — and the Production Control job was created correctly. That is proof that *warnings* and *failure* are not the same thing here.

    **Fix paths identified.** Drawings: recheck the *Include drawing files* export setting and the Drawing Default Directory match. NC grade error: check the Material/Grade property directly on the affected parts in Structures. Case-collision: rename one of the colliding mark series in Structures' numbering setup so they no longer collide once case is stripped.

---

Next: [Step 11 — Combine the balance material in Production Control](step-11.md)

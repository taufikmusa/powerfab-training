# Step 9 — Export to PowerFab as `.pfxt`


**Role:** Steel Detailer · **Software:** Tekla Structures

**Why this matters**

This step packages drawings, NC files, and BOM data into the official hand-off to the production team — the moment a model is genuinely *issued for fabrication*. One transfer, rather than separate files that have to be reconciled by hand.

**How to do it**

=== "Path A — Tekla PowerFab Connector"

    Newer and cloud-linked. The recommended path when properly linked end to end.

    1. Open **Submit to Tekla PowerFab**.
    2. Set **Project** — it must already be linked, not *None*.
    3. Choose **Submittal type: Fabrication**.
    4. Confirm **Selection** — *All objects* or *Selected objects*.
    5. Click **Validate Tekla PowerFab submittal**.
    6. If validation is clean, **Export and submit**.

=== "Path B — Classic manual export"

    Fully reliable, and the safer fallback if Connector sync does not pull through.

    1. Go to **File > Export > Tekla PowerFab**.
    2. Set **Select from: Drawing list**.
    3. Choose the bolts and parts inclusion options.
    4. Confirm **Generate CNC files** is ticked.
    5. Set the file type to `.pfxt`.
    6. Click **Export** and save the file somewhere you can find it again.

<!-- SCREENSHOTS — Step 9
     Drop files into docs/assets/images/implementation/ named:
       impl-step09-01.png, impl-step09-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../../assets/images/implementation/impl-step09-01.png)
    <figcaption>Figure 9.1. Caption text.</figcaption>
-->

**You should now have:** a single `.pfxt` package containing the complete detailed job, or a submitted Connector package confirmed as received on the PowerFab side.

!!! danger "Uploaded is not the same as received"
    A Connector submission showing *Uploaded* with a green checkmark means the package reached the server. It does not mean a Production Control job now exists in Tekla PowerFab — someone still has to sync or import it on the PowerFab side.

    Always verify on the receiving end before treating a submission as complete.

!!! warning "Do not keep clicking submit"
    Each click can create a new numbered package — `TS1000_1`, `TS1000_2` — rather than retrying the same one. That produces confusion about which package is real, and it does not fix the underlying problem.

    Check whether Tekla Structures and the PowerFab desktop are signed into the **same Trimble Identity / Trimble Connect account**. A mismatch causes the sync to correctly report *nothing to sync* — not because anything is broken, but because it is looking in the wrong place.

??? question "Frequently asked questions"
    **Which path should I use — Connector or classic manual export?**

    The Connector is the newer recommended path when properly linked end to end. The classic manual `.pfxt` export remains fully reliable and is the safer fallback if Connector sync does not pull through.

    **What does *Fabricator is not selected* mean on the Connector Validate screen?**

    It means the submittal is not routed to a specific fabricator profile. It does not necessarily block the submission, but it should be set up properly before relying on this path for a real customer.

    **Can I just keep clicking submit until it works?**

    No. Repeated submissions create new numbered packages each time without fixing an underlying sync or account issue. Diagnose the actual cause first.

??? note "Field notes — from the live test run"
    Tekla PowerFab 2026, Trimble Malaysia install.

    - A Connector submission showed *Uploaded* with a green checkmark in Submittal History on the Structures side — but PowerFab's own **Sync Submittals** repeatedly reported *No remaining projects/estimates/production control jobs to sync*. The data never reached this PowerFab install despite a successful-looking upload.
    - Rather than chase the cloud-sync and account issue mid-session, the session switched to the classic **File > Export > Tekla PowerFab** path, which worked reliably — the same approach already proven for the Advance Bill import at Step 4.
    - Takeaway for training: *Uploaded* is not *Received*. Always verify on the receiving end — does the Production Control job actually exist? — before treating a submission as complete.

---

Next: [Step 10 — Import the `.pfxt` into Production Control](step-10.md)

# Part 1 — Steps 1 to 10

Part 1 establishes the project, secures the long-lead material before detailing is complete, and hands the finished model over to Production Control.

---

## Step 1 — Create a Project Management job

**Role:** Project Manager · **Module:** Project Management

**Why this matters**

Every structure needs a single container in the management system before anything else can attach to it. The Project Management job is what RFIs, transmittals, drawing logs, schedules, and costs all hang from. Without it, that information has nowhere to live and ends up scattered across email.

**How to do it**

1. Go to **Project Management > Project Management**.

    ![Tekla PowerFab start screen with the Project Management module being opened](../assets/images/implementation/impl-step01-01.png)
    <figcaption>Figure 1.1. Opening the Project Management module.</figcaption>

2. Click **Add (F1)** at the bottom left.

    ![Project Management job list with the Add button at the bottom left](../assets/images/implementation/impl-step01-02.png)
    <figcaption>Figure 1.2. The job list — Add (F1) sits at the bottom left of the window.</figcaption>

3. Enter a Job Number — use `TRN-001` for this exercise.
4. Enter a Job Name, such as *Training Facility*.
5. Complete the customer name and job location.
6. Click **Save**.

    ![New job entry window with Job Number and Job Name fields completed](../assets/images/implementation/impl-step01-03.png)
    <figcaption>Figure 1.3. Job details — Job Number and Job Name are the two fields that matter most.</figcaption>

**You should now have:** an empty PRJ job that everything else in this exercise will link back to.

!!! warning "Do not start with the material import"
    The instinct is to jump straight to importing steel. Skipping this step means the company has no way to track RFIs, transmittals, or change orders against a job number — and retrofitting a project shell around work already in progress is significantly harder than creating it first.

---

## Step 2 — Create a project schedule

**Role:** Project Manager / Production Manager · **Module:** Project Management

**Why this matters**

Steel projects run on hard dates: drawings due, material ordered, fabrication started, steel on site. The schedule is what allows the system to warn you that material is arriving too late to hit the fabrication window — before it becomes a problem rather than after.

**How to do it**

1. Open job `TRN-001`.
2. Click **Schedule**, or open the **Project Schedules** tab.
3. Click **Add Task** and create the major milestones: Detailing, Material Ordering, Fabrication, Erection.
4. Assign start and end dates to each task.
5. Save the schedule.

<!-- SCREENSHOTS — Step 2
     Drop files into docs/assets/images/implementation/ named:
       impl-step02-01.png, impl-step02-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../assets/images/implementation/impl-step02-01.png)
    <figcaption>Figure 2.1. Caption text.</figcaption>
-->

**You should now have:** a baseline programme the rest of the project can be measured against.

!!! warning "Three things that catch people out"
    **The edit mode times out after 180 seconds.** Save before you lose the work.

    **A mistyped year will not be questioned.** One wrong digit turns a four-month programme into a four-year one and the Gantt chart displays it without complaint. Verify each date after entry.

    **Clicking Apply Template twice duplicates every task**, silently. If the task list looks twice as long as expected, this is why.

---

## Step 3 — Model without connections and export IFC

**Role:** Steel Detailer · **Software:** Tekla Structures

**Why this matters**

Mill lead times run into weeks or months. Waiting for every base plate, shear tab, and bolt to be designed before ordering main steel puts the entire mill lead time on the critical path. A deliberately simple model carries enough information to order the main members now, and the detail can follow.

**How to do it**

1. Open Tekla Structures and create a new model.
2. Insert the main structural members — columns and beams — from the engineering drawings.
3. Deliberately leave out base plates, shear tabs, and bolts.
4. Go to the **Drawings & Reports** tab and run **Perform Numbering**, configured to produce preliminary marks such as `C1` and `C2`.
5. Go to **File > Export > IFC**.
6. Enable **Base quantities** and export.

<!-- SCREENSHOTS — Step 3
     Drop files into docs/assets/images/implementation/ named:
       impl-step03-01.png, impl-step03-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../assets/images/implementation/impl-step03-01.png)
    <figcaption>Figure 3.1. Caption text.</figcaption>
-->

**You should now have:** an IFC file containing main members only, with preliminary marks assigned.

---

## Step 4 — Import the IFC into the Advance Bill

**Role:** Estimator / Purchasing Agent · **Module:** Advance Bill

**Why this matters**

The Advance Bill is the staging area for material bought ahead of detailing. Importing the skeleton model here gives purchasing something concrete to work from weeks earlier than would otherwise be possible.

**How to do it**

1. Go to **Maintenance > Advance Bill**.
2. Add a new Advance Bill job — `AB-TRN-001` — and save.
3. With the job open, click **File > Import > IFC**.
4. Browse to the IFC file exported in Step 3.
5. Work through the **Translate Shapes/Grades** window, mapping source profiles and grades to system equivalents.
6. Confirm and complete the import.

<!-- SCREENSHOTS — Step 4
     Drop files into docs/assets/images/implementation/ named:
       impl-step04-01.png, impl-step04-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../assets/images/implementation/impl-step04-01.png)
    <figcaption>Figure 4.1. Caption text.</figcaption>
-->

**You should now have:** main members listed in the Advance Bill, ready to combine.

!!! danger "Read the translation window — every single time"
    Tekla PowerFab silently reapplies the last saved shape and grade mapping. In a documented live incident, British **UC** and **UB** profiles were converted to American **WT** shapes at **A36** grade because of a mapping saved weeks earlier.

    Nothing failed. No warning appeared. The problem only became visible days later when a Combining run returned **0% combined and $0.00**, because the substituted profiles did not exist in the pricing database. Resolution required restoring the SEA regional database with the correct pre-loaded shapes and engineering properties.

    Treat this window as a checkpoint, not a dialogue box to click through.

---

## Step 5 — Partially combine the advance bill material

**Role:** Purchasing Agent · **Module:** Advance Bill

**Why this matters**

Steel is sold in long lengths. A column may be a fraction of one. Combining is the system working out how to cut the fewest raw lengths to produce the required pieces — the difference between buying efficiently and buying twice as much steel as the job needs.

**How to do it**

1. In the Advance Bill list, select the rows containing columns. Hold **CTRL** for multiple selection.
2. Go to **Advance Bill > Combine**.
3. Click **Mult (F4)**.
4. Review the results — the window shows exactly how the columns nest into available raw lengths.
5. Click **Save Displayed Results & Close**.

<!-- SCREENSHOTS — Step 5
     Drop files into docs/assets/images/implementation/ named:
       impl-step05-01.png, impl-step05-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../assets/images/implementation/impl-step05-01.png)
    <figcaption>Figure 5.1. Caption text.</figcaption>
-->

**You should now have:** columns showing a **C** status, meaning they are solved and ready to purchase.

---

## Step 6 — Send to requisition and raise a purchase order

**Role:** Purchasing Agent · **Modules:** Advance Bill, Purchasing

**Why this matters**

Knowing what to buy and actually buying it are two separate events. A requisition is the internal request; a purchase order is the commitment to a supplier. The system deliberately separates them so purchasing retains control over what gets committed and when.

**How to do it**

1. In the Advance Bill, go to **Advance Bill > Send To Requisition**.
2. Select **Combined Materials Only** so only the optimised columns are requested.
3. Click **OK**, then choose **Requisitions**.
4. Click **Add (F1)**, name the requisition `REQ-TRN-001`, and save.
5. Highlight it and click **OK (F5)**.
6. Open the **Purchasing** module, open the requisition, and use **Purchase Order** to issue it to a vendor.

<!-- SCREENSHOTS — Step 6
     Drop files into docs/assets/images/implementation/ named:
       impl-step06-01.png, impl-step06-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../assets/images/implementation/impl-step06-01.png)
    <figcaption>Figure 6.1. Caption text.</figcaption>
-->

**You should now have:** an issued purchase order against the main members.

!!! warning "Requisitions that never become purchase orders simply disappear"
    Material sitting on an unconverted requisition will never be ordered, never arrive, and never appear in inventory — and nothing prompts you about it. This exact gap was traced on requisition `RQ-001` during a live session. Review the open requisition list at the end of every procurement cycle.

---

## Step 7 — Complete the connections in Tekla Structures

**Role:** Steel Detailer · **Software:** Tekla Structures

**Why this matters**

While the mill produces the main steel, the detailer has a window to finish the connection design. This is deliberate parallel working: two long-duration activities running at the same time instead of one after the other.

**How to do it**

1. Reopen the Tekla Structures model.
2. Open the **Applications & Components** catalog.
3. Select the required connection types — End Plate, Shear Tab, Base Plate.
4. Apply connections at beam-to-column joints and at column bases.
5. Run a clash check and resolve any conflicts, particularly bolt clashes.

<!-- SCREENSHOTS — Step 7
     Drop files into docs/assets/images/implementation/ named:
       impl-step07-01.png, impl-step07-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../assets/images/implementation/impl-step07-01.png)
    <figcaption>Figure 7.1. Caption text.</figcaption>
-->

**You should now have:** a fully detailed model ready for drawing production.

---

## Step 8 — Create drawings and export NC files

**Role:** Steel Detailer · **Software:** Tekla Structures

**Why this matters**

A welder at a workbench cannot use a 3D model. They need a 2D drawing. Similarly, a saw or drill line needs machine-readable instructions, not geometry. This step produces both.

**How to do it**

1. Run **Perform Numbering** again to finalise all part numbers.
2. Select the steel in the model.
3. Right-click and choose **Create Fabrication Drawing > Assembly Drawing**.
4. Repeat for **Single-Part Drawings**.
5. Go to **File > Export > NC Files**.
6. Select the `.nc1` format and click **Create**.

<!-- SCREENSHOTS — Step 8
     Drop files into docs/assets/images/implementation/ named:
       impl-step08-01.png, impl-step08-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../assets/images/implementation/impl-step08-01.png)
    <figcaption>Figure 8.1. Caption text.</figcaption>
-->

**You should now have:** assembly drawings, single-part drawings, and a set of NC files.

!!! danger "Mark case collisions overwrite NC files silently"
    Windows filenames are not case-sensitive. Marks `M1` and `m1` resolve to the same filename, so one NC file overwrites the other with no error and no warning. The shop then cuts one part twice and never cuts the other.

    Enforce consistent mark case in the numbering settings before exporting.

!!! warning "Invalid grade errors block NC export"
    NC files fail with an *Invalid grade* message when a grade — `S275` in a documented case — is not present in the profile database. Add the grade to the database and re-export rather than working around it.

---

## Step 9 — Export to PowerFab as `.pfxt`

**Role:** Steel Detailer · **Software:** Tekla Structures

**Why this matters**

The model is now complete. The `.pfxt` package is what carries the final material list, drawings, and NC files back to the fabrication management system in one transfer, rather than as separate files that have to be reconciled manually.

**How to do it**

1. Open the **Applications & Components** pane.
2. Search for the Tekla PowerFab export tool and open it.
3. Select **Production Control** as the destination — not Advance Bill, which was used in Step 4.
4. Tick the checkboxes for **Drawings** and **NC Files**.
5. Export. The tool produces a `.pfxt` file.

<!-- SCREENSHOTS — Step 9
     Drop files into docs/assets/images/implementation/ named:
       impl-step09-01.png, impl-step09-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../assets/images/implementation/impl-step09-01.png)
    <figcaption>Figure 9.1. Caption text.</figcaption>
-->

**You should now have:** a single `.pfxt` package containing the complete detailed job.

!!! warning "The Connector can report success and still fail"
    The Tekla PowerFab Connector has been observed displaying an *Uploaded* status while failing to sync into Production Control Submittals, caused by an unresolved Fabricator configuration.

    If the submittal does not appear on the PowerFab side, do not assume the export failed — check the Fabricator configuration, and fall back to a manual `.pfxt` export to keep the job moving.

---

## Step 10 — Import the `.pfxt` into Production Control

**Role:** Production Manager / Shop Foreman · **Module:** Production Control

**Why this matters**

This is the formal handover from engineering to production. **Production Control** is the command centre for the shop floor, and this import is what puts the job in front of the people who will actually build it.

**How to do it**

1. Go to **File > Import > Tekla PowerFab Plugin**.
2. Select the `.pfxt` file created in Step 9.
3. When prompted, select the **Production Control** module.
4. Link the import to the master Project Management job `TRN-001` from Step 1.
5. Click **Import** and let it process drawings, NC files, and the final material list.

<!-- SCREENSHOTS — Step 10
     Drop files into docs/assets/images/implementation/ named:
       impl-step10-01.png, impl-step10-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../assets/images/implementation/impl-step10-01.png)
    <figcaption>Figure 10.1. Caption text.</figcaption>
-->

**You should now have:** a live production job with drawings and machine files attached.

!!! tip "Verify the drawing count immediately"
    Drawings occasionally fail to attach during export — `C1` through `C6` drawing PDFs failing to attach has been seen in practice. Comparing the expected drawing count against what actually landed takes thirty seconds now and saves a great deal of confusion once fabrication has started.

---

Continue to [Part 2 — Steps 11 to 18](part-2.md).

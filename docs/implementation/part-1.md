# Part 1 — Steps 1 thru 10

Part 1 makes the project, buys the main steel early and finishes the 3D model.

---

## Step 1: Make a Project Management job

**Role:** Project Manager

**Why**

Each structure needs one central container in the management system. The **Project Management** job holds the drawings, the RFIs, the schedule and the costs for one building.

**Steps**

1. Go to **Project Management > Project Management**.
2. Click **Add (F1)** at the bottom left.
3. Enter a Job Number, for example TRN-001.
4. Enter a Job Name, for example Training Facility.
5. Enter the customer name and the job location.
6. Click **Save**.

!!! warning
    Do not import material first. Without a Project Management job, the company cannot track the RFIs, the transmittals and the change orders against one job number.

---

## Step 2: Make a project schedule

**Role:** Project Manager and Production Manager

**Why**

A steel project has hard dates. The schedule gives a warning when the material arrives too late for the fabrication start.

**Steps**

1. Open the job TRN-001.
2. Click **Schedule** or open the **Project Schedules** tab.
3. Click **Add Task** and make the milestones: Detailing, Material Ordering, Fabrication and Erection.
4. Give each task a start date and an end date.
5. Save the schedule.

!!! warning
    The edit mode has a time limit of 180 seconds. Examine each date after you type it. One wrong year gives a project duration of many years.

---

## Step 3: Model in Tekla Structures and export an IFC file

**Role:** Steel Detailer

**Why**

Steel from the mill takes weeks or months. The company cannot wait for the full connection design. A simple model gives enough data to buy the main members early.

**Steps**

1. Open Tekla Structures and make a new model.
2. Insert the main members: the columns and the beams.
3. Do not add the base plates, the shear tabs or the bolts.
4. Go to the **Drawings & Reports** tab and click **Perform Numbering**.
5. Make sure that the settings give preliminary marks, for example C1 and C2.
6. Go to **File > Export > IFC**.
7. Turn on **Base quantities** and click Export.

---

## Step 4: Import the IFC file into the advance bill

**Role:** Estimator and Purchasing Agent

**Why**

The advance bill is the holding area for the material that the company buys early.

**Steps**

1. Go to **Maintenance > Advance Bill**.
2. Add a new advance bill job, for example AB-TRN-001, and save it.
3. Click **File > Import > IFC**.
4. Select the IFC file from Tekla Structures.
5. Map the shapes and the grades in the **Translate Shapes/Grades** window.
6. Click OK and continue.

!!! danger
    The software keeps the last shape map and grade map that you saved. A wrong map changes a UC profile to a WT profile and a British grade to a US grade. There is no error message. The combine run then gives 0% combined and no cost.

---

## Step 5: Combine part of the advance bill material

**Role:** Purchasing Agent

**Why**

The mill sells long lengths. A column is shorter than one raw length. The combine function is a cutting plan. It puts more than one column into one raw length.

**Steps**

1. Select the rows with the columns. Hold CTRL for more than one row.
2. Go to **Advance Bill > Combine**.
3. Click **Mult (F4)**.
4. Examine the results.
5. Click **Save Displayed Results & Close**.

!!! tip
    A solved item shows the status "C". A "C" status means that the item is ready to buy.

---

## Step 6: Send the material to a requisition and a purchase order

**Role:** Purchasing Agent

**Why**

A requisition is the internal request. A purchase order is the external order to the supplier.

**Steps**

1. Go to **Advance Bill > Send To Requisition**.
2. Select **Combined Materials Only**.
3. Click OK and select **Requisitions**.
4. Click **Add (F1)**, name the requisition REQ-TRN-001 and save it.
5. Select the requisition and click **OK (F5)**.
6. Open the **Purchasing** module.
7. Open the requisition and click **Purchase Order**.

!!! warning
    A requisition alone does not buy the material. Turn each requisition into a purchase order. Material on a requisition without a purchase order never arrives in inventory.

---

## Step 7: Complete the connections in Tekla Structures

**Role:** Steel Detailer

**Why**

The purchasing department waits for the main steel. The detailer uses this time to add the connection parts.

**Steps**

1. Open the Tekla Structures model again.
2. Open the **Applications & Components** catalog.
3. Find the connection types: End Plate, Shear Tab and Base Plate.
4. Apply the connections at the beam-to-column joints and at the column bases.
5. Examine the model for clashes, for example two bolts in the same position.

---

## Step 8: Make the drawings and export the NC files

**Role:** Steel Detailer

**Why**

The welder cannot read a 3D model at the workbench. The welder needs a 2D drawing. The saw and the drill line need an NC file.

**Steps**

1. Click **Perform Numbering** again to make the final part numbers.
2. Select the steel in the model.
3. Right-click and select **Create Fabrication Drawing > Assembly Drawing**.
4. Do the same task for the single-part drawings.
5. Go to **File > Export > NC Files**.
6. Select the `.nc1` format and click **Create**.

!!! danger
    Windows does not see a difference between the mark M1 and the mark m1. Two marks with the same letters overwrite each other in the NC folder. Make sure that the mark case is the same for all parts.

!!! warning
    An NC file fails with an "Invalid grade" message when the grade is not in the profile database. Add the grade before you export again.

---

## Step 9: Export a PFXT file to Tekla PowerFab

**Role:** Steel Detailer

**Why**

The model is now complete. The PFXT file sends the final material list, the drawings and the NC files to the management team in one package.

**Steps**

1. Open the **Applications & Components** pane.
2. Find the Tekla PowerFab export tool.
3. Double-click the tool.
4. Select **Production Control**. Do not select Advance Bill this time.
5. Turn on the checkboxes for **Drawings** and **NC Files**.
6. Click Export. The tool makes a `.pfxt` file.

!!! warning
    The Tekla PowerFab Connector can show the status "Uploaded" and still fail to sync. The cause is an unresolved fabricator configuration. Use the manual `.pfxt` export when the sync fails.

---

## Step 10: Import the PFXT file into Production Control

**Role:** Production Manager and Shop Foreman

**Why**

**Production Control** is the command centre for the shop floor. This import gives the shop the drawings, the NC files and the final material list.

**Steps**

1. Go to **File > Import > Tekla PowerFab Plugin**.
2. Select the `.pfxt` file.
3. Select the **Production Control** module.
4. Link the import to the Project Management job TRN-001 from Step 1.
5. Click Import.

!!! tip
    Examine the drawing count after the import. A drawing that does not attach is easier to find now than two weeks later.

Continue with [Part 2](part-2.md).

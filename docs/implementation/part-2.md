# Part 2 — Steps 11 thru 18

Part 2 buys the balance material and moves the steel through the shop to the truck.

Complete [Part 1](part-1.md) before you start Part 2.

---

## Step 11: Combine the balance material in Production Control

**Role:** Purchasing Agent and Production Manager

**Why**

The PFXT import brought in the new detail parts: the shear tabs, the base plates, the connection angles and the bolts. Nobody bought these parts in Step 6.

**Steps**

1. Open the job in the **Production Control** module.
2. Go to **Production Control > Combine**.
3. Set the filter to the items that are **Not Linked**.
4. Click **Mult (F4)**.
5. Examine how the plates nest into the standard stock sheets.
6. Click **Save Displayed Results & Close**.

---

## Step 12: Send the balance material to a requisition and a purchase order

**Role:** Purchasing Agent

**Why**

This step is the same as Step 6. The material is different. Step 6 bought the main members. This step buys the plates, the angles and the bolts.

**Steps**

1. Go to **Production Control > Send to Requisition**.
2. Select **Combined Materials Only**.
3. Make a new requisition, for example REQ-Plates-Bolts.
4. Open the **Purchasing** module.
5. Find the requisition and make a purchase order.

---

## Step 13: Receive the material

**Role:** Yard Foreman and Receiving Clerk

**Why**

A truck arrives with the steel. Somebody must record the arrival, the heat number and the yard location. The heat number gives the material traceability.

=== "Tekla PowerFab Office"

    1. Go to **Purchasing > Purchase Orders**.
    2. Open the purchase order.
    3. Select the items that arrived.
    4. Click **Receive**.

=== "Tekla PowerFab Go"

    1. Log in to the web interface.
    2. Tap **Receiving** and select the purchase order number.
    3. Enter the heat number from the mill.
    4. Enter the yard location.
    5. Tap **Receive**.

!!! tip
    Attach the heat document at the receiving step. **Check Heat Documents** finds the missing documents later, but the paperwork is easier to find on the day of the delivery.

---

## Step 14: Global edit and apply a route

**Role:** Production Manager

**Why**

A route is the path of one piece through the shop. For example: Saw, then Drill Line, then Welding, then Paint.

**Steps**

1. Open the Production Control job.
2. Select all the main assemblies: the columns and the beams.
3. Right-click and select **Global Edit**.
4. Turn on the **Route** checkbox.
5. Select a standard structural route from the list.
6. Click **Update**.

!!! danger
    Apply the route before Step 15. A route that you apply after the cutlist does not give the completion credit for the cut station. The Station Summary stays empty. You must then add a completed entry by hand.

!!! warning
    Examine the TFS Station field in the route. The default value can point to the last station. Set it to the first station, the cut station.

---

## Step 15: Make a cutlist

**Role:** Shop Foreman

**Why**

The saw operator needs a specific batch of work. A cutlist gives the raw lengths, the cut lengths and the piece marks for one shift.

**Steps**

1. Go to **Review > Cut Lists**.
2. Click **New Cut List**.
3. Filter for the shapes, for example all the W shapes or all the angles.
4. Name the cutlist, for example Monday Morning Saw Batch.
5. Save the cutlist.

!!! warning
    New users often open **Dashboards > Cut List Management**. That screen manages an existing cutlist. Use **Review > Cut Lists** to make a new one.

---

## Step 16: Process the cutlist

**Role:** Machine Operator

**Why**

The software must know that the cut is complete. The process action removes the raw length from inventory and makes the individual project parts.

**Steps**

1. In Tekla PowerFab Go, tap **Cut Lists**.
2. Select the cutlist, for example Monday Morning Saw Batch.
3. Examine the lengths for each cut.
4. Tap **Process**.
5. Enter the drop location for each remnant.

!!! tip
    A drop with a location goes back into inventory as usable material. A drop without a location is lost value.

---

## Step 17: Update the production tracking

**Role:** Shop Floor Workers

**Why**

The office needs live progress data. Each station update moves the progress bar and changes the colour of the assembly in Trimble Connect.

**Steps**

1. The welder opens Tekla PowerFab Go on a tablet.
2. Tap **Production Tracking**.
3. Scan the barcode on the beam, or find the piece mark, for example C1.
4. Select the station, for example Welding.
5. Tap **Add Time** or **Complete**.
6. Do the same task at the quality assurance station and at the paint station.

!!! warning
    The Station Summary stays empty when the items have no route. Go back to Step 14 if the numbers do not appear.

---

## Step 18: Make a load and ship it

**Role:** Shipping Manager

**Why**

The steel is complete. Load tracking makes a digital truck. It gives the Bill of Lading for the driver and the delivery record for the site.

**Steps**

1. Go to **Production Control > Load Tracking**.
2. Click **New Load**.
3. Assign a trailer number and a destination.
4. A yard worker scans the finished beams into the load with Tekla PowerFab Go.
5. Click **Ship Load**.
6. Print the Bill of Lading for the driver.

!!! warning
    Tekla PowerFab Office does not stop a load with incomplete route stations. Tekla PowerFab Go 2026 does stop it. Examine the route status before you ship.

---

## End of the exercise

The job moved from a 3D model to physical steel at the construction site.

!!! info "Content to add"
    Add the field notes, the FAQ and the screenshots for each step here.

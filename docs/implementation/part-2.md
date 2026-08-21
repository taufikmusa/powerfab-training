# Part 2 — Steps 11 to 18

Part 2 procures the material that detailing added, then drives the job through the shop and onto a truck.

Complete [Part 1](part-1.md) before starting.

---

## Step 11 — Combine the balance material

**Role:** Purchasing Agent / Production Manager · **Module:** Production Control

**Why this matters**

The `.pfxt` import in Step 10 brought in everything detailing added — shear tabs, base plates, connection angles, bolts. None of it was covered by the early purchase in Step 6, because none of it existed when that order was placed. This material now has to be optimised and bought.

**How to do it**

1. Open the job in the **Production Control** module.
2. Go to **Production Control > Combine**.
3. Set the filter to items that are **Not Linked** — material not already covered by an existing purchase.
4. Click **Mult (F4)** to run the optimisation.
5. Review how the plates nest into standard stock sheets.
6. Click **Save Displayed Results & Close**.

**You should now have:** the balance material solved and ready to requisition.

---

## Step 12 — Send balance material to requisition and purchase order

**Role:** Purchasing Agent · **Modules:** Production Control, Purchasing

**Why this matters**

Mechanically this is identical to Step 6. What differs is the material: Step 6 bought the main members off a preliminary model, this step buys the connection material off the final one.

**How to do it**

1. From the Production Control window, go to **Production Control > Send to Requisition**.
2. Choose **Combined Materials Only**.
3. Create a new requisition — `REQ-Plates-Bolts`.
4. Open the **Purchasing** module, locate the requisition, and convert it into a formal purchase order.

**You should now have:** a second purchase order covering plates, angles, and bolts.

---

## Step 13 — Receive the material

**Role:** Yard Foreman / Receiving Clerk · **Modules:** Purchasing, Inventory

**Why this matters**

When a truck arrives, someone has to unload it, check it against the packing slip, and record what actually turned up. Heat numbers captured at this point are what make material traceable for the rest of the project — and traceability is a contractual requirement on most structural work.

=== "In PowerFab Office"

    1. Go to **Purchasing > Purchase Orders**.
    2. Open the relevant PO.
    3. Select the items that arrived.
    4. Click **Receive**.

=== "In PowerFab Go (tablet)"

    1. Log in to the web interface.
    2. Tap **Receiving** and select the PO number.
    3. Enter the **Heat Number** from the mill certification.
    4. Enter the yard **Location** where the material was placed.
    5. Tap **Receive**.

**You should now have:** material in inventory, tagged with heat numbers and yard locations.

!!! tip "Attach heat documents at the point of receipt"
    **Check Heat Documents** can find missing certification later, but chasing a supplier for paperwork six weeks after delivery is a different job to asking the driver for it at the gate. Capture it while the delivery is happening.

---

## Step 14 — Global edit and apply routes

**Role:** Production Manager · **Module:** Production Control

**Why this matters**

A route defines the path a piece takes through the shop — Saw, then Drill Line, then Weld, then Paint, then Ship. Without a route, the system has no idea what "finished" means for a given piece, and none of the tracking in the following steps will register.

**How to do it**

1. Open the Production Control job.
2. Select all main assemblies — the columns and beams.
3. Right-click and choose **Global Edit**.
4. Tick the **Route** checkbox and select a standard structural route, such as *Standard Fab & Paint*.
5. Click **Update**.

**You should now have:** every main assembly carrying a defined fabrication route.

!!! danger "Routes must be applied before Step 15 — this cannot be fixed later"
    Confirmed live during a technical enablement session: if the cut list is built and processed before routes are assigned, applying routes afterwards does **not** back-fill completion credit for the Cut/Saw station.

    The Station Summary stays blank despite the cuts having genuinely been processed, and the only remedy is manually adding completed entries piece by piece. This is why Step 14 sits where it does in the sequence.

!!! warning "Verify the TFS Station on the route"
    Routes can default their **TFS Station** to the last station in the sequence rather than the first. On a Sample SP route this appeared as *Sample - Erection* instead of *Sample - Cut/Saw*. Material taken from stock is then credited at entirely the wrong point. Check this field before processing anything.

---

## Step 15 — Create a cut list

**Role:** Shop Foreman · **Module:** Production Control

**Why this matters**

A saw operator cannot work from a full project BOM. A cut list is a defined batch of work for a specific machine and a specific shift, showing which raw lengths to load and which pieces to produce from them.

**How to do it**

1. Go to **Review > Cut Lists**.
2. Click **New Cut List**.
3. Filter for the shapes required — all W-shapes, or all angles, for example.
4. Name the list something the shop will recognise, such as *Monday Morning Saw Batch*.
5. Save.

**You should now have:** a named, prioritised cut list ready to appear on the operator's tablet.

!!! warning "Common navigation error"
    New users frequently head for **Dashboards > Cut List Management**. That screen manages lists that already exist. Creation happens under **Review > Cut Lists**.

---

## Step 16 — Process the cut list

**Role:** Machine Operator · **Software:** Tekla PowerFab Go

**Why this matters**

Cutting the steel and telling the system it has been cut are two different events. Processing converts a raw length in inventory into individual project parts, and it is what allows every subsequent tracking step to function.

**How to do it**

1. In PowerFab Go, tap **Cut Lists**.
2. Select *Monday Morning Saw Batch*.
3. For each cut, verify the lengths against the physical material.
4. Tap **Process**.
5. Where a remnant is produced, enter the **Drop Location** so the system knows where that offcut is stored.

**You should now have:** raw stock consumed, project parts created, and drops recorded against yard locations.

!!! tip "Drops without locations are written-off steel"
    A remnant recorded with a location returns to inventory as usable stock and can be consumed by a later job. One processed without a location is effectively scrapped on paper regardless of what is physically sitting in the rack.

---

## Step 17 — Update production tracking

**Role:** Shop Floor Workers · **Software:** Tekla PowerFab Go

**Why this matters**

The office needs to know where work actually is, not where it was supposed to be. Each station update moves progress reporting forward and recolours the assembly in Trimble Connect, giving project managers and clients a live view without anyone compiling a report.

**How to do it**

1. The welder opens PowerFab Go on a tablet.
2. Tap **Production Tracking**.
3. Scan the barcode on the member, or search for the piece mark — `C1`, for example.
4. Select the station — *Welding*.
5. Tap **Add Time** or **Complete**.
6. Repeat at the Quality Assurance and Painting stations.

**You should now have:** live progress visible in **Production Status** and reflected in the Trimble Connect model.

!!! warning "A blank Station Summary points back to Step 14"
    If tracking appears to work but the Station Summary stays empty, the material has no route assigned. Fix the routing rather than troubleshooting the tracking screen — the tracking is behaving correctly, it simply has no stations to report against.

---

## Step 18 — Create a load and ship

**Role:** Shipping Manager · **Module:** Load Tracking

**Why this matters**

Load Tracking is the shipping department in software form. It creates a digital truck, records what physically goes onto it, and produces the Bill of Lading that travels with the driver and the delivery record the site will sign against.

**How to do it**

1. In PowerFab Office, go to **Production Control > Load Tracking**.
2. Click **New Load** and assign a Trailer Number and Destination.
3. A yard worker uses PowerFab Go to scan finished members onto the load as the forklift places them.
4. Once loading is complete, click **Ship Load**.
5. Print the Bill of Lading for the driver.

**You should now have:** a shipped load, a Bill of Lading, and a complete delivery record against the job.

!!! warning "Office will not stop an incomplete load from shipping"
    Confirmed live: **Tekla PowerFab Office** allows a load to ship even when route stations remain incomplete. **Tekla PowerFab Go 2026** enforces the requirement that all stations be complete before shipping.

    An office user can therefore ship steel the shop has not finished. Where this matters, the control has to come from process discipline or from routing shipping through Go — Office will not prevent it.

---

## Exercise complete

The job has travelled from a preliminary 3D model, through early procurement, detailing, fabrication, quality control, and out of the door on a truck — with full material traceability from mill certificate to delivered piece.

!!! info "To be completed"
    Add field notes, frequently asked questions, and step-by-step screenshots for each stage.

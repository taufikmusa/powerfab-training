# Day 3 — Afternoon Session

- **Topic:** Production Control 1 and Purchasing
- **Chapters:** 6.0 thru 6.15

## 1. Import the final bill of materials (Chapters 6.0 thru 6.3)

1. Make a new **Production Control (PDC)** job.
2. Import the final bill of materials with **PowerFab eXchange**. The file is a PFXT file or an XML file.
3. Map the user-defined attributes.
4. Import the CNC files.
5. Upload the model to **Trimble Connect**.

## 2. Project breakdown and routing (Chapters 6.4 thru 6.7)

### 2.1 Sequences and lots

1. Assign the sequences and the lots to the assemblies by hand.
2. Do the same task again through the Trimble Connect model.

### 2.2 Work packages

1. Group the assemblies into work packages.
2. Use the **Smart Create** tool.

### 2.3 Stations and routes

1. Make a fabrication route, for example Assembly > Welding > Paint > Shipping.
2. Apply the route to the imported material.

!!! danger
    Assign the route to the items before you make the cutlist. A route that you assign later does not give the completion credit for the cut station. You must then add a completed entry by hand.

!!! warning
    Examine the TFS Station field in each route. The default value can point to the last station instead of the first station. Set it to the cut station before you process a cutlist.

## 3. Link the advance bill and buy the material (Chapters 6.8 thru 6.15)

### 3.1 Link CMB and PDC

1. Link the advance bill of materials to the final bill of materials.
2. Run the comparison report.
3. Find the critical differences. For example, find where the detailed length is more than the ordered length.

### 3.2 Requisitions to purchase orders

1. Send the material that is not linked to a requisition.
2. Combine the material with **Mult** and **Nest**.
3. Push the requisition to a purchase order.

### 3.3 Receiving

1. Receive the purchase order into inventory.
2. Attach the heat documents.
3. Enter the heat numbers.

!!! tip
    A requisition that you never turn into a purchase order keeps the material in a hold state. The material does not show in inventory. Examine the requisition list at the end of the day.

## Exercise

!!! info "Content to add"
    Add the afternoon exercise steps and the screenshots here.

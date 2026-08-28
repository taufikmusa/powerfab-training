# Practice Checklist

The condensed click path for all eighteen steps, with no explanations.

This is for the **second** run, not the first. Work through [Part 1](part-1/index.md), [Part 2](part-2/index.md), and [Part 3](part-3/index.md) once so the concepts are understood, then use this page hands-on to build speed.

!!! info "Job reference"
    Practice job `TRN-001`, requisition `RQ-001`, purchase order `TRN-001`. Tekla PowerFab 2026 SP2 running the SEA regional database.

---

## Steps 1 – 6 — Project setup through requisition

### Step 1 — Create a Project Management job

- [ ] **Project Management** on the main toolbar → **Add (F1)**
- [ ] **Job #** (`TRN-001`) → **Description** / **Location** → **Job Status: Open** → **Save**

### Step 2 — Create a project schedule

- [ ] **Maintenance > Project Management > Schedule Templates** → **New Template (F1)** → name it
- [ ] **New Task** × 4 (Detailing / Fabrication / Shipping / Installation) — tick **Sequence** + **Lot #** — set **Status Link** per task — **Add (F4)** each → **Save Template (F4)**
- [ ] Open job → **Project Schedule** → **Schedule Tasks** tab → **Apply Template** → select template → **OK**
- [ ] **Project Breakdown** tab → **New** → Sequence + Description → **Apply to Tasks > All** → **Save (F4)**; repeat per sequence
- [ ] **Gantt Chart** tab → **Edit Mode** → stagger dates sequentially → **Save (F4)**
- [ ] **Baseline Plan** tab → **Set Baseline** → **Yes**

**Apply Template once only.** A second click silently duplicates every task — check the row count before moving on.

### Step 3 — Model, mark, and export (Tekla Structures)

- [ ] Build the model, no connections yet
- [ ] Assign a **Preliminary mark** (`PRELIM_MARK`) on every part
- [ ] **File > Export > IFC** using the **Steel fabrication view** or **2x3 EM11** format — or use the PowerFab Connector if available

### Step 4 — Import the IFC into the Advance Bill

- [ ] **File > Import > Advance Bill > IFC** → browse → **Import**
- [ ] Job # → **Project Management Job > Load Info** → **Save**
- [ ] **Import Field Map** → **Reference Number** row → Tekla PowerFab Field: **Reference #** → **Set Field Mapping** → **OK**
- [ ] Resolve any **Translate Shapes/Grades** prompts carefully
- [ ] **Change Summary** (if shown) → **Continue**
- [ ] Confirm **Successful: X / Unsuccessful: 0**

**Set Field Mapping must be clicked.** Choosing the value in the dropdown does not commit it.

### Step 5 — Combine partially

- [ ] **Advance Bill** ribbon → **Combine** → choose **Mult** / **Nest** / **Mult & Nest**
- [ ] **Combining Run Filters** → click the **Reference #** row → **Select**
- [ ] Filter dialog → **`<<`** to clear → select items → **`>`** to include → **OK**
- [ ] Confirm the Reference # row no longer reads *All*
- [ ] Click the combine button — **MULT (F4)**
- [ ] Check **Combining Run Results** — confirm **% Combined** and **Cost** are not 0% / $0.00
- [ ] **Save Displayed Results & Close** → **Requisitions** → **Add** new → **OK**

**0% / $0.00 is a failure.** Check Shape/Grade/Size Maintenance and Pricing Maintenance before blaming the model or the filter.

### Step 6 — Send to requisition and purchasing

- [ ] **Purchasing** module → **Requisitions** tab → open `RQ-001`
- [ ] Confirm each line's quantity / profile / grade / price / cost
- [ ] Confirm **Linked to ABM** shows a full ratio (X/X) on **each** item, not just the first
- [ ] Once vendor pricing is back: **Load Material into Purchase Order**

---

## Steps 7 – 13 — Connections through receiving

### Step 7 — Complete the connections (Tekla Structures)

- [ ] Build connections — auto-connections are fine for practice
- [ ] Reassign final assembly marks
- [ ] **Check for case-colliding marks** (`M1` versus `m1`) before moving on
- [ ] Save and update the model

### Step 8 — Create drawings and NC files

- [ ] Create assembly **and** single part drawings
- [ ] **Print Drawings** — assembly first, then single parts
- [ ] **File > Export > Tekla PowerFab** settings → tick **Generate CNC files** → **Save the setting**

**Ticked is not saved.** Without clicking Save on that panel, the next export produces zero NC files silently.

### Step 9 — Export to PowerFab

- [ ] Connector path: **Submit to Tekla PowerFab** → select Project → **Fabrication** → **Validate** → **Export and submit**
- [ ] Manual fallback: **File > Export > Tekla PowerFab** → **Drawing list** → confirm CNC ticked → `.pfxt` → **Export**

**Uploaded is not Received.** Verify the job exists on the PowerFab side before assuming this step is done.

### Step 10 — Import the `.pfxt` into Production Control

- [ ] **File > Import > Production Control** → browse `.pfxt` → **Import**
- [ ] Confirm or create the linked Project Management job — same job #
- [ ] **Import Field Map** → `PRELIM_MARK` row → **Reference #** → **Set Field Mapping** → **OK**
- [ ] Resolve **Translate Shapes/Grades** prompts carefully
- [ ] **Change Summary** → scroll to confirm all *Add* → **Continue**
- [ ] Confirm the job appears under **Production Control > Select Production Control Job**

**Read the full import log**, not just the Successful / Unsuccessful count. Warnings hide inside successful imports.

### Step 11 — Combine the balance material

- [ ] **Production Control** ribbon → **Combine** → **Mult**
- [ ] **Combining Run Filters** → **Main Mark** / **Reference #** row → **Select** → choose items → **OK**
- [ ] Run the combine → check real **% Combined** and **Cost**
- [ ] Hardware showing **Not Combined** is normal — no action needed
- [ ] **Save Displayed Results & Close** → **Requisitions** → **Save**

### Step 12 — Send to requisition and purchasing

- [ ] **Purchasing > Requisitions** tab → confirm **Linked to PDC** is a full ratio
- [ ] **Open the requisition** (double-click into the detail screen) → **Requisition** ribbon tab → **Load Material Into Purchase Order**
- [ ] Pick or create the PO → work through **Purchasing Import Filters** → confirm
- [ ] **Purchase Orders** tab — confirm the PO is now populated

**The command is not on the list screen.** Right-clicking the list only offers Select All and Export to Excel.

### Step 13 — Receive the material

- [ ] Open the PO → **Switch to Receive Mode**
- [ ] Select the line(s) → enter **Received** qty → optional **Receiving Fields** (heat number, country of origin, bill of lading) → **Save (F4)**
- [ ] Optional: repeat in PowerFab Go → **Inventory > Receive**

**Receive Mode exists only on the purchase order.** The Requisition's lookalike toggle reads *Switch to Manual Combine Mode*.

---

## Steps 14 – 18 — Routing, cutting, tracking, and shipping

### Step 14 — Apply the fabrication route

- [ ] **Maintenance > Production Control > Fabrication Maintenance > Station and Route Setup** → **Route Maintenance**
- [ ] Verify **TFS Station** = the **first** station (Cut/Saw)
- [ ] Verify **Route Type** matches what is being routed — Assembly / Part / Assembly & Part
- [ ] Verify the **In Route** station list and its order → **Save (F4)**
- [ ] Select items → **Production Control > Modify Data > Global Edit (Selected)** → tick **Route** → pick route → **Update** → **Yes**

**Fixing a route does not apply it.** Global Edit is a separate, mandatory step — and it must happen before Step 16.

### Step 15 — Create a cut list

- [ ] **Production Control > Review > Cut Lists** → **New Cut List**
- [ ] Confirm filters — default All for a first run
- [ ] **Make Report** → **View** → confirm materials look right → close preview
- [ ] **Save Cut List** → fill **Description** and **Date Required** → **Save To Cut List** → **OK**

**Requisitioned material will not appear.** Only material on a PO or in stock is eligible, and nothing warns you.

### Step 16 — Process the cut list

- [ ] **Cut Lists** → select the list → **Details**
- [ ] Select a line → **Cut** → choose **Heat #** → complete PO # / Location → review **Drop** → **TFS (F4)**
- [ ] Repeat for every cutting detail until all show **Complete**

### Step 17 — Production tracking

- [ ] **Production Control > Piece Tracking** → **Station Summary**
- [ ] Select a station → **Add Completed** → pick the **Station** from the dropdown
- [ ] Move items *Not Included* → *Included* → set **Completed By** / **Date** → **Add Material**
- [ ] Shop floor: repeat via PowerFab Go for real-time entry

**A blank Station Summary means no route.** Go back to Step 14.

### Step 18 — Create a load and ship

- [ ] **Production Control > Load Tracking** → **New Load**
- [ ] Set **From** / **Destination Group** / **Load #** / **Trailer #** / **Haulage Company** → **Save**
- [ ] **Add Material** → move items to *Included* → confirm
- [ ] **Ship** → set **Date Shipped** → **Shipping Ticket** → **View** / **Print** / **Export**

**Office will not block an incomplete load.** PowerFab Go 2026 will.

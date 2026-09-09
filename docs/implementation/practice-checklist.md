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

- [ ] Select the members → **AutoConnection** → **Rule groups** tab
- [ ] Connection selection → **End_Plate** · connection parameters → **Green Book 1**
- [ ] **Create connections**
- [ ] Reassign final assembly marks
- [ ] **Check for case-colliding marks** (`M1` versus `m1`) before moving on
- [ ] Save and update the model

### Step 8 — Create drawings and NC files

- [ ] **Drawings & reports** → **Create fabrication drawing** → check **Creation review** → **Create**
- [ ] Create assembly **and** single part drawings
- [ ] **Document manager** → **Print drawings** → **PDF file** → **File location** `.\Plotfiles`
- [ ] Confirm the PDFs landed — both assembly and single part
- [ ] **File > Export > Tekla PowerFab** → **Submittal type: Fabrication** → its **Fabrication settings**
- [ ] All three drawing types **Include**, each pointing at the folder you printed to
- [ ] **CNC files** → **Generate CNC files - settings** → **PowerFab**
- [ ] In **NC Files**: DSTV for Angle, Plate and Profile ticked → **Save** the named setting

**Ticked is not saved.** The DSTV rows belong to a named setting; close the dialog without saving it and the next export produces zero NC files silently.

### Step 9 — Export to PowerFab

- [ ] Connector path: **Submit to Tekla PowerFab** → select Project → **Fabrication** → **Validate** → **Export and submit**
- [ ] Manual fallback: **File > Export > Tekla PowerFab** → **Drawing list** → confirm CNC ticked → `.pfxt` → **Export**

**Uploaded is not Received.** Verify the job exists on the PowerFab side before assuming this step is done.

### Step 10 — Import the `.pfxt` into Production Control

- [ ] **File > Import** → **Production Control** → **PowerFab eXchange** → browse `.pfxt`
- [ ] **Test Import** first, then **Import**
- [ ] Confirm or create the job — check **Project Management Job** carries the same job #
- [ ] Trimble Connect link prompt — optional, the import completes either way
- [ ] **Import Field Map** → `PRELIM_MARK` row → **Reference #** → **Set Field Mapping** → **OK**
- [ ] Resolve **Translate Shapes/Grades** prompts carefully
- [ ] **Change Summary** → scroll to confirm all *Add* → **Continue**
- [ ] Read the log — check the **CNC files found** count, not just Successful / Unsuccessful
- [ ] Confirm the job appears under **Production Control > Select Production Control Job**
- [ ] Confirm it carries **Items** and **Weight** — not 0 / 0Kg

**Read the full import log**, not just the Successful / Unsuccessful count. Warnings hide inside successful imports; the reports are saved under **Document Index (F8)** if you closed the dialog.

### Step 11 — Combine the balance material

- [ ] **Production Control** ribbon → **Combine** → **Mult (F1)**
- [ ] **Combining Run Filters** — leave rows on *All* for the whole balance, or **Main Mark** / **Reference #** row → **Select** → choose items → **OK**
- [ ] **MULT (F4)**
- [ ] Check each combined row has a real **Cost** and **Drop** — not the headline % alone
- [ ] Hardware showing **Not Combined** is normal — no action needed
- [ ] **Save Displayed Results & Close** → **Requisitions** → pick or **Add (F1)** → **OK (F5)**
- [ ] Reopen the requisition — confirm **Items** and **Weight** went up from 0
- [ ] Confirm **Linked to PDC** is a full ratio

### Step 12 — Send to requisition and purchasing

- [ ] **Purchasing > Requisitions** tab → confirm **Linked to PDC** is a full ratio
- [ ] **Open the requisition** (double-click into the detail screen) → **Requisition** ribbon tab → **Load Material Into Purchase Order**
- [ ] Pick or **Add (F1)** the PO → **OK (F5)**
- [ ] **Purchasing Import Filters** — check the **Filters Set** header reads *None* → **Import (F4)**
- [ ] **Import Items** — confirm **Processed** equals **Total** → **OK**
- [ ] **Purchase Orders** tab — confirm the PO carries the items and cost

**The command is not on the list screen.** Right-clicking the list only offers Select All and Export to Excel.

### Step 13 — Receive the material

- [ ] **Purchasing** → **Purchase Orders** tab (not Requisitions) → **Open (F5)**
- [ ] **Switch to Receive Mode** — confirm the toggle now reads *Switch to Input Mode*
- [ ] Select the line(s) → enter **Received** qty, or **Receive (F1)** / **Receive Displayed (F2)**
- [ ] Optional **Receiving Fields** (heat number, country of origin, bill of lading) → **Save (F4)**
- [ ] Back in Input Mode — confirm the **Received** counter moved off zero
- [ ] Optional: repeat in PowerFab Go → **Inventory > Receive**

**Receive Mode exists only on the purchase order.** The Requisition's lookalike toggle reads *Switch to Manual Combine Mode*.

---

## Steps 14 – 18 — Routing, cutting, tracking, and shipping

### Step 14 — Apply the fabrication route

- [ ] **Maintenance > Production Control > Fabrication Maintenance > Station and Route Setup** → **Route Maintenance**
- [ ] Verify **TFS Station** = the **first** station (Cut/Saw)
- [ ] Verify **Route Type** matches what is being routed — Assembly / Part / Assembly & Part
- [ ] Verify the **In Route** station list and its order — check the **Not in Route** tab for anything missing → **Save (F4)**
- [ ] On the job screen, confirm the route column reads *Unassigned* before you start
- [ ] Select items → **Production Control > Modify Data > Global Edit (Selected)**
- [ ] **Un-check All** → tick **Route** only → pick route → **Update (F4)** → **Yes**
- [ ] Re-read the route column — it should now name the route

**Fixing a route does not apply it.** Global Edit is a separate, mandatory step — and it must happen before Step 16.

**Tick one box only.** Global Edit pre-fills every field from the selected item; each ticked box writes that value across the whole selection.

### Step 15 — Create a cut list

- [ ] **Production Control > Review > Cut Lists** → **New Cut List**
- [ ] Confirm filters — check the **Filters Set** header, default All for a first run → **Make Report (F4)**
- [ ] Pick a report → **View (F1)** → confirm materials look right → close preview
- [ ] **Save Cut List** (on the Report Selection dialog) → **Description**, **Date Required**, **Workshop** / **Machine** / **Priority**
- [ ] **Save To Cut List** → **OK**

**Requisitioned material will not appear.** Only material on a PO or in stock is eligible, and nothing warns you — check the **P.O. #** column on the report, and use **Validate** on the Cut Lists screen.

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

# Implementation Workflow

This exercise takes a single job through the complete Tekla PowerFab workflow in eighteen steps — starting with an empty project shell and a 3D model, and ending with steel on a truck and a Bill of Lading in the driver's hand.

Use practice job **TRN-001** throughout.

## Why this exercise exists

The five-day course teaches one module at a time, which is the only practical way to deliver it. The cost of that approach is that participants can finish the week competent in each module and still not see how they connect.

This exercise fixes that. Working through it once shows exactly how a decision made in Tekla Structures on day one shows up on the shop floor two weeks later — and why the sequencing rules that seem arbitrary in the classroom are not arbitrary at all.

!!! info "Prerequisites"
    Access to **Tekla Structures**, **Tekla PowerFab Office**, and **Tekla PowerFab Go**, running against the SEA regional database. Allow roughly a full day to complete both parts unhurried.

## The two parts

| Part | Steps | Covers |
|---|---|---|
| [Part 1](part-1.md) | 1 – 10 | Project setup, early procurement, detailing, and handover to Production Control |
| [Part 2](part-2.md) | 11 – 18 | Balance material, fabrication, quality, and shipping |

## Roles involved

The workflow deliberately passes between roles. In a real fabrication business these are different people, often in different buildings.

| Role | Steps |
|---|---|
| Project Manager | 1, 2 |
| Steel Detailer | 3, 7, 8, 9 |
| Estimator / Purchasing Agent | 4, 5, 6, 11, 12 |
| Production Manager | 10, 14 |
| Yard Foreman / Receiving Clerk | 13 |
| Shop Foreman / Machine Operator | 15, 16 |
| Shop Floor Workers | 17 |
| Shipping Manager | 18 |

## Step index

| Step | Task | Software |
|---|---|---|
| 1 | Create a Project Management job | PowerFab Office |
| 2 | Create a project schedule | PowerFab Office |
| 3 | Model without connections and export IFC | Tekla Structures |
| 4 | Import IFC into the Advance Bill | PowerFab Office |
| 5 | Partially combine advance bill material | PowerFab Office |
| 6 | Send to requisition and raise a purchase order | PowerFab Office |
| 7 | Complete connections in the model | Tekla Structures |
| 8 | Create drawings and export NC files | Tekla Structures |
| 9 | Export to PowerFab as `.pfxt` | Tekla Structures |
| 10 | Import `.pfxt` into Production Control | PowerFab Office |
| 11 | Combine the balance material | PowerFab Office |
| 12 | Send balance material to requisition and PO | PowerFab Office |
| 13 | Receive material | Office + Go |
| 14 | Global edit and apply routes | PowerFab Office |
| 15 | Create a cut list | PowerFab Office |
| 16 | Process the cut list | PowerFab Go |
| 17 | Update production tracking | PowerFab Go |
| 18 | Create a load and ship | Office + Go |

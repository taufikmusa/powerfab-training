# Implementation Workflow

This exercise takes a single job through the complete Tekla PowerFab workflow in eighteen steps — starting with an empty project shell and a 3D model, and ending with steel on a truck and a shipping ticket in the driver's hand.

Use practice job **TRN-001** throughout.

## Why this exercise exists

The five-day course teaches one module at a time, which is the only practical way to deliver it. The cost of that approach is that participants can finish the week competent in each module and still not see how they connect.

This exercise fixes that. Working through it once shows exactly how a decision made in Tekla Structures on day one shows up on the shop floor two weeks later — and why the sequencing rules that seem arbitrary in the classroom are not arbitrary at all.

!!! info "Prerequisites"
    Access to **Tekla Structures**, **Tekla PowerFab Office**, and **Tekla PowerFab Go**, running against the SEA regional database. Allow roughly a full day to complete all three parts unhurried.

## The three parts

| Part | Steps | Covers |
|---|---|---|
| [Part 1](part-1/index.md) | 1 – 6 | Project setup, preliminary model, and early procurement |
| [Part 2](part-2/index.md) | 7 – 13 | Detailing, handover to Production Control, and the balance material |
| [Part 3](part-3/index.md) | 14 – 18 | Routing, cutting, tracking, and shipping |
| [Practice Checklist](practice-checklist.md) | 1 – 18 | Click path only, for a second hands-on run |

Each step carries the same six sections: the role responsible, why the step matters, the click-by-click instructions, the mistakes that catch people out, an FAQ, and field notes recorded during a live test run.

## Roles involved

The workflow deliberately passes between roles. In a real fabrication business these are different people, often in different buildings.

| Role | Steps |
|---|---|
| Project Manager | 1, 2 |
| Steel Detailer / BIM Modeller | 3, 7, 8, 9 |
| Estimator / Material Planner | 4, 5, 11 |
| Purchasing Agent | 6, 12 |
| Production Control Coordinator | 10, 14, 15 |
| Purchasing Agent / Yard Foreman | 13 |
| Workshop / Cutting operator | 16 |
| Shop floor supervisor | 17 |
| Shipping / Logistics Coordinator | 18 |

## Step index

| Step | Task | Software |
|---|---|---|
| 1 | Create a Project Management job | PowerFab Office |
| 2 | Build a schedule template, apply it, and set the baseline | PowerFab Office |
| 3 | Model without connections, assign preliminary marks, export IFC | Tekla Structures |
| 4 | Import the IFC into the Advance Bill | PowerFab Office |
| 5 | Partially combine advance bill material | PowerFab Office |
| 6 | Send to requisition and check the ABM links | PowerFab Office |
| 7 | Complete connections and final assembly marks | Tekla Structures |
| 8 | Create drawings and generate NC files | Tekla Structures |
| 9 | Export to PowerFab as `.pfxt` | Tekla Structures |
| 10 | Import `.pfxt` into Production Control | PowerFab Office |
| 11 | Combine the balance material | PowerFab Office |
| 12 | Send balance material to requisition and PO | PowerFab Office |
| 13 | Receive material | Office + Go |
| 14 | Verify the route, then apply it by global edit | PowerFab Office |
| 15 | Create a cut list | PowerFab Office |
| 16 | Process the cut list — cut and TFS | PowerFab Office |
| 17 | Update production tracking | Office + Go |
| 18 | Create a load and ship | Office + Go |

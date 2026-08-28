# Glossary

Terms used throughout this documentation and in the Tekla PowerFab interface.

| Term | Definition |
|---|---|
| **ABM** | Advance Bill of Materials. The preliminary material list used to place long-lead orders before detailing is finished. |
| **Advance Bill** | The Tekla PowerFab staging area holding material intended for early purchase. |
| **AE** | Automated Events. The module that runs scheduled tasks without a logged-in user, via the Remote Server service. |
| **Baseline** | The saved original schedule dates, set once the programme is agreed. Without it, planned-versus-actual variance cannot be tracked. |
| **Bill of Lading** | The shipping document issued with a load and carried by the driver. |
| **Change Summary** | The dialog listing every add, modify, and delete an import is about to apply. All *Add* is expected on a first import. |
| **CMB** | The Combining module, and the job type it creates. |
| **Combine** | The optimisation that determines how short pieces are cut from longer raw stock with minimum waste. |
| **Combining Run** | A single execution of the combine optimisation, defined by its run type (Mult / Nest) and its filters. |
| **Complete Previous Station First** | Route setting that forces stations to be logged in order. Left unticked, work can be recorded out of sequence. |
| **Critical Difference** | A discrepancy found when comparing the Advance Bill against the final BOM — most often a detailed length exceeding the length ordered. |
| **Cut List** | A defined batch of cutting work assigned to a machine operator for a given shift. |
| **Destination Group** | The grouping a load is shipped to — jobsite, galvaniser, third-party processor — used for routing and reporting. |
| **Document Index** | The per-job document store. Import change summaries and logs are saved here automatically as PDFs. |
| **Drop** | The usable remnant left after a cut. Returns to inventory only if a drop location is recorded. |
| **Find Abbreviation** | Search tool in Shapes/Grades/Sizes maintenance used to locate a shape alias without browsing by Material Group. |
| **Global Edit** | Bulk-edit function that applies a field change across all selected rows at once. |
| **Heat Number** | The mill batch identifier that provides material traceability. |
| **IFC** | Industry Foundation Classes. Open format for exchanging 3D model data between systems. |
| **JOBSUM** | Report listing all material charged to a specific job via TFS. |
| **KISS** | A text-based material list format supported for import. |
| **Labor Standard** | The time value Tekla PowerFab uses to calculate man-hours for an operation. |
| **Linked to ABM** | Ratio showing how many of a requisition's stock pieces reconcile back to the original Advance Bill line items. A partial ratio means material is missing. |
| **Linked to PDC** | The same reconciliation ratio as Linked to ABM, but back to Production Control rather than the Advance Bill. |
| **Lot** | A grouping of assemblies, typically aligned to erection sequence. |
| **Mult** | The multiple-length combine calculation, used for linear material. |
| **NC File** | Machine-readable instruction file for a saw, drill line, or plasma table. Commonly `.nc1`. |
| **Nest** | The combine calculation used for plate material on sheets. |
| **PDC** | The Production Control module, and the job type it creates. |
| **PFXT** | Tekla PowerFab eXchange transfer file. Carries the material list, drawings, and NC files in one package. |
| **Piece Tracking** | The Production Control screen used to record work completed at each station on a route. |
| **PO** | Purchase Order. The formal commitment issued to a supplier. |
| **PRELIM_MARK** | The user-defined attribute carrying a preliminary mark from Tekla Structures, mapped to Reference # on import. |
| **Preliminary Mark** | A throwaway identifier assigned before connections are designed, so material can be grouped and ordered early. Replaced by final assembly marks at Step 7. |
| **PRJ** | The Project Management job type. |
| **Project Breakdown** | The sequence and lot structure applied to schedule tasks. Names must match Production Control exactly or status links fail silently. |
| **Requisition** | An internal material request. Does not order anything until converted to a purchase order. |
| **RFI** | Request For Information. Formal query raised to the engineer or client. |
| **Route** | The defined sequence of stations a piece passes through during fabrication. |
| **Route Type** | Whether a route applies to assemblies, to individual parts, or to both. |
| **S/G/S** | Shapes / Grades / Sizes. The global material database read by every module. |
| **Sequence** | A grouping of assemblies aligned to fabrication order. |
| **Shipping Ticket** | The driver's paperwork generated from Load Tracking. Report selection determines whether it prints as a delivery copy or a bill of lading. |
| **SOV** | Schedule of Values. The contract breakdown that invoices are raised against. |
| **Station** | A single work point within a route — Saw, Fit, Weld, Paint, and so on. |
| **Station Summary** | The Piece Tracking view listing every station with assigned work and its total, completed, and remaining quantities. |
| **Status Link** | The tracked event that drives a schedule task's progress automatically. Tasks with no matching event use `[None]` and `No Factor`. |
| **Status Share** | Trimble Connect integration that pushes Tekla PowerFab statuses back to the 3D model as colour. |
| **Submittal** | A package issued from Tekla Structures to Tekla PowerFab via the Connector. *Uploaded* means it reached the server, not that it was received. |
| **Test Import** | A dry run of an import that reports what would happen without committing anything. |
| **TFS** | Taken From Stock. The record of material consumed by a job. |
| **TFS Station** | The station on a route credited automatically when material is taken from stock. Must be the first station in the sequence. |
| **Translate Shapes/Grades** | The dialog that maps unrecognised imported shapes and grades to database entries. Saved mappings reapply silently on every future import. |
| **Transmittal** | Formal document issuing drawings or files to another firm, with a tracked record. |
| **Trimble Identity** | The sign-in account shared by Tekla Structures, PowerFab, and Trimble Connect. A mismatch makes Connector sync report *nothing to sync*. |
| **UDA** | User-Defined Attribute. Custom model information mapped into Tekla PowerFab during import. |
| **Uncombine** | Reverts a combining run to the original parts so the material can be reoptimised. |
| **Work Package** | A group of assemblies released to the shop floor together. |

!!! info "To be completed"
    Add customer-specific terminology and any local naming conventions used in this deployment.

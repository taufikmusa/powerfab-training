# Glossary

Terms used throughout this documentation and in the Tekla PowerFab interface.

| Term | Definition |
|---|---|
| **ABM** | Advance Bill of Materials. The preliminary material list used to place long-lead orders before detailing is finished. |
| **Advance Bill** | The Tekla PowerFab staging area holding material intended for early purchase. |
| **AE** | Automated Events. The module that runs scheduled tasks without a logged-in user, via the Remote Server service. |
| **Bill of Lading** | The shipping document issued with a load and carried by the driver. |
| **CMB** | The Combining module, and the job type it creates. |
| **Combine** | The optimisation that determines how short pieces are cut from longer raw stock with minimum waste. |
| **Critical Difference** | A discrepancy found when comparing the Advance Bill against the final BOM — most often a detailed length exceeding the length ordered. |
| **Cut List** | A defined batch of cutting work assigned to a machine operator for a given shift. |
| **Drop** | The usable remnant left after a cut. Returns to inventory only if a drop location is recorded. |
| **Global Edit** | Bulk-edit function that applies a field change across all selected rows at once. |
| **Heat Number** | The mill batch identifier that provides material traceability. |
| **IFC** | Industry Foundation Classes. Open format for exchanging 3D model data between systems. |
| **JOBSUM** | Report listing all material charged to a specific job via TFS. |
| **KISS** | A text-based material list format supported for import. |
| **Labor Standard** | The time value Tekla PowerFab uses to calculate man-hours for an operation. |
| **Lot** | A grouping of assemblies, typically aligned to erection sequence. |
| **Mult** | The multiple-length combine calculation, used for linear material. |
| **NC File** | Machine-readable instruction file for a saw, drill line, or plasma table. Commonly `.nc1`. |
| **Nest** | The combine calculation used for plate material on sheets. |
| **PDC** | The Production Control module, and the job type it creates. |
| **PFXT** | Tekla PowerFab eXchange transfer file. Carries the material list, drawings, and NC files in one package. |
| **PO** | Purchase Order. The formal commitment issued to a supplier. |
| **PRJ** | The Project Management job type. |
| **Requisition** | An internal material request. Does not order anything until converted to a purchase order. |
| **RFI** | Request For Information. Formal query raised to the engineer or client. |
| **Route** | The defined sequence of stations a piece passes through during fabrication. |
| **Sequence** | A grouping of assemblies aligned to fabrication order. |
| **S/G/S** | Shapes / Grades / Sizes. The global material database read by every module. |
| **SOV** | Schedule of Values. The contract breakdown that invoices are raised against. |
| **Station** | A single work point within a route — Saw, Fit, Weld, Paint, and so on. |
| **Status Share** | Trimble Connect integration that pushes Tekla PowerFab statuses back to the 3D model as colour. |
| **TFS** | Taken From Stock. The record of material consumed by a job. |
| **Transmittal** | Formal document issuing drawings or files to another firm, with a tracked record. |
| **UDA** | User-Defined Attribute. Custom model information mapped into Tekla PowerFab during import. |
| **Work Package** | A group of assemblies released to the shop floor together. |

!!! info "To be completed"
    Add customer-specific terminology and any local naming conventions used in this deployment.

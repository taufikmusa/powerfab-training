# Day 1 — Afternoon Session

- **Focus** — Material libraries and integrations
- **Chapters** — 2.8 – 2.12
- **Modules** — Maintenance, Integration Settings

This session covers the two databases that everything downstream depends on: what material the system knows about, and what that material costs.

---

## 1. Shapes / Grades / Sizes

This is the global material dictionary. It defines how every shape, grade, and size is named and understood across Estimating, Combining, Purchasing, Production Control, and Inventory. There is one copy, and every module reads from it.

**Steps**

1. Navigate to **Maintenance > Shapes/Grades/Sizes**.
2. Activate a deactivated shape — European sections such as HEB are a good example, since they ship inactive in most databases.
3. Add a new shape and give it dimensions.
4. Use **Global Edit** to apply a consistent scrap length across many dimensions at once.
5. Use **Global Edit** again to assign cost codes in bulk.

Emphasise **Global Edit** heavily. Participants who miss it will spend hours editing rows one at a time.

!!! danger "Saved translation maps are the single most dangerous setting in the system"
    When importing an IFC or KISS file, Tekla PowerFab remembers the last **Translate Shapes/Grades** mapping that was saved and reapplies it silently.

    A real incident from a live session: British **UC** and **UB** profiles were silently converted to American **WT** shapes at **A36** grade, because an incorrect mapping had been saved weeks earlier. Nothing failed. No warning appeared. The problem only surfaced days later when a Combining run returned **0% combined and $0.00** — because the profiles that had been imported did not exist in the pricing database.

    The fix was to restore the SEA regional database with correct pre-loaded shapes and engineering properties. Teach participants to *read the mapping window every single time* rather than clicking through it.

---

## 2. Pricing Maintenance

Pricing Maintenance supplies both material prices and available purchasable lengths to Estimating, Purchasing, and Production Control. If a length is not defined here, the combine engine cannot nest into it.

**Steps**

1. Navigate to **Maintenance > Pricing Maintenance**.
2. Create a new supplier by copying an existing one — for example, build an **EST** supplier from the **Stockholder** template. Copying preserves the structure and saves considerable setup time.
3. Use **Global Edit** to define purchasable lengths, such as 6 m through 15 m at 3 m intervals.
4. Use **Global Edit** to set base prices for a shape family such as RHS.

!!! tip "Purchasable lengths drive combining results"
    If the shop can genuinely buy 12 m sections but only 6 m is defined here, every combine run will return a worse yield than reality allows — and the estimator will never know why the numbers look poor.

---

## 3. Integrations and system standards

### 3.1 Company Standards and Job Maintenance

Point out that **Company Standards** and **Job Maintenance** exist under each individual module's own menu rather than in one central location. This trips up new administrators regularly.

### 3.2 Integration Settings

**Steps**

1. Open **Integration Settings**.
2. Configure the **Trimble Connect** connection and assign default users.
3. Map **Trimble Connect Status Share** so that Tekla PowerFab statuses flow back to the 3D model.

!!! tip "Status Share is what makes the model come alive"
    With Status Share mapped correctly, statuses such as *Purchased*, *Fabricated*, and *Painted* colourise the model in Trimble Connect automatically. Project managers and clients can see progress visually without opening Tekla PowerFab at all — this is often the feature that sells the integration internally.

---

## Wrap-up checklist

- [ ] Activated one shape and added one new shape with dimensions
- [ ] Applied a scrap length to multiple dimensions using Global Edit
- [ ] Created a supplier by copying an existing one
- [ ] Defined purchasable lengths and base prices for at least one shape family
- [ ] Confirmed Trimble Connect connects and Status Share is mapped

## Exercise

!!! info "To be completed"
    Add the afternoon exercise steps and supporting screenshots.

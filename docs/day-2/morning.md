# Day 2 — Morning Session

- **Focus** — Estimating setup and manual takeoffs
- **Chapters** — 3.0 – 3.1.3
- **Modules** — Maintenance > Estimating, Estimating

---

## 1. Estimating Maintenance

Before a single estimate can be produced, the system needs to know what the shop is physically capable of and what that capability costs. This configuration lives under **Maintenance > Estimating**.

**Steps**

1. Navigate to **Maintenance > Estimating**.
2. Open **Fabricator Information** and set the maximum saw dimensions, automatic clip-angle behaviour, and shop efficiency factor.
3. Configure **Labor Rates**.
4. Configure **Cleaning Maintenance** — blasting, pickling, and similar processes.
5. Configure **Paint Maintenance**, including at least one complete paint system such as a primer plus topcoat combination.

Explain that the shop efficiency factor is a blunt but powerful lever. Customers frequently want to adjust it after their first few bids, once they can compare estimated hours against actuals.

---

## 2. Manual takeoff entry

**Steps**

1. Open the **Estimating** module.
2. Click **Add** to create a new estimate job.
3. Walk through the Input Fields: Shape, Dimensions, Length, Grade, and Labor Code.
4. Have participants enter around ten items manually.

!!! tip "Do not skip the manual entry"
    Ten minutes of manual takeoff pays for itself in the afternoon. When the IFC import populates hundreds of rows, participants who have typed the fields themselves immediately recognise what they are looking at — and, more importantly, recognise when something looks wrong.

---

## 3. Accessories, assemblies, and parametric assemblies

### 3.1 Accessories

Accessories are standard items the shop uses repeatedly and does not want to re-specify every time.

**Steps**

1. Create a standard item — a web stiffener is a good example.
2. Link the accessory to a specific beam size so it is proposed automatically.

### 3.2 Assemblies

**Steps**

1. Group multiple pieces under a single main mark, such as a roof frame.
2. Save the assembly for reuse.

### 3.3 Parametric assemblies

This is the most powerful feature in the estimating module and the one most customers never discover on their own. Parametric assemblies are ideal for miscellaneous steel, where the same configuration repeats at varying dimensions.

**Steps**

1. Build an assembly using variables and formulas rather than fixed values.
2. Drive the angle size from the centre-to-centre span.
3. Test the assembly at two different spans and confirm the members resize correctly.

!!! tip "Show the payoff"
    Build one parametric handrail or one ladder live, then generate it at three different lengths in about fifteen seconds. This demonstration usually does more to sell the module than any amount of explanation.

---

## Wrap-up checklist

- [ ] Fabricator Information reflects the shop's real saw capacity
- [ ] At least one paint system configured with primer and topcoat
- [ ] Ten items entered manually into a new estimate
- [ ] One accessory created and linked to a beam size
- [ ] One parametric assembly built and tested at two spans

## Exercise

!!! info "To be completed"
    Add the morning exercise steps and supporting screenshots.

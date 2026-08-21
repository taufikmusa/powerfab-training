# Day 2 — Afternoon Session

- **Focus** — Estimodeling, pricing, and labour
- **Chapters** — 3.2 – 3.4
- **Modules** — Estimating, Trimble Connect

---

## 1. Estimodeling — importing a 3D model

Estimodeling brings a 3D model directly into an estimate, replacing hours of manual takeoff with a few minutes of mapping.

**Steps**

1. Go to **File > Import > Estimating > IFC**.
2. Select the IFC file.
3. Work through the **Translate Shapes/Grades** window, mapping source profiles and grades to system equivalents.
4. Confirm the mapping and complete the import.
5. Review the imported model visually through the Trimble Connect integration.

!!! danger "Read the mapping window every time"
    Tekla PowerFab reapplies the last saved translation mapping automatically. If an incorrect mapping was saved previously, the import will succeed, produce no warning, and quietly substitute the wrong profiles and grades throughout the estimate.

    The downstream symptom is a combine run that returns **0% combined and $0.00** — because the substituted profiles do not exist in the pricing database. Nothing in that error points back to the mapping window, which is why this costs teams days when it happens in the field.

---

## 2. Combining and job-specific pricing

**Steps**

1. Run a **Combine** within the estimate using **Mult** and **Nest**.
2. Review the yield and the resulting purchase quantities.
3. Open **Job-Specific Pricing Maintenance** and override a global material price for this bid only.

!!! info "Combining inside an estimate does not reserve stock"
    A combine run at estimate stage is purely a calculation — it works out the most efficient purchase pattern so the bid is priced realistically. It does not touch inventory and does not commit the company to anything. Make this distinction explicit, because participants frequently assume otherwise.

---

## 3. Understanding the labour calculation

Labour is where estimating credibility is won or lost, and it is the part of the module participants find least transparent. Use **Tell, Show, Do** and take the time to make the hierarchy explicit:

**Labor Codes → Labor Groups → Labor Operations → Labor Standards**

**Steps**

1. Select a single line item in the estimate.
2. Open the **Labor Diagnostics** screen for that item.
3. Walk through exactly how Tekla PowerFab arrives at the total man-hours, level by level.
4. Demonstrate a **Manual Override** where an estimator needs to force a specific time.

!!! tip "Labor Diagnostics is the trust-builder"
    Estimators are rightly sceptical of hours they cannot explain. Once they see that every hour traces back through a named operation to a named standard, resistance to the module drops sharply. Spend real time on this screen.

---

## 4. Proposals

**Steps**

1. Open **Proposal Setup** and configure the layout, sections, and branding.
2. Generate a formal bid document suitable to send to a client.
3. Have participants complete the practical exercises at the end of Chapter 3 — creating a parametric assembly and modifying a labour rate are the two most valuable.

---

## Wrap-up checklist

- [ ] IFC model imported with the mapping window reviewed line by line
- [ ] Combine run completed and yield understood
- [ ] One job-specific price override applied
- [ ] Labour traced end to end in Labor Diagnostics for at least one item
- [ ] One proposal generated

## Exercise

!!! info "To be completed"
    Add the afternoon exercise steps and supporting screenshots.

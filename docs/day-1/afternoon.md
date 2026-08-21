# Day 1 — Afternoon Session

- **Topic:** Material libraries and integrations
- **Chapters:** 2.8 thru 2.12

The afternoon covers the two databases that drive estimating and purchasing: the material shapes and the material prices.

## 1. Shapes/Grades/Sizes (Chapter 2.8)

Explain that this is the global database. It controls how the software calls out material in all modules.

1. Go to **Maintenance > Shapes/Grades/Sizes**.
2. Turn on a shape that is off, for example a European beam such as HEB.
3. Add a new shape.
4. Add a dimension to the new shape.
5. Use **Global Edit** to set the same scrap length for many dimensions.
6. Use **Global Edit** to set the cost codes.

!!! danger
    Do not save a wrong shape map or a wrong grade map. A wrong map changes a British UC profile to a US WT profile without an error message. The combine run then gives 0% combined and no cost.

## 2. Pricing Maintenance (Chapter 2.9)

Explain that this module gives the material prices and the purchasable lengths to Estimating, Purchasing and Production Control.

1. Go to **Maintenance > Pricing Maintenance**.
2. Copy an existing supplier to make a new supplier. For example, make an "EST" supplier from the "Stockholder" template.
3. Use **Global Edit** to set the purchasable lengths. For example, set 6 m thru 15 m at 3 m steps.
4. Use **Global Edit** to set the base prices for a shape such as RHS.

## 3. Integrations and system standards (Chapters 2.10 thru 2.12)

### 3.1 Company standards and job maintenance

Show **Company Standards** and **Job Maintenance**. Each module has its own menu for these two screens.

### 3.2 Integration settings

1. Open **Integration Settings**.
2. Set up **Trimble Connect** and give the default users.
3. Map **Trimble Connect Status Share**.

!!! tip
    A correct Status Share map makes the Tekla PowerFab status update the 3D model. The model then shows the "Purchased" status and the "Painted" status in colour.

## Exercise

!!! info "Content to add"
    Add the afternoon exercise steps and the screenshots here.

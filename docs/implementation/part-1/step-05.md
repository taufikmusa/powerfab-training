# Step 5 — Combine partially in the Advance Bill


**Role:** Estimator / Material Planner · **Module:** Advance Bill

**Why this matters**

Steel is not bought piece by piece — it arrives in stock lengths or sheets, and a good material planner groups parts onto the fewest stock lengths possible to minimise waste.

*Partially* is the word that matters. On a real project you lock in only the long-lead or critical items now — the columns — and leave the rest for later, once detailing is further along. Combining everything immediately defeats the point of staged procurement.

**How to do it**

1. With the Advance Bill job open, click the **Advance Bill** ribbon tab and then **Combine**.

    ![Advance Bill ribbon menu open with Combine highlighted, above the job material list](../../assets/images/implementation/impl-step05-01.png)
    <figcaption>Figure 5.1. Combine sits on the Advance Bill ribbon, above Filter and Global Edit.</figcaption>

2. The *Select Combining Run* dialog opens. Choose **Mult (F1)** for linear items such as beams, angles, and columns; **Nest (F2)** for plates and gratings; or **Mult & Nest (F3)** for both.

    ![Select Combining Run dialog with an empty run list and Mult, Nest and Mult and Nest buttons along the bottom](../../assets/images/implementation/impl-step05-02.png)
    <figcaption>Figure 5.2. An empty run list is normal on a first combine. The three buttons choose the calculation type.</figcaption>

3. *Combining Run Filters* opens. In the **Type** list — the left-hand column, not the separate *Filter Types* button — click the row for **Reference #**.
4. Click **Select** on the right. The *Filter* dialog opens.

    ![Combining Run Filters showing the Type list on the left with every filter value reading All, the Select and Find buttons on the right, and MULT F4 at the bottom](../../assets/images/implementation/impl-step05-03.png)
    <figcaption>Figure 5.3. Everything in one frame: the Type list on the left, Select on the right, the Filter Types button that is <em>not</em> the item picker, and MULT (F4) at the bottom. Every row reads All until a filter is applied.</figcaption>

5. Click **`<<`** to clear the Included list, then Ctrl+click the specific items to include — the two columns — in *Not Included*, click **`>`** to move them across, and click **OK**.
6. Confirm the **Reference #** row now shows the chosen items rather than *All*.
7. Click the combine button at the bottom — **MULT (F4)**.
8. *Combining Run Results* opens. Check **% Combined** and **Cost**.

    ![Combining Run Results grid listing combined stock lengths with grade, weight, base price, cost and drop columns, and a summary panel reading 100 percent combined](../../assets/images/implementation/impl-step05-04.png)
    <figcaption>Figure 5.4. A healthy result: 100% combined, a real drop percentage, and real costs. Zeroes here mean the combine failed — see the warning below.</figcaption>

9. Click **Save Displayed Results & Close**, choose **Requisitions**, add a new one, name it, and save.

    ![Prompt asking where to save the ordered pieces, offering Requisitions or Purchase Orders, with an arrow pointing at Save Displayed Results and Close](../../assets/images/implementation/impl-step05-05.png)
    <figcaption>Figure 5.5. Requisitions sends the material out for pricing; Purchase Orders commits immediately. Step 6 explains why the requisition route usually comes first.</figcaption>

    ![Select Requisition dialog listing existing requisitions with an arrow pointing at the Add button](../../assets/images/implementation/impl-step05-06.png)
    <figcaption>Figure 5.6. Add creates a new requisition rather than appending to an existing one.</figcaption>

    ![Requisition Edit window with the requisition number, date and item increment fields](../../assets/images/implementation/impl-step05-07.png)
    <figcaption>Figure 5.7. Name the requisition, then Save (F4).</figcaption>

**You should now have:** the columns combined onto stock lengths, with a real percentage combined and a real cost, and a requisition holding the result.

!!! danger "0% Combined and $0.00 is a failure, not a result"
    The dialog closes cleanly either way. A zero result means Tekla PowerFab has no usable stock-length or pricing data for that exact shape, grade, and size combination — the shape may exist, but there is nothing to combine the material into.

    Check **Shape/Grade/Size Maintenance** and **Pricing Maintenance** before assuming the model data or the filter is wrong. Never proceed on the assumption that it worked because no error appeared.

!!! warning "Four ways this step goes wrong"
    **Forgetting the filter and combining everything.** The most common slip on this exact step — Combine with no filter grabs the whole job.

    **Confusing *Filter Types* with *Select*.** Filter Types manages custom filter categories and is usually empty and irrelevant. The actual item picker is reached by clicking a row in the **Type** list, then **Select**.

    **Not reviewing Optimizations and Supplier settings first.** Combining uses whatever default stock lengths and suppliers are configured.

    **Treating a clean-looking dialog as a successful combine.** Read the summary numbers, not just whether the window closed without complaint.

??? question "Frequently asked questions"
    **What is the difference between Mult and Nest?**

    Mult combines linear items such as beams and angles. Nest combines items with area, such as plates or gratings.

    **Can I undo a combine if I made a mistake?**

    Yes. Use **Uncombine** to revert to the original parts, then reoptimise.

    **Does combining automatically create a purchase order?**

    No. You explicitly choose afterwards whether to send the result to a Requisition for price-shopping, or straight to a Purchase Order.

    **What does 0% Combined and $0.00 Cost actually mean?**

    Tekla PowerFab has no usable stock-length or pricing data for that shape, grade, and size. Check Shape/Grade/Size Maintenance and Pricing Maintenance first.

    **Why would an import map a UK profile such as UC to a US shape such as WT?**

    When an imported shape or grade is not recognised, the *Translate Shapes/Grades* dialog lets you map it to something in PowerFab's database. Once saved, that mapping applies silently to every future import of the same shape. It will not prompt again, even if the mapping was wrong.

    **Is there a faster way to load all the standard UC and UB sizes than typing each one?**

    Yes. Check whether a regional database — a UK or SEA dataset — already includes these shapes with full engineering properties and pricing pre-loaded. Restoring the correct regional database is far faster and more reliable than hand-keying dozens of sizes.

??? note "Field notes — the shape and grade incident, in full"
    Tekla PowerFab 2026, Trimble Malaysia install. This was the richest piece of troubleshooting in the whole exercise and is worth walking through with trainees.

    **What happened.** A first combine attempt on two columns returned **0% Combined / $0.00 Cost**, with both items sitting under *Not Combined*. Investigation traced it to two separate problems.

    1. **Missing pricing and stock-length data.** The shape technically existed in the database but had no available length or price set up for that grade and size, so there was nothing to combine the material into.
    2. **A wrong shape and grade translation, saved previously and applied silently.** The model used genuine British profiles — UC356×406×467, grade S275 — but the IFC import resolved them to WT / A36, a completely different US shape and grade, with 0 errors and 0 warnings on import. Someone had previously run *Translate Shapes/Grades* and mapped UC to WT, and that mapping is saved permanently, so it no longer prompts on later imports. The giveaway was a Shape/Grade/Size Maintenance dimension entry with every engineering property — weight, depth, flange width — sitting at zero.

    **The fix path used.** Maintenance > Shapes/Grades/Sizes, located and deleted the wrong dimension entries, then used **Find Abbreviation** to locate and delete the UC-to-WT alias. Browsing by Material Group wasted time here — UC belongs under *Beams*, not *Tubes*. Proper UC and UB shapes were then created via **Shape Maintenance**, a distinct ribbon-menu dialog and not the same as the browse-only Shape/Grade/Size Maintenance window, using **New Shape** based on the closest existing relative (W, Wideflange Beams).

    **The cleanest fix, in the end.** Restoring the correct SEA regional database rather than hand-building shapes. It already contained UC (31 dimensions, 3 grades) and UB (80 dimensions, 3 grades) fully populated with real engineering and pricing data. A re-import after the restore resolved UC / S275 correctly on the first pass, with no manual translation needed.

    **Result after the fix.** 100% Combined, 0% Drop, real cost (£11,007.49) — confirming shape, grade, and pricing were finally aligned.

    **Takeaway for training.** If a combine returns 0% / $0.00, do not assume the model or the filter is wrong. Check Shape/Grade/Size Maintenance and Pricing Maintenance first. And if a shape or grade looks suspicious on import, check whether it has been silently auto-translated before — that will not raise a warning.

---

Next: [Step 6 — Send to requisition and purchasing](step-06.md)

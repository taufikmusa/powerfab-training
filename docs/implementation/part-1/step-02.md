# Step 2 — Create a project schedule


**Role:** Project Manager · **Module:** Project Management

**Why this matters**

A schedule records when things are supposed to happen, and then updates itself as real work gets done elsewhere in Tekla PowerFab. Drawing approvals, material purchases, fabrication, and shipping all move the progress bars automatically through **Status Links**. Without a schedule, the team is back to editing a spreadsheet by hand every time anything changes.

**How to do it**

## Part A — Build a reusable schedule template

1. Go to **Maintenance > Project Management > Schedule Templates**.
2. Click **New Template (F1)** and name it — `Training-Schedule-Template` for this exercise.
3. Click **New Task** and add tasks one at a time: Detailing, Fabrication, Shipping, Installation.
4. For each task, tick **Sequence** and **Lot #** under *Apply Project Breakdown*.
5. Set a **Status Link** tied to a real tracked event — Detailing to *Drawings Approved* (By Quantity), Fabrication to *Production Completed*, Shipping to *Shipping Completed*.
6. Click **Add (F4)** to save each task, then **Save Template (F4)** once every task is listed.

    ![Schedule Templates dialog with four template tasks listed and the Maintenance menu open at Project Management > Schedule Templates](../../assets/images/implementation/impl-step02-01.png)
    <figcaption>Figure 2.1. The finished template, with the menu path that reaches it still open on the left. Note Installation's Status Link — it reads [None], because no Installation event exists to link to.</figcaption>

## Part B — Apply the template to the job

1. Open the job and click **Project Schedule**.
2. Go to the **Schedule Tasks** tab and click **Apply Template** — once, and only once. Select the template and click **OK**.

    ![Schedule Tasks menu open with Apply Template highlighted above the Project Schedule window](../../assets/images/implementation/impl-step02-02.png)
    <figcaption>Figure 2.2. Apply Template sits on the Schedule Tasks menu, above Save as Template.</figcaption>

    ![Enter Value dialog prompting to select a schedule template from a dropdown](../../assets/images/implementation/impl-step02-03.png)
    <figcaption>Figure 2.3. Choose the template, then OK.</figcaption>

3. Confirm exactly the expected number of tasks appears — four, not eight. If they duplicated, select the extra rows and click **Delete (F2)**.

    ![Schedule Tasks window listing Detailing, Fabrication, Shipping and Installation, with the task detail pane showing Detailing linked to Drawings Approved](../../assets/images/implementation/impl-step02-04.png)
    <figcaption>Figure 2.4. Four tasks, applied once. Eight rows here means Apply Template was clicked twice.</figcaption>

## Part C — Build the project breakdown

1. Go to the **Project Breakdown** tab and click **New**.
2. Enter a **Sequence** number and **Description** — *Area A*, for example.
3. Click the **Apply to Tasks** tab and tick **All**.

    ![Schedule Breakdown Item dialog with Sequence and Description filled in, the Apply to Tasks tab open and All ticked](../../assets/images/implementation/impl-step02-05.png)
    <figcaption>Figure 2.5. Sequence and Description on the breakdown item, with Apply to Tasks &gt; All ticked.</figcaption>

4. Click **Save (F4)**, or **Add (F4)** for a brand-new item.
5. Click **New (F1)** again and repeat for each additional sequence.

    ![Project Breakdown tab listing two sequences, with the breakdown item dialog open and arrows pointing at New and Save](../../assets/images/implementation/impl-step02-06.png)
    <figcaption>Figure 2.6. A second sequence added. The Link column reading None is expected — it shows predecessor chaining, not whether Apply to Tasks worked.</figcaption>

## Part D — Adjust dates and set the baseline

1. Go to the **Gantt Chart** tab and confirm **Edit Mode** is active.

    ![Confirmation dialog reading Enter edit mode? with Yes and No buttons](../../assets/images/implementation/impl-step02-07.png)
    <figcaption>Figure 2.7. The edit-mode prompt, which appears across the schedule screens. Edit mode drops out again after 180 seconds.</figcaption>

2. Click the date cells, or drag the blue duration bars, to stagger the tasks sequentially.
3. Check the top-level project **Duration** after every change.

    ![Gantt Chart tab in Edit Mode showing tasks and sequences staggered across a date grid, with a Duration column](../../assets/images/implementation/impl-step02-08.png)
    <figcaption>Figure 2.8. Tasks staggered in Edit Mode. The top row's Duration — 145 days here — is the number to sanity-check after every date edit.</figcaption>

4. Click **Save (F4)**.
5. Go to the **Baseline Plan** tab and click **Set Baseline > Yes**.

    ![Baseline Plan tab with the Set Baseline button and a confirmation dialog asking whether to set the baseline values](../../assets/images/implementation/impl-step02-09.png)
    <figcaption>Figure 2.9. Setting the baseline. Until this is done, planned-versus-actual variance cannot be tracked.</figcaption>

**You should now have:** a baselined programme the rest of the project can be measured against.

!!! info "There is no Installation or Erection Status Link in PowerFab 2026"
    Confirmed against live Trimble documentation. These are the only system Status Links available:

    | Status Link | Typically used for |
    |---|---|
    | Drawings Approved | Detailing |
    | Material Purchased | Procurement |
    | Material Received | Receiving |
    | TFS | Material taken from stock |
    | Production Progress | Fabrication |
    | Production Completed | Fabrication |
    | Station Progress | Fabrication |
    | Shipping Destination Progress | Shipping |
    | Shipping Completed | Shipping |

    For a task with no matching event — Installation is the usual case — set **Status Link = [None]** and **Status Summary Method = No Factor**. Do not force-reuse an unrelated link to make the field look populated.

!!! warning "Three things that catch people out"
    **The Gantt edit mode times out after 180 seconds.** If date cells stop responding, check whether the button now reads *Enter Edit Mode* again — click it to resume.

    **A mistyped date will not be questioned.** One wrong month inflated a test schedule from roughly 20 days to 73 before it was noticed. Sanity-check the top-level Duration after every date change.

    **Clicking Apply Template twice duplicates every task**, silently — eight rows instead of four. Check the row count in Schedule Tasks before moving on.

!!! danger "Sequence and lot names must match Production Control exactly"
    The names entered here — *Area A*, *Area B* — have to be typed identically later in Production Control. If they differ by so much as a space, the link fails silently and progress sits at 0% with no error.

??? question "Frequently asked questions"
    **Can I edit the schedule after applying the template?**

    Yes. The template is only a starting point — every task, date, and link is fully editable per job afterwards.

    **Does the schedule update itself in real time?**

    No. Someone clicks **Update Status** to pull the latest percentage complete from drawing approvals, purchasing, and piece tracking. It is refresh-on-demand, not live.

    **Why is my Fabrication task still stuck at 0%?**

    The Status Link only moves when the tracked event actually fires. For Station Progress, that means someone on the shop floor logging piece tracking entries in PowerFab Office or Go.

    **Can we have different templates for large and small projects?**

    Yes. A simple job might need four tasks; a complex one might split Purchase, Receive, and Process Material into separate line items.

    **What if we do not track sequences and lots at all?**

    Tick the boxes in the template anyway. Breakdown tracking cannot easily be retrofitted onto an existing template later.

??? note "Field notes — from the live test run"
    Tekla PowerFab 2026, Trimble Malaysia install.

    - Ticking **Apply to Tasks > All** is not enough on its own — **Save** (or **Add**) must also be clicked for it to commit.
    - The **Link** column in Project Breakdown shows predecessor and successor links between breakdown items, *not* whether Apply to Tasks succeeded. Seeing *None* there is expected when no predecessor chaining was configured. It is not an error.
    - A single mistyped month inflated the test schedule from roughly 20 days to 73 days before being caught.
    - Clicking **Apply Template** a second time on the same job silently produced eight rows instead of four — Detailing, Fabrication, Shipping, Installation, twice over.

---

Next: [Step 3 — Model in Tekla Structures, assign preliminary marks, and export](step-03.md)

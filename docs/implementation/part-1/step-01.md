# Step 1 — Create a Project Management job


**Role:** Project Manager · **Module:** Project Management

**Why this matters**

Every structure needs a single container in the management system before anything else can attach to it. The Project Management job is what contacts, drawings, schedules, RFIs, and submittals all hang from. Skip it and Tekla PowerFab will force you to create one later anyway, when the Production Control import demands it — except it will be disconnected from whatever planning has already been done.

**How to do it**

1. Open Tekla PowerFab and click the **Project Management** button on the main toolbar. The *Select Project Management Job* dialog opens.

    ![Tekla PowerFab start screen with the Project Management module being opened](../../assets/images/implementation/impl-step01-01.png)
    <figcaption>Figure 1.1. Opening the Project Management module.</figcaption>

2. Click **Add (F1)** at the bottom of the window.

    ![Project Management job list with the Add button at the bottom left](../../assets/images/implementation/impl-step01-02.png)
    <figcaption>Figure 1.2. The job list — Add (F1) sits at the bottom left of the window.</figcaption>

3. Enter a **Job #** — use `TRN-001` for this exercise.
4. Complete **Description** and **Location**.
5. Optionally complete **Customer PO #** and **Job Group**.
6. Leave **Job Status** as *Open*.
7. Click **Save**.

    ![New job entry window with Job Number and Description fields completed](../../assets/images/implementation/impl-step01-03.png)
    <figcaption>Figure 1.3. Job details — Job # is the field that matters most, because it cannot be changed later.</figcaption>

**You should now have:** an empty PRJ job that everything else in this exercise will link back to.

!!! danger "The Job # is permanently locked once saved"
    There is no rename. A typo means abandoning the job and creating a replacement, and any work already attached to it goes with it.

    Agree the numbering convention with the customer before training day, not during it.

!!! warning "Do not start with the material import"
    The instinct is to jump straight to Advance Bill or Production Control. Doing so loses the ability to link drawings, RFIs, and schedule status properly — and Tekla PowerFab will force-create a disconnected Project Management job later regardless.

??? question "Frequently asked questions"
    **Can the Job # be changed after saving?**

    No. It is permanently locked. Plan the numbering convention with the client before training day.

    **What is the difference between Job Status *Open* and *Closed*?**

    Open jobs stay visible in the active job list. Closed jobs are hidden from the default view — not deleted — which is useful once a project wraps.

    **Is the ERP Job # field required?**

    Only if the customer exports data to an accounting system such as Trimble Viewpoint. Otherwise leave it blank.

??? note "Field notes — from the live test run"
    Tekla PowerFab 2026, Trimble Malaysia install.

    - Job creation was smooth in testing — no issues encountered.
    - Fill in **Description** and **Location** immediately on a real customer job. An unlabelled job list becomes very hard to search once a company has hundreds of jobs.

---

Next: [Step 2 — Create a project schedule](step-02.md)

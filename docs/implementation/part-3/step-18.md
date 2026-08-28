# Step 18 — Create a load and ship


**Role:** Shipping / Logistics Coordinator · **Module:** Production Control (Load Tracking)

**Why this matters**

Load Tracking manages what physically goes on a truck, to where, and when. It generates the paperwork the driver needs — shipping ticket, bill of lading — and keeps an accurate record of what has left the shop versus what is still on site.

**How to do it**

1. Go to **Production Control** ribbon tab **> Load Tracking**. The *Loads* dialog opens.
2. Click **New Load**.
3. In *Load Properties*, set **From** (Shop), **Destination Group** (Jobsite), **Load #**, **Trailer #**, **Haulage Company**, and **Capacity / Max Length** if relevant.
4. Click **Save**.
5. In *Load Properties - Not Shipped*, click **Add Material**.
6. Move the items for this load into the *Included* list, adjust quantities if needed, and click **Add Material** to confirm.
7. When ready to physically ship, click **Ship** and set **Date Shipped** — and **Date Received** once delivered.
8. Click **Shipping Ticket** to generate the driver's paperwork. Choose a report — *Shipping Ticket - Delivery Copy*, for example — click **View** to confirm, then **Print** or **Export** as needed.
9. Save and close.

<!-- SCREENSHOTS — Step 18
     Drop files into docs/assets/images/implementation/ named:
       impl-step18-01.png, impl-step18-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../../assets/images/implementation/impl-step18-01.png)
    <figcaption>Figure 18.1. Caption text.</figcaption>
-->

**You should now have:** a shipped load, a printed shipping ticket or bill of lading for the driver, and a complete delivery record against the job.

!!! warning "Office will not stop an incomplete load from shipping"
    Tekla PowerFab 2026 blocks loading an item in **PowerFab Go** until every station on its assigned route shows complete. Desktop **Office** Load Tracking does not currently enforce the same gate.

    Confirmed during this session by shipping a load from Office with several stations still incomplete and no warning shown. An office user can therefore ship steel the shop has not finished. Where this matters, the control has to come from process discipline or from routing shipping through Go — Office will not prevent it.

??? question "Frequently asked questions"
    **Can I ship an item that has not completed every station on its route?**

    In PowerFab Go (2026), no — all stations must be complete first. In PowerFab Office, the desktop Load Tracking dialog currently allows it with no warning, so this is a behaviour gap worth confirming against each customer's process.

    **What is the difference between the shipping ticket and the bill of lading?**

    Both are produced from the **Shipping Ticket** button by choosing a different report. The shipping ticket is the delivery record; the bill of lading is the carrier document that travels with the driver.

    **What does Destination Group do?**

    It groups destinations — jobsite, galvaniser, third-party processor — so loads can be routed and reported by where they are going, not just by individual address.

??? note "Field notes — from the live test run"
    Tekla PowerFab 2026, Trimble Malaysia install.

    - A load was shipped from PowerFab Office on `TRN-001` with Cut/Saw, Layout/Weld, and Quality Control all showing incomplete stations, with no warning from the desktop client. The 2026 Go shipping gate does not apply to Office.

---

That completes the workflow. Use the [Practice Checklist](../practice-checklist.md) for a second hands-on run.

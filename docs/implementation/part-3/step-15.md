# Step 15 — Create a cut list


**Role:** Production Control Coordinator, working with the workshop cutting team · **Module:** Production Control

**Why this matters**

A cut list tells the shop exactly how each bar or sheet of received material should be cut to produce the parts on the job — the bridge between *we have steel in stock* and *we are cutting specific pieces today*. A saw operator cannot work from a full project BOM.

**How to do it**

1. Go to **Production Control** ribbon tab **> Review > Cut Lists**.
2. Click **New Cut List**.
3. In the *Purchasing Report Filters* dialog, leave the filters at the default (All) for a first cut list, or narrow by Shape or Category for separate cut lists per material type.
4. Click **Make Report**.
5. In *Report Selection*, choose a cutting list report — *PC/PO Cutting List*, for example — and click **View** to preview it.
6. Confirm the items, lengths, and quantities look correct, then close the preview.
7. Click **Save Cut List**.
8. Enter a **Cut List Description** and **Date Required**, and tick **Share Cut List** and **Lock Cut List** as appropriate.
9. Click **Save To Cut List**, then **OK** to confirm.

<!-- SCREENSHOTS — Step 15
     Drop files into docs/assets/images/implementation/ named:
       impl-step15-01.png, impl-step15-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../../assets/images/implementation/impl-step15-01.png)
    <figcaption>Figure 15.1. Caption text.</figcaption>
-->

**You should now have:** a named, saved cut list ready to be processed.

!!! danger "Requisitioned material is silently excluded"
    A cut list can only be built from material that is on a **purchase order** or **already in stock**. Material still sitting on a requisition is not eligible.

    Tekla PowerFab does not throw an error. It simply leaves those rows out, which looks like a bug if you are not expecting it. This is the payoff for Steps 6, 12, and 13 — anything left unconverted or unreceived quietly fails to appear here.

!!! warning "Two menus both say Cut List"
    **Dashboards > Cut List Management** launches the PowerFab Go shop-floor dashboard — a different product surface entirely.

    **Production Control > Review > Cut Lists** is the desktop authoring screen used above. It is easy to click the wrong one.

??? question "Frequently asked questions"
    **Why can I not create a cut list for items I already combined and sent to a requisition?**

    A cut list can only be built from material linked to a purchase order or already in stock. Requisitioned-only material has not yet been purchased or received, so it is outside the cut list's eligible scope by design.

    **Should I build one cut list or several?**

    Either works. Leave the filters at All for a first pass, or narrow by Shape or Category to produce separate cut lists per material type — which is usually what a shop with multiple machines wants.

    **What do Share Cut List and Lock Cut List do?**

    Share makes the list visible beyond its creator; Lock prevents further edits. Set them according to how the shop wants the list controlled.

??? note "Field notes — from the live test run"
    Tekla PowerFab 2026, Trimble Malaysia install.

    - `TRN-001`'s UC columns, sitting on requisition `RQ-001`, never appeared in the cut list because they had not yet been converted to a purchase order and received. No error was shown — just missing rows.
    - Both *Cut List* menu entries were clicked during the session before the right one was found. Worth calling out explicitly to trainees.

---

Next: [Step 16 — Process the cut list](step-16.md)

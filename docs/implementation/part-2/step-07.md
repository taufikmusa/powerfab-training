# Step 7 — Complete the connections in Tekla Structures


**Role:** Steel Detailer / BIM Modeller · **Software:** Tekla Structures

**Why this matters**

Material has at least been requisitioned off the preliminary model, so the detailer now has a window to finish the real engineering — bolts, plates, welds — and move from preliminary marks to final assembly marks. This is deliberate parallel working: two long-duration activities running at the same time instead of one after the other. It is also the point where the model shifts from advance procurement data to production-ready data.

**How to do it**

1. Open the Tekla Structures model.
2. Select the members to be connected, then open **AutoConnection**.
3. On the **Rule groups** tab, set **Choose predefined rule group for connection selection** to the joint type the exercise uses — **End_Plate** — and set **Choose predefined rule group for connection parameters selection** to **Green Book 1**.
4. Click **Create connections**.

    ![Tekla Structures AutoConnection dialog on the Rule groups tab, with End_Plate chosen for connection selection and Green Book 1 for connection parameters, alongside the three-bay training frame](../../assets/images/implementation/impl-step07-01.png)
    <figcaption>Figure 7.1. The two dropdowns do different jobs. The upper one decides <em>which</em> connection is applied; the lower one decides <em>how</em> it is sized — bolt grade, plate thickness, edge distances. Setting the first and leaving the second on the wrong parameter group produces the right joint built to the wrong standard.</figcaption>

5. Reassign final assembly marks where needed, replacing the preliminary marks used in Step 3.
6. Check for case-colliding part marks before going any further — see the warning below.
7. Run a clash check and resolve any conflicts, particularly bolt clashes.
8. Save and update the model.

**You should now have:** a fully detailed model carrying final assembly marks, ready for drawing production.

!!! danger "Check for case-only mark collisions now, not later"
    An auto-generated clip plate marked `m1` sitting alongside an existing `M1` looks harmless in the model. It causes a real, invisible problem two steps later: Windows filenames are not case-sensitive, so both marks write to the same `.nc1` filename and one silently overwrites the other.

    Build the habit of checking for case-only collisions right after adding connections, rather than discovering it via a cryptic import warning at Step 10.

!!! warning "Review the joint types, do not just blanket-apply"
    Auto-connections everywhere is fine for a training exercise. A real project needs the right connection type per joint, not a default applied across the board — and AutoConnection applies one rule group to everything currently selected, so a wide selection is how a beam-to-column joint ends up detailed as a beam-to-beam one.

??? question "Frequently asked questions"
    **Why wait until now to add connections — why not from the start?**

    Advance procurement, Steps 3 to 6, needs material data before detailing is fully finished. Locking in connections too early risks re-detailing work if quantities or specifications change after the initial order review.

    **Does adding connections change my existing Advance Bill data?**

    No. The Advance Bill is already locked in from Steps 4 to 6. New connection material — clips, bolts — is captured fresh during the Production Control import at Step 10, since it was not part of the original advance list.

    **What if I used auto-connections but need to customise a joint later?**

    That is fine. Auto-connections can be individually edited or overridden afterwards; nothing is locked in.

??? note "Field notes — from the live test run"
    Tekla PowerFab 2026, Trimble Malaysia install.

    - Adding auto-connections went smoothly at this stage — no errors during modelling itself. The run used the **End_Plate** rule group with **Green Book 1** parameters.
    - The real complication from this step did not surface until Step 10's import: a case-colliding part mark (`M1` versus `m1`) created here caused one NC file to silently overwrite the other on disk.

---

Next: [Step 8 — Create drawings and export NC files](step-08.md)

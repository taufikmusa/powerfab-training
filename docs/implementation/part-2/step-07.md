# Step 7 — Complete the connections in Tekla Structures


**Role:** Steel Detailer / BIM Modeller · **Software:** Tekla Structures

**Why this matters**

Material has at least been requisitioned off the preliminary model, so the detailer now has a window to finish the real engineering — bolts, plates, welds — and move from preliminary marks to final assembly marks. This is deliberate parallel working: two long-duration activities running at the same time instead of one after the other. It is also the point where the model shifts from advance procurement data to production-ready data.

**How to do it**

1. Open the Tekla Structures model.
2. Add connections to the members. Auto-connections such as fin plates are fine for a practice run.
3. Reassign final assembly marks where needed, replacing the preliminary marks used in Step 3.
4. Check for case-colliding part marks before going any further — see the warning below.
5. Run a clash check and resolve any conflicts, particularly bolt clashes.
6. Save and update the model.

<!-- SCREENSHOTS — Step 7
     Drop files into docs/assets/images/implementation/ named:
       impl-step07-01.png, impl-step07-02.png, ...
     Then delete this comment wrapper and indent each block 4 spaces
     under the numbered step it belongs to.

    ![Describe what the screenshot shows](../../assets/images/implementation/impl-step07-01.png)
    <figcaption>Figure 7.1. Caption text.</figcaption>
-->

**You should now have:** a fully detailed model carrying final assembly marks, ready for drawing production.

!!! danger "Check for case-only mark collisions now, not later"
    An auto-generated clip plate marked `m1` sitting alongside an existing `M1` looks harmless in the model. It causes a real, invisible problem two steps later: Windows filenames are not case-sensitive, so both marks write to the same `.nc1` filename and one silently overwrites the other.

    Build the habit of checking for case-only collisions right after adding connections, rather than discovering it via a cryptic import warning at Step 10.

!!! warning "Review the joint types, do not just blanket-apply"
    Auto-connections everywhere is fine for a training exercise. A real project needs the right connection type per joint, not a default applied across the board.

??? question "Frequently asked questions"
    **Why wait until now to add connections — why not from the start?**

    Advance procurement, Steps 3 to 6, needs material data before detailing is fully finished. Locking in connections too early risks re-detailing work if quantities or specifications change after the initial order review.

    **Does adding connections change my existing Advance Bill data?**

    No. The Advance Bill is already locked in from Steps 4 to 6. New connection material — clips, bolts — is captured fresh during the Production Control import at Step 10, since it was not part of the original advance list.

    **What if I used auto-connections but need to customise a joint later?**

    That is fine. Auto-connections can be individually edited or overridden afterwards; nothing is locked in.

??? note "Field notes — from the live test run"
    Tekla PowerFab 2026, Trimble Malaysia install.

    - Adding auto-connections (fin plates) went smoothly at this stage — no errors during modelling itself.
    - The real complication from this step did not surface until Step 10's import: a case-colliding part mark (`M1` versus `m1`) created here caused one NC file to silently overwrite the other on disk.

---

Next: [Step 8 — Create drawings and export NC files](step-08.md)

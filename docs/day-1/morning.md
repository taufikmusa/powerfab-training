# Day 1 — Morning Session

- **Focus** — System navigation and basic administration
- **Chapters** — 1.0 – 2.7
- **Modules** — Administration

---

## 1. Tekla PowerFab overview

### 1.1 Understanding the project workflow

Before opening a single screen, walk participants through the shape of the whole system. Tekla PowerFab is not a collection of independent tools — it is one continuous pipeline, and understanding that pipeline is what makes the individual modules make sense.

The flow runs like this: an **estimate** is prepared and won, which becomes a **project**. Material moves through **combining** and **purchasing**. The detailed model arrives in **Production Control**, which drives the shop floor and ultimately shipping.

Draw this on a whiteboard and leave it up for the whole week. Participants will refer back to it constantly.

### 1.2 Screen layout and orientation

**Steps**

1. Introduce the menu bar: **File**, **Maintenance**, **About**, **Windows**.
2. Point out the three working areas — the Navigation Tree on the left, the Display Field in the centre, and the Input Field below it.
3. Open a sample job so participants can see how the Display Field repopulates as selection changes.

### 1.3 Customising the grid

Grids in Tekla PowerFab are highly configurable, and a well-configured grid is the difference between a usable screen and an overwhelming one.

**Steps**

1. Right-click anywhere in the display area.
2. Select **Customize Grid**.
3. Add the columns relevant to the participant's role and remove everything else.

!!! tip "Save a grid layout per role"
    An estimator and a shop foreman need entirely different columns. Configure and save one layout for each role rather than trying to build a single grid that serves everyone — new users are far more productive on a short, relevant grid.

---

## 2. Basic administration

!!! info "Kick Start Meeting overlap"
    Chapters 2.1 – 2.7 are normally covered remotely in the Kick Start Meeting held before the on-site training. Ask participants what they have already completed, then review these topics at pace rather than teaching them from scratch. Do not skip them entirely — retention from the remote session is usually partial.

### 2.1 Users and permissions

**Steps**

1. Go to **File > Administration**.
2. Create a user account and assign a password.
3. Set the desktop permissions appropriate to the role.
4. Set the **remote permissions**, which control access to Tekla PowerFab Go.

!!! warning "Remote permissions are separate"
    Desktop permissions and remote permissions are configured independently. A user with full desktop rights and no remote permissions simply cannot log in to PowerFab Go — the login fails with no useful explanation. Set remote permissions now for every shop floor user, or Day 4 will stall.

### 2.2 Company information and cost setup

**Steps**

1. Open **Company Information** and upload the logo that will appear on reports.
2. Configure **Cost Maintenance** — cost codes and cost types.
3. Set the currency.
4. Configure tax rates and tax groups.

Explain that cost codes entered here become the reporting backbone. Retrofitting a cost code structure after six months of live jobs is painful, so it is worth getting the customer's finance team involved in this decision early.

### 2.3 Address Book

**Steps**

1. Open the **Address Book**.
2. Add a firm, then add contacts beneath it.
3. Set the **Firm Type** — Subcontractor, Supplier, Client, Detailer, and so on.

!!! tip "Firm Type controls visibility downstream"
    The Firm Type determines which dropdowns a firm appears in across the rest of the system. A supplier saved with the wrong Firm Type will be invisible when someone tries to raise a purchase order against it, and the cause is rarely obvious to the person hitting the problem.

---

## Wrap-up checklist

Before breaking for lunch, confirm every participant has:

- [ ] Logged in with their own named account
- [ ] Customised at least one grid and saved the layout
- [ ] Created a test user with both desktop and remote permissions
- [ ] Added one firm and one contact to the Address Book with the correct Firm Type

## Exercise

!!! info "To be completed"
    Add the morning exercise steps and supporting screenshots.

# Day 5 — Morning Session

- **Focus** — Inventory control and documentation
- **Chapter** — 8
- **Modules** — Inventory

---

## 1. Inventory and Inventory History

These two screens answer different questions, and confusing them is the most common inventory support call.

| Screen | Question it answers |
|---|---|
| **Inventory** | What material do we physically have, and what is reserved against jobs? |
| **Inventory History** | What material has already been consumed, and which job consumed it? |

Material consumed by a job is recorded as **Taken From Stock (TFS)**.

**Key reports**

1. **AUDIT** — used for physical stock counts. Print it, walk the yard, reconcile.
2. **JOBSUM** — shows everything charged to a specific job via TFS. This is the report accounts will ask for.

---

## 2. Valuation

Inventory valuation matters to finance far more than to the shop, so pitch this section at the accounting and management participants.

**Steps**

1. Run a valuation **By Date/Time** for a precise point-in-time figure.
2. Run a valuation **By Date** for a standard end-of-day position.
3. Run a valuation **By Archive** for a fast historical snapshot.

!!! tip "By Archive is the month-end workhorse"
    Archived valuations return quickly and do not depend on recalculating live transactions, which makes them the practical choice for routine month-end reporting.

---

## 3. Heat documents and manual combining

### 3.1 Heat documents

Material occasionally arrives without its mill certification, or the certificate arrives separately days later. Tekla PowerFab provides a way to catch and correct this.

**Steps**

1. Run **Check Heat Documents** to identify material with missing certification.
2. Attach the PDF certificate.
3. Link the document to the correct heat number in Inventory.

!!! warning "Traceability gaps surface at the worst possible time"
    Missing heat documentation is usually discovered during a client audit or a handover package review, long after the material has been fabricated and installed. Running **Check Heat Documents** as a weekly routine catches it while the supplier can still be asked for the paperwork.

### 3.2 Manual Combine Mode

**Steps**

1. Switch to **Manual Combine Mode**.
2. Remove an item from a combined length.
3. Add it back and observe the recalculation.

!!! info "Use sparingly"
    Standard requisition combining is correct for the overwhelming majority of jobs. Manual mode exists for the genuine exceptions — an odd remnant the yard wants used, or a supplier constraint the system does not know about. It is not a general-purpose editing tool.

---

## Wrap-up checklist

- [ ] AUDIT and JOBSUM reports both run and interpreted
- [ ] All three valuation types produced
- [ ] One missing heat document identified, attached, and linked
- [ ] Manual Combine Mode used to remove and restore an item

## Exercise

!!! info "To be completed"
    Add the morning exercise steps and supporting screenshots.

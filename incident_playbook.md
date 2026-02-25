# SAP MM – Incident Playbook

This document contains practical SAP MM operational support cases based on real-life integration and warehouse-driven environments.

The focus is on structured investigation, root cause identification, and preventive thinking.

---

## Case 1: IDoc Status 51 – Unit of Measure Mismatch

### Problem

Goods Receipt posted in WMS system.  
IDoc received in SAP but stuck in **status 51**.

Warehouse reports stock not visible in SAP.

---

### Investigation

1. Checked IDoc in **WE02**
2. Error message: *Unit of measure not defined for material*
3. Verified material master in **MM03**
4. Compared WMS UoM with SAP base UoM
5. Confirmed mismatch in alternative unit configuration

---

### Root Cause

Material master missing correct alternative Unit of Measure mapping.

---

### Resolution

- Extended UoM configuration in material master
- Reprocessed IDoc using **BD87**
- Validated stock update in **MMBE**

---

### Prevention

- Align UoM mapping between WMS and SAP
- Add validation check during material master creation
- Improve integration testing for new materials

---

## Case 2: Posting Period Blocked During Goods Issue

### Problem

Warehouse unable to post Goods Issue (movement 261).  
Error: *Posting only possible in periods XX/XXXX and XX/XXXX*

Production blocked.

---

### Investigation

1. Verified posting period in **MMPV**
2. Checked current open MM period
3. Confirmed FI period alignment
4. Validated document date vs posting date

---

### Root Cause

MM posting period not opened for current month after month-end closing.

---

### Resolution

- Coordinated with finance team
- Opened correct posting period
- Reprocessed blocked goods issue

---

### Prevention

- Align MM and FI closing calendars
- Add checklist for period opening after month-end
- Improve cross-team communication

---

## Case 3: Stock Mismatch Between SAP and Physical Inventory

### Problem

Warehouse reports 120 units physically available.  
SAP shows 98 units.

---

### Investigation

1. Checked recent goods movements in **MB51**
2. Verified transfer postings (movement 311)
3. Checked for blocked stock
4. Reviewed open deliveries
5. Verified IDoc queue status

---

### Root Cause

Transfer posting created but not confirmed properly in WMS.

---

### Resolution

- Corrected stock via inventory adjustment (MI10)
- Confirmed correct movement replication
- Validated stock reconciliation

---

### Prevention

- Improve monitoring of transfer postings
- Add daily reconciliation report
- Enhance WMS confirmation validation

---

This playbook reflects operational MM support mindset focused on:

- Business continuity
- Technical validation
- Cross-team collaboration
- Preventive improvement
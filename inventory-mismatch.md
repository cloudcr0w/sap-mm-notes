# Inventory Mismatch – SAP MM vs WMS

## Scenario
Physical stock in the warehouse does not match SAP MM stock levels.
WMS shows correct quantity, but SAP stock is lower or higher.

---

## Possible Causes
- Missing or failed IDoc from WMS
- Goods movement posted in WMS but not confirmed in SAP
- Incorrect movement type mapping
- Unit of measure inconsistency
- Posting to wrong storage location

---

## Investigation Steps

1. Verify physical stock with warehouse team
2. Check stock in SAP (MMBE / MB52)
3. Analyze recent material documents (MB51)
4. Check IDoc status (WE02 / WE05)
5. Identify failed or stuck IDocs
6. Validate movement type and storage location

---

## Resolution

- Reprocess IDoc via BD87
- Manually post corrective movement if approved
- Align UoM and master data if required
- Confirm stock consistency with business

---

## Prevention / Lessons Learned
- Regular IDoc monitoring
- Clear communication between SAP and WMS teams
- Documented recovery procedures

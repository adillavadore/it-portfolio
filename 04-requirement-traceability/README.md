
# Requirements Traceability Matrix (RTM)
## Sales Activity Tracking System

**Document Version:** 1.0  
**Project:** Sales Activity Tracking System  
**Document Owner:** Business Analyst  
**Status:** Draft

---

## 1. Purpose

The Requirements Traceability Matrix (RTM) establishes the relationship between business requirements, functional requirements, and test scenarios.

The purpose is to ensure that every approved business requirement is translated into system functionality and can be verified through testing.

## 2. Requirement Traceability Matrix

| BRD ID | Business Requirement | FRS ID | Functional Requirement | Test Scenario |
|---|---|---|---|---|
| BR-001 | Customer visit planning | FR-035, FR-036 | Monthly Calendar and Create Visit Schedule | Verify Account Manager can create a visit schedule |
| BR-002 | Calendar-based scheduling | FR-035 | Monthly Visit Calendar | Verify schedules appear on the correct date |
| BR-003 | GPS-based visit validation | FR-042–FR-046 | GPS Check-in, Check-out and Radius Validation | Verify GPS location and radius validation |
| BR-004 | Visit result recording | FR-048, FR-049 | Record Visit Outcome and Notes | Verify visit results can be recorded |
| BR-005 | Customer follow-up tracking | FR-050, FR-052 | Create and Update Follow-up Activity | Verify follow-up creation and status updates |
| BR-006 | Centralized customer information | FR-028, FR-029 | View Customer List and Details | Verify customer information availability |
| BR-007 | Customer status monitoring | FR-032, FR-057 | Customer Status Management and Monitoring | Verify customer status display |
| BR-008 | Sales activity monitoring | FR-054–FR-061 | Sales Manager Dashboard | Verify sales activity monitoring |
| BR-009 | Sales Manager dashboard | FR-054, FR-055, FR-056 | Team Summary and Account Manager Detail | Verify dashboard summary and detail |
| BR-010 | Visit report export | FR-063, FR-066 | Generate and Export Visit Activity Report | Verify Excel visit report generation |
| BR-011 | Customer report export | FR-064, FR-067 | Generate and Export Customer Report | Verify Excel customer report generation |
| BR-012 | Role-based access | FR-003, FR-068 | Role-Based Access Control | Verify user access restrictions |
| BR-013 | Centralized data synchronization | Pending confirmation | Android and Web data synchronization | Verify data consistency across platforms |

## 3. Test Scenario Summary

| Test ID | Test Scenario | Expected Result |
|---|---|---|
| TC-001 | Create customer visit schedule | Schedule is saved and displayed in calendar |
| TC-002 | Create duplicate customer visit on the same date | System rejects the duplicate active schedule |
| TC-003 | Perform GPS check-in within 100 meters | Check-in passes location validation |
| TC-004 | Perform GPS check-in outside 100 meters | System rejects valid check-in |
| TC-005 | Perform GPS check-out within 100 meters | Check-out passes location validation |
| TC-006 | Submit visit without required notes | System prevents final submission |
| TC-007 | Submit visit without follow-up | System prevents final submission |
| TC-008 | Submit visit without attachment | System prevents final submission |
| TC-009 | Reassign customer through Sales Planning mapping | Customer ownership updates automatically |
| TC-010 | Export Visit Activity Report | Excel file is generated with approved columns |
| TC-011 | Export Customer Report | Excel file is generated with approved columns |
| TC-012 | Access unauthorized customer records | System denies unauthorized access |
| TC-013 | Update Account Manager Employee ID mapping | Customer ownership changes while historical visits remain unchanged |

## 4. Traceability Status

| Status | Description |
|---|---|
| Covered | Business requirement is mapped to FRS |
| Pending | Requirement needs further confirmation |
| Not Covered | Requirement has no corresponding functional requirement |
| Under Review | Requirement mapping requires validation |

## 5. Open Items

The following items require further review:

- BR-013 data synchronization details.
- GPS accuracy threshold.
- GPS check-in and check-out exception handling.
- Detailed report export authorization.
- Customer status transition rules.
- Follow-up assignment and ownership rules.

## 6. Conclusion

This RTM provides traceability between the Sales Activity Tracking System business requirements, functional specifications, and proposed test scenarios.

The matrix will be updated as requirements are reviewed, approved, and validated during the project lifecycle.

All project scenarios and test data are fictional and created for professional portfolio purposes.

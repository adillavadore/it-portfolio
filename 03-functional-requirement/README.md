# Functional Requirement Specification (FRS)
## Sales Activity Tracking System

**Document Version:** 1.0  
**Project:** Sales Activity Tracking System  
**Application:** Android Mobile Application & Web Application  
**Document Status:** Draft

---

## 1. Login & User Management

### 1.1 Module Overview

This module manages user authentication and access permissions for the Sales Activity Tracking System.

The system shall allow authorized users to access the Android and Web applications using their registered credentials.

### 1.2 User Roles

| User Role | Description |
|---|---|
| Account Manager | Manages customer visits and sales activities |
| Sales Manager | Monitors team activities and customer development |
| Management | Reviews consolidated sales reports and dashboards |
| Administrator | Manages user accounts and access permissions |

### 1.3 Functional Requirements

#### FR-001: User Login

**Description:**

The system shall allow registered users to log in using their registered username or email and password.

**Input:**
- Username or email.
- Password.

**Process:**
1. User opens the application.
2. User enters login credentials.
3. System validates the submitted credentials.
4. System verifies the user's account status and permissions.
5. System grants access when authentication is successful.

**Output:**
- Successful login: User is redirected to the relevant dashboard or home page.
- Failed login: System displays an appropriate error message.

**Business Rules:**
- Only registered and active users can access the system.
- Invalid credentials must not grant access.
- User access must follow assigned roles and permissions.

#### FR-002: User Logout

**Description:**

The system shall allow users to securely log out from the application.

**Process:**
1. User selects Logout.
2. System terminates the active session.
3. User is redirected to the login page.

**Output:**
- User session is terminated.
- Protected pages require authentication before access.

#### FR-003: Role-Based Access Control

**Description:**

The system shall restrict access to application features according to the assigned user role.

**Access Overview:**

| Feature | Account Manager | Sales Manager | Management | Administrator |
|---|---|---|---|---|
| Customer Listing | Assigned | Team | Authorized | Yes |
| Visit Planning | Yes | View | View | Yes |
| Visit Recording | Yes | View | View | Yes |
| Sales Dashboard | Personal | Team | Consolidated | Yes |
| Excel Reports | Authorized | Yes | Yes | Yes |
| User Management | No | No | No | Yes |

**Business Rules:**
- Each user must have an assigned role.
- Users may access the Web Application according to their permissions.
- Account Managers may only access customer and activity data permitted by their assignment.
- Sales Managers may monitor activities within their authorized team scope.
- Management may access consolidated information according to assigned permissions.
- Administrators manage user accounts and role assignments.

#### FR-004: User Account Management

**Description:**

The system shall allow authorized administrators to manage user accounts.

**Functions:**
- Create user accounts.
- Update user information.
- Assign user roles.
- Activate and deactivate user accounts.
- View user account information.

**Business Rules:**
- Only authorized administrators can manage user accounts.
- Inactive users cannot access the system.
- Each user account must have a unique identifier.

### 1.4 Non-Functional Requirements

- User authentication must be secure.
- Passwords must be stored securely.
- Access permissions must be enforced on the backend.
- User sessions must be protected against unauthorized access.
- Important user account changes must be recorded in activity logs.

### 1.5 Acceptance Criteria

The module will be considered acceptable when:

- Registered users can log in successfully.
- Invalid credentials are rejected.
- Inactive users cannot log in.
- Users can log out successfully.
- Application access follows assigned user roles.
- Administrators can manage user accounts.
- Unauthorized users cannot access restricted features.

---

## 2. Document Notes

This specification is part of the simulated Sales Activity Tracking System portfolio project.

The detailed authentication mechanism, password policy, session expiration, and integration requirements will be defined during system design.

All business scenarios and user information are fictional.

---

## 3. Customer Management

### 3.1 Module Overview

This module manages customer information and customer status within the Sales Activity Tracking System.

The module enables Account Managers to access their assigned customer information and allows authorized users to manage customer records and monitor customer development.

### 3.2 Customer Information

The system shall maintain the following customer information:

| Field | Description |
|---|---|
| Customer ID | Unique customer identifier |
| Customer Name | Customer or company name |
| Customer Address | Customer business address |
| Contact Person | Main customer contact |
| Contact Number | Customer contact number |
| Email Address | Customer email |
| Customer Status | Proposed, Prospect, Current, Inactive, or Lost |
| Assigned Account Manager | Responsible Account Manager |
| Created Date | Customer record creation date |

### 3.3 Functional Requirements

#### FR-028: View Customer List

**Description:**

The system shall allow authorized users to view customer records.

**Input:**
- Search keyword.
- Customer status filter.
- Account Manager filter (where authorized).

**Process:**
1. User opens the Customer menu.
2. System retrieves customer records according to user permissions.
3. System displays the customer list.
4. User can search and filter customer information.

**Output:**
- Customer list displayed according to access permissions.

#### FR-029: View Customer Details

**Description:**

The system shall allow authorized users to view detailed customer information.

**Output:**
- Customer profile.
- Contact information.
- Customer status.
- Assigned Account Manager.
- Customer visit history, subject to permissions.

#### FR-030: Create Customer

**Description:**

The system shall allow authorized users to register new customer information.

**Input:**
- Customer name.
- Customer address.
- Contact person.
- Contact number.
- Email address.
- Customer status.
- Assigned Account Manager.

**Process:**
1. User selects Add Customer.
2. User enters customer information.
3. System validates mandatory fields.
4. System checks customer record completeness.
5. System saves the customer record.

**Output:**
- Customer record successfully created.
- New customer appears in the customer list.

#### FR-031: Update Customer Information

**Description:**

The system shall allow authorized users to update customer information.

**Process:**
1. User selects an existing customer.
2. User selects Edit.
3. User updates permitted customer information.
4. System validates the updated information.
5. System saves the changes.

**Output:**
- Updated customer information is displayed.

#### FR-032: Customer Status Management

**Description:**

The system shall allow authorized users to manage customer status.

**Available Statuses:**
- Proposed
- Prospect
- Current
- Inactive
- Lost

**Business Rules:**
- Each customer must have one current status.
- Status changes must be performed by authorized users.
- Important status changes must be recorded in the activity log.
- Status transition rules require business stakeholder approval.

#### FR-033: Automatic Customer Ownership Reassignment

**Description:**

The system shall automatically reassign customer ownership when the Sales Planning team updates the Employee ID associated with an existing Sales ID.

**Preconditions:**
- The new Account Manager (AM B) must already have an active user account.
- The required Sales ID and user access configuration for AM B must be registered in the system.
- The Sales Planning team must have authorized access to update employee mapping.

**Business Process:**

1. Sales Planning identifies the Account Manager reassignment.
2. Sales Planning verifies that AM B has an active user account and the required Sales ID configuration.
3. Sales Planning updates the Employee ID associated with the existing Sales ID.
4. The system retrieves the updated Sales ID and Employee ID mapping.
5. The system immediately updates customer ownership for all customers associated with the affected Sales ID.
6. AM B receives access to the reassigned customer records.
7. AM A loses access to the reassigned customer records, unless separately authorized.

**Business Rules:**

- The existing Sales ID remains unchanged during reassignment.
- Employee ID is updated according to the latest Sales Planning mapping.
- Customer ownership is determined by the active Sales ID and Employee ID mapping.
- All customers associated with the affected Sales ID are reassigned automatically.
- Reassignment takes effect immediately after a successful mapping update.
- Only authorized Sales Planning users can update the mapping.
- Historical visit records must retain the original visiting employee identity.
- All mapping changes must be recorded in an audit log.

**Acceptance Criteria:**

- AM B must have an active user account before reassignment.
- Sales Planning can update the Employee ID mapping.
- The existing Sales ID remains unchanged.
- All associated customers automatically reflect the new Account Manager.
- AM B can access the reassigned customer records.
- AM A cannot access the reassigned customer records unless separately authorized.
- Historical visit records remain associated with the original visiting employee.
- The system records the previous mapping, updated mapping, timestamp, and responsible user.
- 
### 3.4 Business Rules

- Each customer must have a unique Customer ID.
- Customer name and required customer information must be provided.
- Each customer must have a defined customer status.
- Customer access must follow assigned user permissions.
- Customer assignment changes must be restricted to authorized users.
- Customer records must be retained according to applicable data retention policies.

### 3.5 Acceptance Criteria

The module will be considered acceptable when:

- Authorized users can view customer lists.
- Users can search and filter customer records.
- Authorized users can view customer details.
- Authorized users can create customer records.
- Authorized users can update customer information.
- Customer status can be managed by authorized users.
- Customers can be assigned to Account Managers.
- Unauthorized users cannot access restricted customer records.

---
---

## 4. Visit Planning & Calendar

### 4.1 Module Overview

This module enables Account Managers to plan and manage customer visits through the Android Mobile Application.

The system provides a monthly calendar to display scheduled customer visits and allows authorized users to create, reschedule, and cancel visit schedules.

Sales Managers can also monitor and manage visit schedules according to their assigned permissions.

### 4.2 User Roles

| User Role | Responsibility |
|---|---|
| Account Manager | Create, view, reschedule, and cancel assigned visit schedules |
| Sales Manager | View, monitor, reschedule, and cancel team visit schedules |

### 4.3 Visit Schedule Information

The system shall maintain the following visit schedule information:

| Field | Description |
|---|---|
| Visit ID | Unique visit schedule identifier |
| Customer ID | Customer identifier |
| Customer Name | Customer or company name |
| Sales ID | Assigned sales identifier |
| Employee ID | Responsible Account Manager |
| Visit Date | Planned visit date |
| Start Time | Planned visit start time |
| End Time | Planned visit end time |
| Visit Purpose | Selected visit purpose category |
| Additional Notes | Additional visit description |
| Visit Status | Current schedule status |
| Created Date | Schedule creation timestamp |

### 4.4 Functional Requirements

#### FR-035: Monthly Visit Calendar

**Description:**

The Android application shall provide a monthly calendar to display customer visit schedules.

**Process:**
1. Account Manager opens the Visit Planning menu.
2. System displays the current monthly calendar.
3. System retrieves visit schedules assigned to the Account Manager.
4. Scheduled visits are displayed on their respective dates.
5. User selects a calendar date to view visit details.

**Output:**
- Monthly calendar.
- Visit schedules by date.
- Visit details for selected dates.

#### FR-036: Create Visit Schedule

**Description:**

The system shall allow Account Managers to create customer visit schedules through the Android application.

**Input:**
- Customer.
- Visit date.
- Start time.
- End time.
- Visit purpose category.
- Additional notes (optional).

**Process:**
1. Account Manager selects a customer.
2. Account Manager selects the planned visit date.
3. Account Manager enters the visit time.
4. Account Manager selects a visit purpose category.
5. Account Manager enters additional notes if necessary.
6. System validates the submitted information.
7. System checks whether the customer already has a visit schedule on the selected date.
8. System saves the visit schedule if validation is successful.

**Output:**
- Visit schedule successfully created.
- New schedule appears in the monthly calendar.

#### FR-037: Duplicate Customer Visit Validation

**Description:**

The system shall prevent an Account Manager from creating more than one visit schedule for the same customer on the same date.

**Business Rules:**
- One customer can only have one active visit schedule per calendar date.
- Different visit times do not permit a second schedule for the same customer on the same date.
- The validation shall consider existing active schedules.
- Cancelled schedules shall not count as active schedules.
- The system shall display an appropriate warning when a duplicate schedule is detected.

**Output:**

The system displays a duplicate visit warning and does not save the additional schedule.

#### FR-038: View Visit Schedule Details

**Description:**

The system shall allow authorized users to view detailed information about scheduled visits.

**Output:**
- Customer information.
- Visit date and time.
- Visit purpose.
- Additional notes.
- Assigned Account Manager.
- Visit status.

#### FR-039: Reschedule Visit

**Description:**

The system shall allow Account Managers and authorized Sales Managers to change existing visit schedules.

**Process:**
1. User selects an existing visit schedule.
2. User selects Reschedule.
3. User enters the new visit date and time.
4. System validates the updated schedule.
5. System checks duplicate customer visit restrictions.
6. System saves the updated schedule.
7. System updates the monthly calendar.

**Business Rules:**
- Account Managers may reschedule their assigned visits.
- Sales Managers may reschedule visits within their authorized team scope.
- The system must retain the original schedule information for audit purposes.
- Duplicate visit validation must be applied to the new date.

**Output:**
- Updated visit schedule.
- Updated monthly calendar.

#### FR-040: Cancel Visit Schedule

**Description:**

The system shall allow Account Managers and authorized Sales Managers to cancel existing visit schedules.

**Process:**
1. User selects an existing visit schedule.
2. User selects Cancel Visit.
3. User provides a cancellation reason.
4. System updates the visit status to Cancelled.
5. System records the cancellation information.

**Business Rules:**
- Only authorized users can cancel visit schedules.
- Cancelled schedules must remain available in historical records.
- Cancelled schedules shall not be treated as active visits.
- Cancellation information must be recorded in the audit log.

**Output:**
- Visit status updated to Cancelled.
- Cancellation information recorded.

#### FR-041: Visit Purpose Management

**Description:**

The system shall allow Account Managers to select a predefined visit purpose category and provide additional notes.

**Proposed Visit Purpose Categories:**
- Customer Relationship Management.
- Business Opportunity Discussion.
- Service Review.
- Complaint Handling.
- Contract Discussion.
- New Business Development.
- Other.

**Business Rules:**
- Account Managers must select one visit purpose category.
- Additional notes may be entered to provide more context.
- When Other is selected, additional notes should explain the visit purpose.

**Output:**
- Selected visit purpose category.
- Additional visit description.

### 4.5 Business Rules

- Every visit schedule must be associated with a valid customer.
- Every visit schedule must have an assigned Account Manager.
- Each customer may have only one active scheduled visit per calendar date.
- Visit date and time are mandatory.
- Visit purpose category is mandatory.
- Additional notes are optional except when Other is selected.
- Rescheduling and cancellation are restricted to authorized users.
- Changes to visit schedules must be recorded in the audit log.
- Visit schedules must be available to authorized users through the centralized system.

### 4.6 Acceptance Criteria

The module will be considered acceptable when:

- Account Managers can access the monthly calendar.
- Account Managers can create customer visit schedules.
- The system prevents duplicate active visit schedules for the same customer on the same date.
- Visit schedules are displayed on the correct calendar dates.
- Authorized Account Managers and Sales Managers can reschedule visits.
- Authorized Account Managers and Sales Managers can cancel visits.
- The system records cancellation reasons.
- Visit purpose categories can be selected.
- Additional visit notes can be entered.
- Schedule changes are recorded for audit purposes.

---

## 4. Visit Planning & Calendar

### 4.1 Module Overview

This module enables Account Managers to plan and manage customer visits through the Android Mobile Application.

The system provides a monthly calendar to display scheduled customer visits and allows authorized users to create, reschedule, and cancel visit schedules.

Sales Managers can also monitor and manage visit schedules according to their assigned permissions.

### 4.2 User Roles

| User Role | Responsibility |
|---|---|
| Account Manager | Create, view, reschedule, and cancel assigned visit schedules |
| Sales Manager | View, monitor, reschedule, and cancel team visit schedules |

### 4.3 Visit Schedule Information

The system shall maintain the following visit schedule information:

| Field | Description |
|---|---|
| Visit ID | Unique visit schedule identifier |
| Customer ID | Customer identifier |
| Customer Name | Customer or company name |
| Sales ID | Assigned sales identifier |
| Employee ID | Responsible Account Manager |
| Visit Date | Planned visit date |
| Start Time | Planned visit start time |
| End Time | Planned visit end time |
| Visit Purpose | Selected visit purpose category |
| Additional Notes | Additional visit description |
| Visit Status | Current schedule status |
| Created Date | Schedule creation timestamp |

### 4.4 Functional Requirements

#### FR-035: Monthly Visit Calendar

**Description:**

The Android application shall provide a monthly calendar to display customer visit schedules.

**Process:**
1. Account Manager opens the Visit Planning menu.
2. System displays the current monthly calendar.
3. System retrieves visit schedules assigned to the Account Manager.
4. Scheduled visits are displayed on their respective dates.
5. User selects a calendar date to view visit details.

**Output:**
- Monthly calendar.
- Visit schedules by date.
- Visit details for selected dates.

#### FR-036: Create Visit Schedule

**Description:**

The system shall allow Account Managers to create customer visit schedules through the Android application.

**Input:**
- Customer.
- Visit date.
- Start time.
- End time.
- Visit purpose category.
- Additional notes (optional).

**Process:**
1. Account Manager selects a customer.
2. Account Manager selects the planned visit date.
3. Account Manager enters the visit time.
4. Account Manager selects a visit purpose category.
5. Account Manager enters additional notes if necessary.
6. System validates the submitted information.
7. System checks whether the customer already has a visit schedule on the selected date.
8. System saves the visit schedule if validation is successful.

**Output:**
- Visit schedule successfully created.
- New schedule appears in the monthly calendar.

#### FR-037: Duplicate Customer Visit Validation

**Description:**

The system shall prevent an Account Manager from creating more than one visit schedule for the same customer on the same date.

**Business Rules:**
- One customer can only have one active visit schedule per calendar date.
- Different visit times do not permit a second schedule for the same customer on the same date.
- The validation shall consider existing active schedules.
- Cancelled schedules shall not count as active schedules.
- The system shall display an appropriate warning when a duplicate schedule is detected.

**Output:**

The system displays a duplicate visit warning and does not save the additional schedule.

#### FR-038: View Visit Schedule Details

**Description:**

The system shall allow authorized users to view detailed information about scheduled visits.

**Output:**
- Customer information.
- Visit date and time.
- Visit purpose.
- Additional notes.
- Assigned Account Manager.
- Visit status.

#### FR-039: Reschedule Visit

**Description:**

The system shall allow Account Managers and authorized Sales Managers to change existing visit schedules.

**Process:**
1. User selects an existing visit schedule.
2. User selects Reschedule.
3. User enters the new visit date and time.
4. System validates the updated schedule.
5. System checks duplicate customer visit restrictions.
6. System saves the updated schedule.
7. System updates the monthly calendar.

**Business Rules:**
- Account Managers may reschedule their assigned visits.
- Sales Managers may reschedule visits within their authorized team scope.
- The system must retain the original schedule information for audit purposes.
- Duplicate visit validation must be applied to the new date.

**Output:**
- Updated visit schedule.
- Updated monthly calendar.

#### FR-040: Cancel Visit Schedule

**Description:**

The system shall allow Account Managers and authorized Sales Managers to cancel existing visit schedules.

**Process:**
1. User selects an existing visit schedule.
2. User selects Cancel Visit.
3. User provides a cancellation reason.
4. System updates the visit status to Cancelled.
5. System records the cancellation information.

**Business Rules:**
- Only authorized users can cancel visit schedules.
- Cancelled schedules must remain available in historical records.
- Cancelled schedules shall not be treated as active visits.
- Cancellation information must be recorded in the audit log.

**Output:**
- Visit status updated to Cancelled.
- Cancellation information recorded.

#### FR-041: Visit Purpose Management

**Description:**

The system shall allow Account Managers to select a predefined visit purpose category and provide additional notes.

**Proposed Visit Purpose Categories:**
- Customer Relationship Management.
- Business Opportunity Discussion.
- Service Review.
- Complaint Handling.
- Contract Discussion.
- New Business Development.
- Other.

**Business Rules:**
- Account Managers must select one visit purpose category.
- Additional notes may be entered to provide more context.
- When Other is selected, additional notes should explain the visit purpose.

**Output:**
- Selected visit purpose category.
- Additional visit description.

### 4.5 Business Rules

- Every visit schedule must be associated with a valid customer.
- Every visit schedule must have an assigned Account Manager.
- Each customer may have only one active scheduled visit per calendar date.
- Visit date and time are mandatory.
- Visit purpose category is mandatory.
- Additional notes are optional except when Other is selected.
- Rescheduling and cancellation are restricted to authorized users.
- Changes to visit schedules must be recorded in the audit log.
- Visit schedules must be available to authorized users through the centralized system.

### 4.6 Acceptance Criteria

The module will be considered acceptable when:

- Account Managers can access the monthly calendar.
- Account Managers can create customer visit schedules.
- The system prevents duplicate active visit schedules for the same customer on the same date.
- Visit schedules are displayed on the correct calendar dates.
- Authorized Account Managers and Sales Managers can reschedule visits.
- Authorized Account Managers and Sales Managers can cancel visits.
- The system records cancellation reasons.
- Visit purpose categories can be selected.
- Additional visit notes can be entered.
- Schedule changes are recorded for audit purposes.

---

---


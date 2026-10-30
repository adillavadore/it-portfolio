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

## 5. GPS Check-in & Check-out

### 5.1 Module Overview

This module enables Account Managers to validate customer visits through GPS-based check-in and check-out using the Android Mobile Application.

The system captures GPS coordinates and timestamps to record the Account Manager's location during customer visits.

A customer visit must be within a maximum radius of 100 meters from the registered customer location to satisfy the GPS location validation requirement.

### 5.2 GPS Visit Information

| Field | Description |
|---|---|
| Visit ID | Unique visit identifier |
| Customer ID | Customer identifier |
| Customer Name | Customer name |
| Account Manager | Responsible employee |
| Check-in Latitude | GPS latitude at check-in |
| Check-in Longitude | GPS longitude at check-in |
| Check-in Timestamp | Check-in date and time |
| Check-in Photo | Photo captured during check-in |
| Check-out Latitude | GPS latitude at check-out |
| Check-out Longitude | GPS longitude at check-out |
| Check-out Timestamp | Check-out date and time |
| GPS Accuracy | GPS accuracy information |
| Visit Validation Status | GPS validation result |

### 5.3 Functional Requirements

#### FR-042: GPS Check-in

**Description:**

The Android application shall allow Account Managers to perform GPS-based check-in when arriving at a scheduled customer location.

**Preconditions:**
- Account Manager must be logged in.
- A valid customer visit schedule must exist.
- Device location permission must be enabled.
- Internet connectivity must be available.

**Process:**
1. Account Manager selects an existing visit schedule.
2. Account Manager selects Check-in.
3. System requests the device's current GPS location.
4. System captures latitude, longitude, and timestamp.
5. System calculates the distance between the current GPS location and the registered customer location.
6. System validates the distance against the 100-meter radius.
7. System checks GPS accuracy.
8. Account Manager captures a check-in photo.
9. System saves the GPS information, timestamp, photo, and visit validation result when all mandatory validations are satisfied.

**Output:**
- Recorded GPS coordinates.
- Check-in timestamp.
- Check-in photo.
- GPS validation result.
- Updated visit status.

#### FR-043: GPS Radius Validation

**Description:**

The system shall validate the Account Manager's GPS location against the registered customer location.

**Business Rules:**
- The maximum permitted distance is 100 meters.
- The distance shall be calculated using the current GPS coordinates and registered customer coordinates.
- Check-in outside the permitted radius shall not be accepted as a valid visit check-in.
- The system shall display an appropriate warning when the Account Manager is outside the permitted radius.
- The validation result must be recorded.

**Output:**
- Valid location: GPS radius validation successful.
- Invalid location: System displays a location validation warning.

#### FR-044: GPS Accuracy Warning

**Description:**

The system shall monitor GPS accuracy during check-in and check-out operations.

**Process:**
1. System retrieves GPS coordinates and accuracy information.
2. System evaluates the GPS accuracy against the configured accuracy threshold.
3. If GPS accuracy is insufficient, the system displays a warning.
4. Account Manager is requested to retry GPS location detection.
5. System repeats the GPS accuracy validation.

**Business Rules:**
- GPS accuracy warnings must be displayed to the Account Manager.
- The system must allow the Account Manager to retry location detection.
- GPS accuracy thresholds must be configurable.
- The system must not classify an inaccurate GPS reading as a validated location without satisfying the configured validation rules.

#### FR-045: Check-in Photo Capture

**Description:**

The Android application shall require an Account Manager to capture a photo during customer visit check-in.

**Process:**
1. Account Manager selects Check-in.
2. System requests GPS validation.
3. Account Manager captures a photo using the device camera.
4. System associates the photo with the relevant visit record.
5. System stores the photo reference and check-in information.

**Business Rules:**
- A check-in photo is mandatory.
- The photo must be associated with the relevant Visit ID.
- The system must record the check-in timestamp.
- Photo access must follow authorized user permissions.
- Photo storage and retention must follow applicable company policies.

#### FR-046: GPS Check-out

**Description:**

The Android application shall allow Account Managers to perform GPS-based check-out after completing a customer visit.

**Preconditions:**
- A valid check-in record must exist.
- The visit must not already be checked out.
- Device location permission must be available.

**Process:**
1. Account Manager selects Check-out.
2. System requests the current GPS location.
3. System captures latitude and longitude.
4. System records the check-out timestamp.
5. System validates GPS accuracy and location radius.
6. System saves the check-out information.
7. System updates the visit status.

**Output:**
- Check-out GPS coordinates.
- Check-out timestamp.
- GPS validation result.
- Updated visit status.

#### FR-047: GPS Visit History

**Description:**

The system shall maintain GPS check-in and check-out information for each completed customer visit.

**Information to be maintained:**
- Visit ID.
- Customer information.
- Account Manager information.
- Check-in location.
- Check-in timestamp.
- Check-in photo.
- Check-out location.
- Check-out timestamp.
- GPS validation status.

**Output:**
Authorized users can review GPS visit information through the Web Application.

### 5.4 Business Rules

- GPS check-in must be associated with an existing visit schedule.
- GPS check-in must be performed within 100 meters of the registered customer location.
- A check-in photo is mandatory.
- GPS coordinates and timestamps must be recorded.
- GPS accuracy warnings must be displayed when the configured threshold is not met.
- Account Managers must retry GPS detection when an accuracy warning occurs.
- Check-out must be performed after a valid check-in.
- Check-out must record GPS coordinates and timestamp.
- GPS information must be associated with the relevant Visit ID.
- GPS records must be protected against unauthorized modification.
- GPS data and visit photos must be accessible only to authorized users.

### 5.5 Acceptance Criteria

The module will be considered acceptable when:

- Account Managers can perform GPS check-in for scheduled visits.
- The system captures GPS coordinates and timestamps.
- The system validates the 100-meter customer location radius.
- The system rejects check-in outside the permitted radius as a valid visit.
- Account Managers must capture a photo during check-in.
- GPS accuracy warnings are displayed when necessary.
- Account Managers can retry GPS detection.
- Account Managers can perform GPS check-out after check-in.
- Check-out GPS coordinates and timestamps are recorded.
- GPS visit records can be reviewed by authorized users through the Web Application.

---

## 6. Visit Activity Recording & Follow-up Management

### 6.1 Module Overview

This module enables Account Managers to record customer visit results, document meeting notes, attach supporting evidence, and create follow-up activities through the Android Mobile Application.

The system ensures that every customer visit is properly documented and has a corresponding follow-up action.

Visit information shall be available to authorized users through the Web Application.

### 6.2 Visit Activity Information

| Field | Description |
|---|---|
| Visit ID | Unique visit identifier |
| Customer ID | Customer identifier |
| Customer Name | Customer name |
| Account Manager | Responsible employee |
| Visit Date | Actual visit date |
| Visit Outcome | Result of customer visit |
| Visit Notes | Free-text meeting notes |
| Follow-up Action | Required next action |
| Follow-up Due Date | Expected follow-up date |
| Attachment | Supporting photo or document |
| Check-in Timestamp | Actual check-in time |
| Check-out Timestamp | Actual check-out time |
| Visit Status | Current visit status |

### 6.3 Visit Outcome Classification

The system shall provide the following visit outcome categories:

| Outcome | Description |
|---|---|
| Successful | Customer meeting successfully conducted |
| No Response | Customer was unavailable or did not respond |
| Reschedule | Customer meeting needs to be rescheduled |
| Not Interested | Customer indicates no interest in the proposed business |
| Business Opportunity | Potential business opportunity identified |
| Complaint | Customer submitted a complaint |
| Other | Other visit outcomes not covered by the predefined categories |

### 6.4 Functional Requirements

#### FR-048: Record Visit Outcome

**Description:**

The system shall allow Account Managers to record the outcome of customer visits through the Android application.

**Input:**
- Visit ID.
- Visit outcome category.
- Visit notes.

**Process:**
1. Account Manager opens the active visit record.
2. Account Manager selects a visit outcome category.
3. Account Manager enters meeting notes.
4. System validates the submitted information.
5. System saves the visit activity record.

**Output:**
- Visit outcome recorded.
- Visit notes stored.
- Visit activity updated.

**Business Rules:**
- Visit outcome is mandatory.
- Account Manager must select one predefined outcome category.
- Visit notes shall support free-text input.
- The Other category should include an explanation in the visit notes.

#### FR-049: Record Visit Notes

**Description:**

The system shall allow Account Managers to document customer meeting results through free-text input.

**Information may include:**
- Meeting discussion.
- Customer requirements.
- Customer feedback.
- Business opportunities.
- Service concerns.
- Agreed actions.

**Business Rules:**
- Visit notes are mandatory.
- Visit notes must be associated with the relevant Visit ID.
- Notes must be available to authorized users through the Web Application.

#### FR-050: Create Follow-up Activity

**Description:**

The system shall require Account Managers to create a follow-up activity for every recorded customer visit.

**Input:**
- Follow-up action.
- Follow-up due date.

**Process:**
1. Account Manager completes the visit outcome and notes.
2. Account Manager enters the required follow-up action.
3. Account Manager selects a follow-up due date.
4. System validates the follow-up information.
5. System saves the follow-up activity.
6. The follow-up activity becomes available for monitoring.

**Business Rules:**
- Every customer visit must have at least one follow-up activity.
- Follow-up action is mandatory.
- Follow-up due date is mandatory.
- Follow-up activities must be associated with the relevant Visit ID and customer.
- Follow-up information must be available to authorized Sales Managers.
- Follow-up completion status must be trackable.

#### FR-051: Upload Visit Attachment

**Description:**

The system shall require Account Managers to upload at least one supporting attachment for every customer visit.

**Supported Attachment Types (Proposed):**
- JPG
- JPEG
- PNG
- PDF

**Process:**
1. Account Manager opens the visit activity form.
2. Account Manager selects an attachment from the device or captures a photo.
3. System validates the attachment format and file size.
4. System associates the attachment with the relevant Visit ID.
5. System stores the attachment reference.

**Business Rules:**
- At least one attachment is mandatory for every visit.
- Multiple attachments may be supported.
- Attachment formats must follow configured system restrictions.
- Attachments must be accessible only to authorized users.
- Attachment upload must be completed before the visit record can be finalized.

#### FR-052: Update Follow-up Status

**Description:**

The system shall allow authorized users to update and monitor follow-up activity status.

**Proposed Follow-up Statuses:**
- Pending
- In Progress
- Completed
- Overdue
- Cancelled

**Process:**
1. Authorized user opens the follow-up record.
2. User reviews the follow-up information.
3. User updates the follow-up status.
4. System saves the updated status.
5. Updated information becomes available on the Web Application.

**Business Rules:**
- Each follow-up activity must have a defined status.
- Completed follow-ups must retain completion information.
- Overdue status should be determined based on the due date and completion status.
- Follow-up status changes must be recorded.

#### FR-053: View Visit Activity History

**Description:**

The system shall allow authorized users to view historical customer visit activities through the Web Application.

**Information to be displayed:**
- Customer information.
- Account Manager information.
- Visit date.
- Visit outcome.
- Visit notes.
- Follow-up action.
- Follow-up due date.
- Follow-up status.
- Supporting attachments.
- GPS check-in and check-out information.

**Output:**
- Consolidated customer visit history.
- Visit activity details.
- Follow-up activity information.
- Supporting attachment references.

### 6.5 Business Rules

- Every visit must have a recorded outcome.
- Every visit must contain visit notes.
- Every visit must have at least one follow-up activity.
- Every visit must have at least one supporting attachment.
- Follow-up activities must have an action and due date.
- Visit activities must be associated with a valid customer and Account Manager.
- Visit records must retain their historical information.
- Authorized Sales Managers may monitor team visit activities and follow-up progress.
- Attachments and visit records must be protected against unauthorized access.

### 6.6 Acceptance Criteria

The module will be considered acceptable when:

- Account Managers can record customer visit outcomes.
- All predefined visit outcome categories are available.
- Account Managers can enter free-text visit notes.
- The system requires visit notes before final submission.
- The system requires at least one follow-up activity.
- Follow-up action and due date are mandatory.
- The system requires at least one supporting attachment.
- The system validates permitted attachment formats.
- Follow-up activities can be monitored and updated.
- Authorized users can view historical visit activities through the Web Application.
- Visit information and attachments are associated with the correct customer and Visit ID.



---


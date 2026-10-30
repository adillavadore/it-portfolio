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

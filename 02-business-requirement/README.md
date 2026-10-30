# Business Requirement Document (BRD)
## Sales Activity Tracking System

**Document Version:** 1.1  
**Project Type:** Simulated Portfolio Project  
**Document Owner:** Business Analyst  
**Application Platforms:** Android Mobile Application & Web Application  
**Document Status:** Draft for Business Validation

---

## 1. Introduction

### 1.1 Purpose

This document defines the business requirements for the Sales Activity Tracking System. The system aims to improve customer visit planning, sales activity recording, customer status monitoring, and management reporting through integrated Android and Web applications.

### 1.2 Business Background

Account Managers are responsible for maintaining customer relationships, planning customer visits, identifying business opportunities, and following up on customer needs.

Without a centralized system, sales activities may be recorded through spreadsheets, emails, or messaging applications. This creates challenges in monitoring customer visits, tracking customer development, validating visit activities, and preparing management reports.

The proposed system will provide a centralized platform for recording, managing, and monitoring sales activities.

### 1.3 Project Objectives

- Simplify customer visit planning and scheduling.
- Enable GPS-based customer visit validation.
- Centralize sales visit activity records.
- Improve customer follow-up monitoring.
- Provide visibility into customer status.
- Enable Sales Managers to monitor team activities.
- Provide downloadable Excel reports.
- Improve data availability across mobile and web platforms.

## 2. System Overview

The Sales Activity Tracking System consists of two integrated applications.

### 2.1 Android Mobile Application

The Android application is designed primarily for Account Managers to manage field sales activities.

Key capabilities:
- Customer listing and information.
- Customer visit planning.
- Calendar-based visit scheduling.
- GPS-based check-in and check-out.
- Visit result recording.
- Follow-up activity recording.
- Customer status information.

The Android application requires an active internet connection to access and submit information to the centralized system.

### 2.2 Web Application

The Web Application provides access to all authorized system users, based on their assigned roles and permissions.

Key capabilities:
- Customer information management.
- Sales activity monitoring.
- Visit schedule monitoring.
- Customer status monitoring.
- Sales Manager dashboard.
- Visit activity reporting.
- Customer reporting.
- Excel report export.

### 2.3 Centralized Data Management

Both applications will access a centralized backend and database.

Customer information, visit schedules, GPS records, visit results, and follow-up activities will be maintained centrally and made available to authorized users through the relevant application interfaces.

## 3. Stakeholder Analysis

| Stakeholder | Responsibility |
|---|---|
| Sales Manager | Monitor sales activities and customer development |
| Account Manager | Plan customer visits and record visit results |
| Management | Review sales activity and customer reports |
| IT Project Manager | Coordinate project delivery |
| Business Analyst | Analyze business requirements |
| System Analyst | Define system requirements and solution design |
| Development Team | Develop Android and Web applications |
| IT Support | Provide technical support |

## 4. Business Requirements

| ID | Business Requirement | Priority |
|---|---|---|
| BR-001 | The system shall support customer visit planning through the Android application. | High |
| BR-002 | The system shall provide calendar-based visit scheduling. | High |
| BR-003 | The system shall support GPS-based visit check-in and check-out. | High |
| BR-004 | The system shall allow Account Managers to record visit results. | High |
| BR-005 | The system shall support customer follow-up tracking. | High |
| BR-006 | The system shall provide centralized customer information. | High |
| BR-007 | The system shall support customer status monitoring. | High |
| BR-008 | The system shall provide sales activity monitoring through the Web Application. | High |
| BR-009 | The system shall provide a Sales Manager dashboard. | High |
| BR-010 | The system shall provide downloadable Excel visit reports. | High |
| BR-011 | The system shall provide downloadable Excel customer reports. | High |
| BR-012 | The system shall provide role-based access for authorized users across both platforms. | High |
| BR-013 | The system shall synchronize information between Android and Web applications through centralized data management. | High |

## 5. User Roles and Access

### 5.1 Account Manager

The Account Manager shall be able to:
- View assigned customer information.
- Plan and schedule customer visits.
- View visit schedules through the calendar.
- Perform GPS-based visit check-in and check-out.
- Record visit details and outcomes.
- Create and monitor follow-up activities.
- View relevant customer information and visit history.

### 5.2 Sales Manager

The Sales Manager


# SupportOps AI — Functional Requirements

## 1. Purpose

This document defines the initial functional requirements for the SupportOps AI minimum viable product (MVP).

Each requirement has a unique identifier to support implementation, testing, and traceability.

## 2. User Roles

### Employee

An employee manages customer support requests.

For the initial MVP, employees may create, view, search, filter, and update requests.

### Manager

A manager is an employee who may eventually receive additional administrative capabilities.

Manager-specific permissions are outside the initial MVP.

## 3. Functional Requirements

### FR-001: Create Support Request

The system shall allow an employee to create a support request associated with a customer.

Acceptance Criteria:
- A request can be created with valid required information.
- The system generates a unique request ID.
- The created request can be retrieved using its ID.
- Invalid requests return a validation error.

### FR-002: Incomplete Reference Information

The system shall allow an employee to create a request without an order number or product serial number.

Acceptance Criteria:
- Order number and serial number are optional.
- A request can be saved without either value.
- Missing values can be added later.

### FR-003: Update Request Information

The system shall allow an employee to update supported request information after creation.

Acceptance Criteria:
- An existing request can be updated.
- Updated information is persisted.
- Updating a nonexistent request returns a not-found response.

### FR-004: Search Requests

The system shall allow an employee to perform a case-insensitive request search using a full or partial customer name, order number, or serial number.

Acceptance Criteria:
- Searching by full customer name returns matching requests.
- Searching by partial customer name returns matching requests.
- Customer name matching is case-insensitive.
- Searching by order number returns matching requests.
- Searching by serial number returns matching requests.
- A search with no matches returns an empty result set.

### FR-005: Filter Requests

The system shall allow an employee to filter requests by status, priority, and assignee.

Acceptance Criteria:
- Requests can be filtered by status.
- Requests can be filtered by priority.
- Requests can be filtered by assignee.
- Multiple filters can be applied simultaneously.
- Combined filters use AND logic.
- Only requests satisfying all selected filters are returned.

### FR-006: Assign Requests

The system shall allow an employee to assign a request to an employee.

Acceptance Criteria:
- A request can be assigned to an existing employee.
- The assigned employee is stored with the request.
- The assignee can be changed.
- The current assignee can be retrieved.

### FR-007: Request Status

The system shall allow an employee to view and update a request's status.

Acceptance Criteria:
- Every request has a status.
- An employee can retrieve the current status.
- An employee can update the status.
- Invalid status values are rejected.

### FR-008: Request Priority

The system shall allow an employee to view and update a request's priority.

Acceptance Criteria:
- Every request has a priority.
- An employee can retrieve the current priority.
- An employee can update the priority.
- Invalid priority values are rejected.

### FR-009: Request Notes

The system shall allow an employee to add notes to a support request.

Acceptance Criteria:
- An employee can add a note to an existing request.
- Multiple notes can be associated with one request.
- Notes can be retrieved with the request.
- Each note records its creation timestamp.

### FR-010: Customer Information

The system shall allow an employee to associate customer information with a request.

Acceptance Criteria:
- A request references a customer record.
- Customer information can be retrieved.
- Supported customer contact information can be updated.
- Customer information is not duplicated unnecessarily across requests.

## 4. Planned AI Requirements

The following requirements are planned for a later phase and are not part of the initial MVP.

### AI-001: Request Classification

The system shall support AI-generated category suggestions based on request information.

### AI-002: Priority Recommendation

The system shall support AI-generated priority recommendations.

### AI-003: Human Approval

The system shall require employee approval before applying AI-generated priority recommendations.

## 5. Business Rules Requiring Confirmation

The following decisions will be finalized during domain modeling:

- Required customer fields
- Allowed request status values
- Allowed priority values
- Default request status and priority
- Whether an unassigned request is permitted
- Whether notes can be edited or deleted
- Whether request updates are restricted by status
- Whether searches match complete or partial order and serial numbers

## 6. Nonfunctional Requirements

The application should:

- Validate incoming API requests.
- Persist records in a relational database.
- Return consistent API error responses.
- Avoid exposing secrets in source control.
- Include automated tests for core workflows.
- Provide documentation for local setup and execution.

Quantitative performance and availability targets have not yet been established.

## 7. Requirements Traceability

Each implemented requirement will be linked to its corresponding API functionality and automated tests.

Example:

FR-001 -> Create Request API -> Request creation tests

A detailed traceability matrix will be introduced during implementation.

## 8. Document Status

Status: Initial draft

These requirements define the starting MVP scope and may be refined as implementation decisions are made.

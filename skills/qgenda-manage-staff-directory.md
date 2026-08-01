---
name: Read and update the staff member directory
description: List QGenda staff members, read a single provider, and create or update staff records.
api: openapi/qgenda-openapi.yml
operations: [getStaffmember, getStaffmemberStaffId, postStaffmember, putStaffmemberStaffId]
---

# Manage the QGenda staff member directory

Authenticate first (`postLogin`) and send `Authorization: bearer <access_token>` on every call.

## Steps
1. **List staff** — `GET /staffmember` (`getStaffmember`). Supports `includes`, `sinceModifiedTimestamp`, and OData `$select`.
2. **Read one provider** — `GET /staffmember/{staffId}` (`getStaffmemberStaffId`).
3. **Create a staff member** — `POST /staffmember` (`postStaffmember`) with `dateFormat` and a JSON body.
4. **Update a staff member** — `PUT /staffmember/{staffId}` (`putStaffmemberStaffId`).

## Rules
- All write bodies are JSON (`Content-Type: application/json`).
- QGenda does not document an idempotency key — treat POST/PUT as non-idempotent and guard retries.
- Entity relationships: see `data-model/qgenda-data-model.yml`.

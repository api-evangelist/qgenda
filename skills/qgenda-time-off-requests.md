---
name: Retrieve time-off requests and request limits
description: Pull QGenda time-off requests, approved requests, and configured request limits for scheduling.
api: openapi/qgenda-openapi.yml
operations: [getRequest, getRequestApproved, getRequestlimit]
---

# Retrieve QGenda time-off requests

Authenticate first (`postLogin`); send `Authorization: bearer <access_token>`.

## Steps
1. **All requests** — `GET /request` (`getRequest`) with `companyKey`, `startDate`, `endDate`.
2. **Approved requests** — `GET /request/approved` (`getRequestApproved`).
3. **Request limits** — `GET /requestlimit` (`getRequestlimit`) with `companyKey` and `dateFormat`.

## Rules
- JSON responses; `401` on auth failure.
- Request limits nest task-shift and staff-quota sub-resources — see `data-model/qgenda-data-model.yml`.

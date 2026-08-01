---
name: Authenticate and read the physician schedule
description: Obtain a QGenda access token and pull the published schedule, open shifts, and rotations for a company and date range.
api: openapi/qgenda-openapi.yml
operations: [postLogin, getSchedule, getScheduleOpenshifts, getScheduleRotations]
---

# Authenticate and read the QGenda schedule

Base URL: `https://api.qgenda.com/v2` (HTTPS, TLS 1.2/1.3 only).

## Steps
1. **Authenticate** — `POST /login` (`postLogin`). Send `Content-Type: application/x-www-form-urlencoded` with the QGenda username/email and password. The response contains `access_token`. Send it on every later call as `Authorization: bearer <access_token>`. A missing/expired token returns `401` (see `errors/qgenda-problem-types.yml`).
2. **Read the schedule** — `GET /schedule` (`getSchedule`) with `companyKey`, `startDate`, `endDate`. Dates use the documented date format.
3. **Find open shifts** — `GET /schedule/openshifts` (`getScheduleOpenshifts`) for `startDate`/`endDate`.
4. **Read rotations** — `GET /schedule/rotations` (`getScheduleRotations`) with `companyKey`, `rangeStart`.

## Rules
- JSON responses by default; request `Accept-Encoding: br` or `gzip` for compression.
- Some resources accept OData params (`$select`, `$filter`, `$orderby`) — case-sensitive.
- See `conventions/qgenda-conventions.yml` for the full request/response contract.

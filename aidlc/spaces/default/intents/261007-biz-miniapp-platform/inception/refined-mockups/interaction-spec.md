# Interaction Specification

## Login

Submit mock credentials → `POST /mock/session`; success stores the mock session and routes to list; invalid/expired session returns a stable error and keeps retryable fields. Announce loading and result through a live region.

## List and detail

Load `GET /admin/mini-apps`; loading occupies the table region; empty shows Register action; API error shows Retry. Selecting Edit loads the record and preserves navigation context.

## Create and edit

Create uses `POST /admin/mini-apps`; edit uses `PUT /admin/mini-apps/{code}`. Client validation runs before submit. API validation, duplicate-code and session errors map to field or page alerts without clearing input. Success shows confirmation and refreshes the list.

## API verification

The scenario is login → create → list/detail read → update permissions/status/version/`forceUpdate` → reread → error cases. Reset data before each run; record request, stable error code, status and redacted response.

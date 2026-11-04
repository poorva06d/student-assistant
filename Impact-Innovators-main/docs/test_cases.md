# Test Cases

| ID | Scenario | Steps | Expected result |
| --- | --- | --- | --- |
| TC-01 | Register a user | Submit valid required registration fields | Account is created; password is not returned; user can sign in |
| TC-02 | Reject invalid registration | Submit malformed email or password under 6 characters | HTTP 400 with validation details; no account is created |
| TC-03 | Authenticate | Log in with valid credentials | JWT/session data is returned and protected UI becomes available |
| TC-04 | Block private access | Call a protected `/api/study` endpoint without/with invalid JWT | HTTP 401/403; no data is exposed |
| TC-05 | Task lifecycle | Create, update, complete, and delete an owned task | Changes persist; status and dashboard metrics update |
| TC-06 | Ownership check | Attempt to read/update another user's task by ID | Request is rejected; other record is unchanged |
| TC-07 | Study session | Start a session, end it, request sessions/stats | Duration and session record are saved; stats reflect it |
| TC-08 | AI summary | Send authenticated valid text to `/api/gemini/summarize` | A structured success response or safe upstream error is returned |
| TC-09 | AI limit | Exceed configured Gemini request limit | Request is rate-limited with HTTP 429; service remains available |
| TC-10 | File validation | Upload allowed and disallowed/oversize files | Allowed file processes; invalid file is rejected safely |
| TC-11 | Flashcard review | Create card, submit review performance, retrieve due cards | Scheduling fields change and due-card query is accurate |
| TC-12 | Quiz attempt | Open owned quiz and submit answers | Score/answers/timestamp are saved as an attempt |
| TC-13 | Group authorization | Non-admin tries to alter roles or remove members | Request is rejected; membership remains intact |
| TC-14 | Group collaboration | Authorized user sends group message and connected member joins room | Message persists/broadcasts according to API and Socket.IO contract |
| TC-15 | Resource privacy | Access private resource as uploader and unrelated user | Uploader succeeds; unrelated user is denied |
| TC-16 | Calendar lifecycle | Connect test account, create/update/delete study event | Correct external event is managed and errors are comprehensible |
| TC-17 | Frontend quality | Run `npm run lint` and `npm run build` in `frontend/` | Both commands succeed with no blocking errors |
| TC-18 | Health check | Request `GET /health` with database available/unavailable | Returns status and accurately reports database connection state |

Run TC-01 through TC-18 before release, automating the highest-risk authorization, validation, and AI-limit paths first.

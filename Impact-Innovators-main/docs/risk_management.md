# Risk Management

| Risk | Likelihood | Impact | Mitigation | Owner |
| --- | --- | --- | --- | --- |
| Gemini quota/outage or poor output | Medium | High | Rate limits, clear fallback errors, retry policy, output review notice, monitor usage | Backend/AI |
| Exposure of JWTs, OAuth tokens, or API keys | Medium | Critical | Environment-only secrets, token encryption/rotation, least privilege, secret scanning | Security |
| Unauthorized access to another student's data | Medium | Critical | Enforce owner/group-role checks in every controller; integration authorization tests | Backend |
| Malicious or oversized upload | Medium | High | MIME/size validation, malware scanning, object-storage isolation, expiry and cleanup | Backend/DevOps |
| Duplicate source trees cause fixes in wrong module | High | Medium | Declare active paths, consolidate after backup/review, protect with CI | Tech lead |
| Data loss or accidental deletion | Low | High | MongoDB backups, restore drills, soft delete where appropriate, audit trails | DevOps |
| Calendar sync creates duplicate/wrong events | Medium | Medium | Store external event IDs, idempotency keys, explicit timezone tests, confirm destructive actions | Integrations |
| Real-time chat abuse or inappropriate content | Medium | Medium | Authentication, moderation/reporting policy, message limits, retention rules | Product/Backend |
| Missing automated tests regress core flows | High | High | Prioritize auth/study/AI/group API tests and CI gates | QA |
| Third-party dependency vulnerability | Medium | High | Lockfiles, dependency scans, timely upgrades, minimal permissions | DevOps |

Review this register before each release. Escalate critical risks immediately, assign an owner and target date, and record the outcome after mitigation.

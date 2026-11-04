# Project Plan

## Objective

Deliver a dependable AI study companion that turns study material into useful revision tools, helps learners plan work, and enables safe collaboration.

## Delivery phases

| Phase | Scope | Exit criteria |
| --- | --- | --- |
| 1. Foundation | Repository cleanup, environment setup, MongoDB, authentication, CI | App starts from documented setup; protected routes reject invalid tokens |
| 2. Core learning | Tasks, dashboard, study sessions, progress and timer | Students can create, complete, and review study activity |
| 3. AI workflow | Gemini summary, explain, solve, flashcard, quiz, file processing | Input validation, quotas, graceful AI errors, and saved outputs work |
| 4. Planning and collaboration | Calendar sync, groups, resources, real-time room messaging | Access rules protect private content and group workflows are test-covered |
| 5. Hardening and release | Tests, accessibility, observability, security review, deployment | Acceptance tests pass, secrets are configured, rollback is documented |

## Prioritized backlog

1. Establish a single authoritative frontend/backend directory and remove or archive duplicate code after review.
2. Add unit, API integration, and end-to-end tests; the backend `test` script currently intentionally fails.
3. Enforce authorization for every ownership and group-membership operation.
4. Implement reliable upload scanning/retention and storage cleanup.
5. Finish analytics, notifications, resource comments, and calendar edge cases.
6. Add CI for lint, tests, dependency audit, and production build.

## Milestones and measures

- Core release: registration/login, study tasks/sessions, dashboard, and basic AI summarization work end to end.
- Learning release: flashcard review and quiz attempts persist and show progress.
- Collaboration release: group roles, invitations, resources, and messages are secure and usable.
- Production readiness: critical-path test automation, rate-limit monitoring, error logging, and documented incident response.

Success is measured by successful core-flow completion, AI failure rate, API error rate, page performance, study-session completion, and user retention—using aggregate, privacy-respecting telemetry.

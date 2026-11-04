# Requirements

## Functional requirements

| ID | Requirement |
| --- | --- |
| FR-01 | A student shall register with name, email, password, college, major, and year, and sign in with credentials or supported Google authentication. |
| FR-02 | An authenticated student shall view and update profile and study preferences. |
| FR-03 | A student shall create, update, complete, filter, and delete study tasks with due dates and priorities. |
| FR-04 | A student shall start/end study and Pomodoro sessions and view progress, statistics, streaks, and recommendations. |
| FR-05 | A student shall submit text or supported files for AI summary, explanation, study-plan, flashcard, quiz, practice-question, and problem-solving assistance. |
| FR-06 | A student shall create, import, export, search, review, reset, and track flashcards. |
| FR-07 | A student shall access saved quizzes, submit attempts, and delete owned quizzes. |
| FR-08 | A student shall create/join/leave study groups, manage authorized members, schedules, invitations, announcements, resources, and messages. |
| FR-09 | A student shall upload, discover, rate, bookmark, download, and manage permitted learning resources. |
| FR-10 | A student shall connect Google Calendar and create, update, view, sync, and delete study events. |
| FR-11 | The system shall expose a health endpoint and real-time study-room events. |

## Non-functional requirements

- NFR-01 Security: hash passwords, use JWT authentication, validate inputs, restrict CORS, and rate-limit login/API/AI routes.
- NFR-02 Privacy: collect only necessary student data, keep tokens and uploads private, and provide deletion/retention policies before release.
- NFR-03 Reliability: return clear errors for database, upload, calendar, and AI failures; do not corrupt saved work on retries.
- NFR-04 Performance: normal API responses should be prompt; long file/AI work should show progress or use background processing.
- NFR-05 Accessibility: keyboard operation, sufficient contrast, semantic labels, and responsive layouts are required.
- NFR-06 Maintainability: documented environment variables, linting, tests, and a single source of truth for each module.
- NFR-07 Observability: record structured request/error metrics without logging secrets or sensitive content.

## Assumptions and constraints

The platform depends on MongoDB, Gemini availability/quota, Google OAuth/Calendar availability, and configured file storage. AI output is assistive: users must be able to review it and should not treat it as authoritative academic advice.

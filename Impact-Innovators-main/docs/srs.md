# Software Requirements Specification (SRS)

## 1. Purpose

Student Assistant is a browser-based, AI-assisted study platform for college students and self-learners. It reduces the effort of transforming notes and lectures into summaries, revision material, tasks, and collaborative study activity.

## 2. Actors

- **Student:** registered user who manages personal study activity and participates in groups.
- **Group administrator/moderator:** group member with authorization to manage membership and group content.
- **External services:** Gemini, Google OAuth/Calendar, MongoDB, and file/object storage.

## 3. Product scope

The system provides authentication, dashboard/task/session tracking, AI study assistance, flashcards, quizzes, file/resource management, calendar planning, and study groups. It does not guarantee factual correctness of generated content, replace instructors, or provide a native mobile app in the current scope.

## 4. Interfaces

- **Web UI:** React single-page app served by Vite in development and optionally Express in production.
- **HTTP API:** JSON REST endpoints under `/api`; private routes require a bearer JWT.
- **Real-time API:** Socket.IO events for study-room membership, messages, and session updates.
- **External APIs:** Gemini, Google OAuth/Calendar, Supabase/object storage.
- **Health:** `GET /health` reports service/database status.

## 5. Behavioral requirements

The system shall meet FR-01 through FR-11 in [requirements.md](requirements.md). It shall validate incoming data and return appropriate errors without exposing server internals. It shall persist user-owned records in MongoDB and permit access only to authenticated, authorized users. It shall limit AI calls and authentication attempts to reduce abuse.

## 6. Data requirements

The persisted entities are User, Task, StudySession, Flashcard, Quiz, Progress, StudyGroup, Resource, File, Notification, and Analytics. Full ownership, indexes, and field-level intent are specified in [database_design.md](database_design.md).

## 7. Quality attributes

Security, privacy, reliability, accessibility, maintainability, performance, and observability requirements are defined in [requirements.md](requirements.md). Production deployment requires HTTPS, non-default secrets, restricted origins, backup procedures, and monitoring.

## 8. Acceptance criteria

A release is acceptable when a new user can register and log in; manage a task and study session; receive AI assistance for valid input; revise saved cards or quizzes; use authorized group functions; and see understandable errors for invalid, unauthorized, or unavailable-service scenarios. These flows must pass the cases in [test_cases.md](test_cases.md).

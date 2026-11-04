# Database Design

The application uses MongoDB through Mongoose. ObjectId references represent ownership and relationships.

## Core collections

| Collection | Key fields | Relationships |
| --- | --- | --- |
| `users` | name, email (unique), password hash, college, major, year, Google tokens, preferences | owns tasks, sessions, cards, quizzes, files, progress, notifications; bookmarks resources |
| `tasks` | userId, title, subject, priority, status, dueDate, reminders, recurrence | belongs to user; may depend on tasks |
| `studysessions` | userId, subject, topic, start/end, duration, productivity score | belongs to user |
| `flashcards` | userId, subject, question, answer, difficulty, nextReviewDate, interval, easeFactor, reviews | belongs to user |
| `quizzes` | userId, topic, subject, questions, attempts | belongs to user |
| `progresses` | userId, subject, date, study/task/card/quiz metrics | belongs to user |
| `studygroups` | creatorId, members, schedule, resources, invitations, requests, announcements, messages | creator and member references point to users |
| `resources` | title, type, subject, URL, uploadedBy, visibility, ratings, downloads | uploaded by user; user bookmarks reference resources |
| `files` | originalName, storagePath, mimeType, size, category, uploadedBy | belongs to user |
| `notifications` | userId, type, title, message, read state, expiry | belongs to user |
| `analytics` | userId, endpoint, method, statusCode, responseTime, timestamp | optionally associated with user |

## Relationship sketch

```text
User 1--* Task / StudySession / Flashcard / Quiz / Progress / File / Notification
User 1--* Resource (uploadedBy)
User *--* Resource (bookmarkedResources)
User *--* StudyGroup (members)
User 1--* StudyGroup (creatorId)
```

## Existing indexes and constraints

- `users.email` is unique.
- `quizzes.userId` is indexed.
- `progresses` has compound index `{ userId, date, subject }`.
- `notifications` indexes user/read/date and uses a TTL index on `expiresAt`.
- `analytics` indexes timestamp, user/timestamp, and endpoint/timestamp.
- Schema validation restricts enumerations such as task status, resource type, flashcard difficulty, and group roles.

## Design guidance

All queries for private records must filter by authenticated `userId`; group operations must validate creator/admin/member authorization. Google refresh tokens are sensitive and should be encrypted at rest or held by a dedicated secrets/token service. Embedded arrays are suitable for bounded items (quiz questions and flashcard reviews); unbounded group messages, ratings, and analytics should be extracted into collections if data volume grows.

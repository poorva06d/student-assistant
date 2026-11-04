# Architecture

## Overview

Student Assistant is a web application that helps students organise study work, process learning materials with AI, revise with flashcards and quizzes, and collaborate in groups.

```text
React + Vite client
       | HTTPS / Socket.IO
Express + Socket.IO server
 |        |          |          |
MongoDB  Gemini     Google      Supabase / local uploads
          API       Calendar
```

## Client

The `frontend/` application uses React, React Router, Axios, Tailwind CSS, Recharts, and Socket.IO Client. `AuthContext` manages the signed-in user and JWT; `ProtectedRoute` prevents unauthenticated access. Pages include Dashboard, Summarizer, Quiz Session, Doubt Solver, References, Study Session, Groups, and Momentum Planner.

## Server

`backend/server.js` creates the Express HTTP server and Socket.IO instance. It configures CORS, JSON parsing, static uploads, request logging, rate limiting, API routes, health reporting, and graceful shutdown. Controllers contain business logic, Mongoose models persist data, and middleware handles authentication, validation, and limits.

| Area | Route prefix | Responsibility |
| --- | --- | --- |
| Identity | `/api/auth` | registration, login, Google sign-in, profile and preferences |
| AI | `/api/gemini` | ask, explain, summarize, generate plans, flashcards, quizzes, and solve problems |
| Study | `/api/study` | sessions, tasks, progress, statistics, timer, recommendations |
| Revision | `/api/flashcards`, `/api/quizzes` | flashcard lifecycle, reviews, saved quiz attempts |
| Collaboration | `/api/groups` | groups, membership, resources, announcements, schedules, messages |
| Resources | `/api/resources`, `/api/upload` | upload, discover, rate, bookmark, and download learning resources |
| Planning | `/api/calendar` | Google Calendar authorization and study events |

## Data and integrations

MongoDB stores users and learning-domain records. Passwords are hashed with bcrypt; JWT protects private endpoints. Gemini is accessed only through authenticated, rate-limited endpoints. Uploaded files are processed by the file/media utilities (PDF, DOCX, image, audio, and video support) and can use Supabase storage. Calendar endpoints use Google OAuth credentials associated with a user.

Socket.IO supports joining study rooms, room messages, session updates, and group-message broadcasts. REST remains the source of record for persistent domain data.

## Deployment boundaries

In production the Express server can serve `frontend/dist`; locally the frontend runs on Vite and calls the API server (default port 5000). Required configuration belongs in environment variables, including `MONGODB_URI`, JWT secret, Gemini key, Google OAuth credentials, Supabase credentials, `FRONTEND_URL`, and `PORT`. Secrets must never be committed.

## Quality notes

The repository contains duplicated legacy-looking `server/`, root, `client/`, and `frontend/` trees. The active integrated entry points documented here are `backend/server.js` and `frontend/`. Consolidating duplicate modules and adding automated tests are recommended before production deployment.

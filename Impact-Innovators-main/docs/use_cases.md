# Use Cases

## UC-01: Create an account and sign in

**Actor:** Student  
**Preconditions:** The student has access to the web app.  
**Main flow:** The student registers with required details or uses Google sign-in, then logs in. The system validates identity, creates/fetches the profile, and grants access to protected pages.  
**Alternate flow:** Invalid details, duplicate email, invalid credentials, or rate limiting return a clear error.

## UC-02: Plan and record study work

**Actor:** Student  
**Preconditions:** Authenticated.  
**Main flow:** The student creates tasks, sets dates and priorities, starts a focus/study session, records completion, and views dashboard progress, streaks, and recommendations.  
**Outcome:** Personal task, session, and progress data are persisted.

## UC-03: Convert material into revision content

**Actor:** Student  
**Preconditions:** Authenticated; AI quota available.  
**Main flow:** The student enters text or uploads supported material, chooses summary/explanation/flashcard/quiz/plan action, reviews the generated result, and saves useful cards or quiz work.  
**Alternate flow:** Unsupported file, invalid input, upload failure, quota limit, or provider failure gives actionable feedback without losing local work.

## UC-04: Review flashcards and take a quiz

**Actor:** Student  
**Preconditions:** Authenticated; cards or a quiz exist.  
**Main flow:** The student opens due cards, rates recall, then answers quiz questions and submits.  
**Outcome:** Review schedule and quiz attempt/progress metrics update.

## UC-05: Collaborate in a study group

**Actors:** Student, Group administrator  
**Preconditions:** Authenticated; group exists.  
**Main flow:** An administrator creates a group and invites members or reviews join requests. Members access permitted schedules/resources/announcements and exchange messages in the group/study room.  
**Alternate flow:** Non-members and insufficient-role members are denied restricted actions.

## UC-06: Schedule study time

**Actor:** Student  
**Preconditions:** Authenticated; Google Calendar authorization completed for sync functions.  
**Main flow:** The student creates or syncs a study event, views upcoming events, then modifies or removes it when plans change.  
**Outcome:** The event state is reflected in Google Calendar and the app response.

## UC-07: Share a learning resource

**Actor:** Student  
**Preconditions:** Authenticated.  
**Main flow:** The student uploads a permitted resource, describes and classifies it, selects visibility, then others discover, rate, bookmark, or download it subject to access rules.  
**Outcome:** Resource metadata and storage reference are available according to visibility and authorization.

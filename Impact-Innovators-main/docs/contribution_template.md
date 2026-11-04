# Contribution Template

Use this template when opening an issue or pull request.

## Pull request

**Title:** `type: short description`

Types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`.

### Summary

Describe the user-visible change and why it is needed.

### Scope

- Frontend pages/components affected:
- Backend routes/controllers/models affected:
- Database migration or data impact:
- Environment/configuration changes:

### Verification

- [ ] `npm run lint` passes in `frontend/`
- [ ] Relevant frontend flow was tested manually
- [ ] Relevant API endpoints were tested with authenticated and unauthenticated requests
- [ ] Errors and validation cases were checked
- [ ] No secrets, generated logs, or local uploads were added
- [ ] Documentation was updated when behavior or configuration changed

### Screenshots or API examples

Add screenshots for UI changes. For API changes, include request/response examples with sensitive values removed.

### Risks and rollback

State any compatibility, data, security, or third-party-service risk, and how to revert it.

## Issue

**Problem:** What happens now?

**Expected behavior:** What should happen?

**Steps to reproduce:** Numbered, minimal steps.

**Environment:** Browser/OS, branch or commit, API URL, and relevant non-secret configuration.

**Evidence:** Screenshots, console errors, server logs with tokens and personal data removed.

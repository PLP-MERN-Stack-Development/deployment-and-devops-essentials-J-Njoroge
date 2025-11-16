# Real-Time Chat App — Deployment & Monitoring Notes

This README adds monitoring and backup strategy guidance required for Week 7 submission. Use this file to document how the service is monitored, how backups are taken, and where CI/CD screenshots are stored for grading.

## Monitoring

- Use Sentry (or a similar error-tracking tool) to capture server and client errors.
  - Server: install `@sentry/node` and initialize in `server/server.js` when `SENTRY_DSN` is provided.
  - Client: install `@sentry/react` and initialize in the React entry point when `VITE_SENTRY_DSN` is provided.
  - Configure the DSN values as repository secrets or platform environment variables.

- Uptime monitoring: use an external uptime monitor (UptimeRobot, Pingdom) to hit the health endpoint `GET /` regularly.

- Performance monitoring: consider using APM (NewRelic, Datadog) or Render/Vercel built-in metrics to monitor CPU, memory, and response times.

## Backup Strategy

- Database backups (MongoDB Atlas):
  - Use Atlas's built-in backup and snapshot features for production clusters.
  - Configure automated daily snapshots and retain as per course requirements.

- File uploads:
  - Do not rely on local `uploads/` folder for production persistence. Instead use S3-compatible storage (AWS S3, DigitalOcean Spaces) and back up bucket policies.

## CI/CD Evidence (for submission)

- Save screenshots of successful GitHub Actions runs and deployment pages (Render/Vercel) and place them under a `docs/ci-screenshots/` folder in the repo.

- Example structure:

```
docs/
  ci-screenshots/
    github-actions-success.png
    render-deploy.png
```

Include links to the deployed frontend and backend URLs in `report.md` and in this README when available.

---

Document generated on: 2025-11-16

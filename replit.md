# StudyMate

A personal study manager for students to build and track their own syllabus, study materials, schedule, exams, tasks, focus sessions, and progress.

## Run & Operate

- `pnpm --filter @workspace/studymate run dev` — run the StudyMate web app
- `pnpm --filter @workspace/studymate run typecheck` — typecheck the web app
- `PORT=5000 BASE_PATH=/ pnpm --filter @workspace/studymate run build` — create a production build
- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)

StudyMate runs as a local-first web app and does not currently require the API server or database.

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- Frontend: React, Vite, TypeScript, Tailwind CSS
- UI: Lucide icons and the workspace's shadcn-style components
- Persistence: browser `localStorage`
- Build: Vite static bundle

## Where things live

- `artifacts/studymate/src/App.tsx` — StudyMate pages, data model, and interactions
- `artifacts/studymate/src/index.css` — StudyMate visual theme and responsive styles
- `artifacts/studymate/index.html` — document title and social metadata
- `artifacts/api-server` and `lib/` — shared API/database workspace scaffolding; not used by StudyMate

## Architecture decisions

- Start with empty academic content; never seed sample subjects, lessons, topics, or activity.
- Keep student records in versioned browser storage so a student can use StudyMate without an account or external service.
- Browser reminder notifications are optional and only fire while the app is open; due reminders are also visible in the app.

## Product

StudyMate includes a home dashboard; editable subject, lesson, and topic tracking; notes; flashcards and revision; custom quizzes; a weekly timetable; exams; tasks and reminders; focus timers; a smart study planner; and progress tracking.

## User preferences

- Keep all academic content student-created and the initial state completely empty.

## Gotchas

- Browser storage is specific to this browser/device and does not sync across devices. Clearing browser data removes the saved StudyMate records.
- Browser notifications require the student's permission and cannot be delivered while the app is closed.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details

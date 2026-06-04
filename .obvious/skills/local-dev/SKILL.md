---
name: local-dev
version: 1.0.0
description: Bring this repo's local development environment up from scratch.
category: local-dev
triggers:
  - local dev setup
  - run repo locally
  - start dev server
  - bring up local stack
author: autobuild-setup
created: 2026-06-04
---

## Prerequisites

- Node.js 20.x (verified: v20.20.2)
- npm 10.x (verified: 10.8.2)
- MongoDB 8.x -- must be running locally on port 27017 (mongod available at /usr/bin/mongod)
- No Docker or additional runtimes required

## Install

    npm install
    cd frontend && npm install && cd ..

Both node_modules directories must be present. Use package-lock.json (root and frontend) as canonical lockfiles.

## Environment

Create .env at repo root:

    POST=3000
    MONGO_URI=mongodb://127.0.0.1:27017/moviesApp
    NODE_ENV=development
    JWT_SECRET=<any-long-random-string>

All four variables are required. JWT_SECRET can be any string for local dev.

## Start

Start MongoDB (if not pre-running):

    mkdir -p /tmp/mongodb-data
    mongod --dbpath /tmp/mongodb-data --port 27017

Start backend + frontend together:

    npm run fullstack

Or individually:

    npm run backend   # Express on port 3000 with nodemon
    npm run frontend  # Vite on port 5173

Expected: "Successfully connected to MongoDB" + "Server is running on port 3000" + Vite ready on 5173.

## Verify Primary User Flow

1. GET http://localhost:5173 -- React app HTML loads (HTTP 200)
2. POST http://localhost:3000/api/v1/users body={username,email,password} -- returns user object with _id
3. POST http://localhost:3000/api/v1/users/auth body={email,password} -- HTTP 201, sets jwt HttpOnly cookie
4. GET http://localhost:3000/api/v1/genre/genres -- HTTP 200, returns [] on fresh DB
5. GET http://localhost:3000/api/v1/movies/all-movies -- HTTP 200, returns [] on fresh DB

Evidence (2026-06-04):
- fl_7OB1DUtP: Home page loaded (tc-1)
- fl_GHmxkGV0: Post-auth state (tc-2 before)
- fl_2G9ah4gw: Movies page (tc-2 after)

## Verified Commands

- Typecheck: not_discovered (JavaScript only -- no TypeScript)
- Lint: cd frontend && npx eslint . --ext js,jsx
- Test: not_discovered (no test suite)

## Sandbox Snapshot

- snapshotId: rztrw1xu43hls9zlpcck:default

## Known Blockers / Workarounds

- Port 3000 already in use: A node process from the snapshot runs backend/index.js. Reuse or kill and restart.
- MongoDB socket owned by root: /tmp/mongodb-27017.sock may be owned by root. Use system mongod (PID 2197) or specify a fresh dbpath.
- ESLint prop-types: 34 pre-existing warnings in frontend codebase. Not blocking.

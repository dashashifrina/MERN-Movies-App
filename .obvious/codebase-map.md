# Codebase Map

| Directory | Purpose |
|---|---|
| `backend` | Express.js REST API — routes, controllers, models, middlewares |
| `backend/config` | MongoDB connection setup (`db.js`) |
| `backend/controllers` | Route handler logic — users, genres, movies |
| `backend/middlewares` | JWT auth, admin authorization, request ID checks |
| `backend/models` | Mongoose schemas — User, Genre, Movie |
| `backend/routes` | Express router definitions for each resource |
| `backend/utils` | Shared helpers (e.g. JWT creation) |
| `frontend` | React 18 + Vite SPA |
| `frontend/src/pages` | Page-level components — Auth, Movies, Admin, Home, User |
| `frontend/src/component` | Shared UI components (GenreForm, Loader, Modal, SliderUtil) |
| `frontend/src/redux` | Redux Toolkit store, API slices, feature slices |
| `.github` | (empty — no CI workflows present) |

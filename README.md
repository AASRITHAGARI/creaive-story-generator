# Creative Story Generate

Full-stack web app for playful story generation, translation, history, and animated visuals.

## Stack
- Frontend: React + Vite + TypeScript, React Query, Zustand, Framer Motion
- Backend: Express 5, MongoDB (with in-memory fallback), Mongoose
- Animations: lightweight SVG/Framer Motion

## Quick start
1. Backend
   ```bash
   cd server
   cp .env.example .env
   # set MONGODB_URI if you want persistence; otherwise memory store is used
   npm run dev
   ```
2. Frontend
   ```bash
   cd frontend
   cp .env.example .env    # optional: override API base
   npm run dev             # opens on http://localhost:5173
   ```

## API (summary)
- `POST /stories` → generate + save story `{ prompt }`
- `GET /stories` → list history for the session (cookie-based)
- `DELETE /stories/:id` → delete one
- `POST /stories/clear` → clear all
- `POST /translate` → translate `{ text, targetLang, storyId? }` (cached when storyId supplied)

## Notes
- If `MONGODB_URI` is absent or fails, the API transparently uses an in-memory store.
- The frontend keeps translations per-story in memory; backend caches when storyId is passed.
- Theme preference persists via `localStorage` and the `<html data-theme>` attribute.

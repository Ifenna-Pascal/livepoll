# LivePoll

Run live quizzes and polls from a big screen. A host builds a presentation of timed questions, players join from their phones, vote, chat, and climb a live leaderboard.

| Folder | What it is | Stack |
| --- | --- | --- |
| [`apps/api`](apps/api) | REST API, auth, game state | Go, Gin, PostgreSQL, sqlc, JWT, Swagger |
| [`apps/web`](apps/web) | Host and player web app | React 19, TypeScript, Vite, Tailwind CSS |

## Run it locally

You need Go 1.22+, Node 20+ and Docker.

```bash
# 1. API + database
cd apps/api
cp app.env.example app.env
docker compose up -d postgres
go run ./cmd/rest          # http://localhost:8081, Swagger at /swagger/index.html

# 2. Web app (new terminal)
cd apps/web
npm install
npm run dev                # http://localhost:5173, forwards /api to the Go server
```

Or run everything in containers: `cd apps/api && docker compose up --build` (web on http://localhost:3000).

## Tests

```bash
cd apps/api && go test ./...
cd apps/web && npm test
```

Each app has its own README with more detail. This repo combines the former `live-quiz-api` and `live-quiz-web` repos, with their full commit history.

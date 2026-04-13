# ProjectKit

Open-source project management platform with conversational AI task execution. Fork and customize for your use case.

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | NestJS 11, TypeScript, PostgreSQL 16 + Prisma 6, Redis + BullMQ, Socket.io |
| Frontend | Next.js 16, React 19, Tailwind CSS 4, Radix UI, dnd-kit |
| AI | OpenAI / Anthropic / OpenRouter / Ollama, in-app browser automation |

## Features

- **AI Task Execution** - conversational AI executes project management actions directly in-app
- **Multiple Views** - Kanban, List, Gantt, Calendar
- **Sprint Planning** - agile workflow with custom statuses
- **Multi-tenant** - Organization > Workspace > Project > Task hierarchy
- **Real-time** - WebSocket live updates
- **Rich Text** - Tiptap editor with file attachments
- **Email Integration** - SMTP + IMAP inbox sync
- **Docker Ready** - one-command dev/prod setup
- **Self-hosted** - bring your own LLM, your data stays on your infra

## Quick Start

### Prerequisites

- Node.js 22+, npm 10+
- PostgreSQL 16+
- Redis 7+

### Docker (Recommended)

```bash
git clone https://github.com/Curious1008/ProjectKit.git
cd ProjectKit
cp .env.example .env
docker compose -f docker-compose.dev.yml up
```

### Manual

```bash
git clone https://github.com/Curious1008/ProjectKit.git
cd ProjectKit
cp .env.example .env    # edit secrets before use
npm install
npm run db:migrate
npm run db:seed
npm run dev
```

- Frontend: http://localhost:3001
- Backend API: http://localhost:3000
- API Docs: http://localhost:3000/api/docs

## Project Structure

```
ProjectKit/
├── backend/              # NestJS API (port 3000)
│   ├── src/modules/      # 38+ feature modules
│   ├── prisma/           # schema + migrations
│   └── uploads/
├── frontend/             # Next.js (port 3001)
│   ├── src/components/   # UI components
│   ├── src/contexts/     # auth, chat, task state
│   ├── src/lib/          # browser automation, API client
│   └── public/
├── docker/               # entrypoints
├── scripts/              # build utilities
└── docker-compose*.yml
```

## Commands

```bash
npm run dev              # start both frontend + backend
npm run build            # production build
npm run db:migrate       # run migrations
npm run db:seed          # seed sample data
npm run db:studio        # Prisma GUI
npm run test             # run all tests
npm run lint             # lint all workspaces
```

## AI Setup

1. Go to Settings > Organization > AI Assistant
2. Toggle "Enable AI Chat", add your LLM API key
3. Open the AI chat panel and start managing tasks via conversation

Supported providers: OpenRouter, OpenAI, Anthropic, Ollama (local)

## Customization

This is a template. To adapt for your project:

1. Update `.env.example` and `.env` with your config
2. Modify `backend/prisma/schema.prisma` for your data model
3. Add/remove modules in `backend/src/modules/`
4. Customize UI components in `frontend/src/components/`
5. Update branding in `frontend/public/`

## License

Business Source License - see [LICENSE.md](LICENSE.md)

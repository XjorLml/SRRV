# SRRV

> _Short project description goes here._

---

## Tech Stack

- **Framework** — [Next.js 14](https://nextjs.org/) (App Router)
- **Database** — [Supabase](https://supabase.com/) (PostgreSQL)
- **ORM** — [Prisma](https://www.prisma.io/)
- **Auth** — [Auth.js v5](https://authjs.dev/)
- **UI** — [shadcn/ui](https://ui.shadcn.com/) + [Tailwind CSS](https://tailwindcss.com/)

---

## Prerequisites

Make sure you have the following installed:

- [Node.js](https://nodejs.org/) `v18+`
- [pnpm](https://pnpm.io/) `v8+` — `npm install -g pnpm`
- [Git](https://git-scm.com/)

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/XjorLml/SRRV.git
cd SRRV
```

### 2. Install dependencies

```bash
pnpm install
```

### 3. Set up environment variables

```bash
cp .env.example .env
```

Fill in the required values in `.env`:

```env
# Auth.js
AUTH_SECRET=        # generate with: openssl rand -base64 32
AUTH_GITHUB_ID=     # from GitHub OAuth App settings
AUTH_GITHUB_SECRET= # from GitHub OAuth App settings

# Supabase
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=

# Prisma / Database
DATABASE_URL=       # Supabase connection string (pooled)
DIRECT_URL=         # Supabase direct connection string
```

> **Where to get these:**
> - `AUTH_SECRET` → run `openssl rand -base64 32` in terminal
> - Supabase keys → [Supabase Dashboard](https://supabase.com/dashboard) → Project → Settings → API
> - GitHub OAuth → GitHub → Settings → Developer settings → OAuth Apps → New OAuth App
>   - Homepage URL: `http://localhost:3000`
>   - Callback URL: `http://localhost:3000/api/auth/callback/github`

### 4. Set up the database

```bash
# Push Prisma schema to Supabase
pnpm prisma db push

# (Optional) Seed the database
pnpm prisma db seed

# (Optional) Open Prisma Studio
pnpm prisma studio
```

### 5. Run the development server

```bash
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## Project Structure

```
src/
├── app/             # Next.js App Router pages and layouts
├── components/      # Reusable UI components
│   └── ui/          # shadcn/ui components
├── lib/             # Utility functions and config
│   ├── auth.ts      # Auth.js configuration
│   ├── prisma.ts    # Prisma client instance
│   └── supabase/    # Supabase client (server + client)
├── actions/         # Next.js Server Actions
└── types/           # TypeScript type definitions
prisma/
└── schema.prisma    # Database schema
```

---

## Available Scripts

| Command | Description |
|---|---|
| `pnpm dev` | Start development server with Turbopack |
| `pnpm build` | Build for production |
| `pnpm start` | Start production server |
| `pnpm lint` | Run ESLint |
| `pnpm prisma studio` | Open Prisma database GUI |
| `pnpm prisma db push` | Sync schema to database |

---

## Environment Variables Reference

| Variable | Required | Description |
|---|---|---|
| `AUTH_SECRET` | ✅ | Auth.js encryption secret |
| `AUTH_GITHUB_ID` | ✅ | GitHub OAuth App client ID |
| `AUTH_GITHUB_SECRET` | ✅ | GitHub OAuth App client secret |
| `NEXT_PUBLIC_SUPABASE_URL` | ✅ | Supabase project URL |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | ✅ | Supabase anon/public key |
| `SUPABASE_SERVICE_ROLE_KEY` | ✅ | Supabase service role key (server only) |
| `DATABASE_URL` | ✅ | Pooled DB connection string for Prisma |
| `DIRECT_URL` | ✅ | Direct DB connection string for migrations |

---

## License

MIT

# Your Drip Studio

A modern and stylish web application for creating, showcasing, and managing fashion "drip" collections. Built with a clean UI, responsive design, and smooth user experience.

---

## 🚀 Features

- 🎨 Modern responsive UI with dark mode support
- ⚡ Fast SSR with TanStack Start on Cloudflare Workers
- 📱 Mobile-friendly design
- 🛍️ Product showcase interface
- 🔐 Supabase-powered backend
- 💳 Cashfree payment integration (coming soon)

---

## 🛠️ Tech Stack

- **Framework**: TanStack Start (React 19 + SSR)
- **Routing**: TanStack Router (file-based)
- **Styling**: Tailwind CSS v4 + shadcn/ui
- **Backend**: Supabase (Postgres + Auth + Storage)
- **Deploy**: Cloudflare Workers via Wrangler
- **Package Manager**: Bun

---

## 📂 Project Structure

```
your-drip-studio/
│
├── public/                  # Static assets
├── src/
│   ├── routes/              # File-based routes (TanStack Router)
│   │   ├── __root.tsx       # HTML shell + providers
│   │   └── index.tsx        # Home page
│   ├── components/          # Reusable UI components
│   │   └── ui/              # shadcn/ui components
│   ├── lib/
│   │   ├── supabase.ts      # Supabase client (browser)
│   │   └── utils.ts         # cn() helper
│   ├── hooks/               # Custom React hooks
│   ├── styles.css           # Global Tailwind CSS
│   ├── router.tsx           # Router factory
│   ├── client.tsx           # Browser hydration entry
│   └── server.ts            # Cloudflare Workers SSR entry
│
├── .env                     # Local env vars (never commit!)
├── .env.example             # Safe template to commit
├── wrangler.jsonc           # Cloudflare Workers config
├── vite.config.ts           # Vite + TanStack Start config
├── tsconfig.json            # TypeScript config
├── components.json          # shadcn/ui config
└── package.json
```

---

## ⚙️ Setup

### 1. Install dependencies
```bash
bun install
```

### 2. Configure environment
```bash
cp .env.example .env
# Fill in your Supabase and Cashfree keys
```

### 3. Run locally
```bash
bun dev
```

### 4. Type-check
```bash
bun run typecheck
```

### 5. Build & deploy
```bash
bun run build
wrangler deploy
```

---

## 🔐 Environment Variables

| Variable | Required | Description |
|---|---|---|
| `VITE_SUPABASE_URL` | ✅ | Your Supabase project URL |
| `VITE_SUPABASE_PUBLISHABLE_KEY` | ✅ | Supabase anon/public key |
| `SUPABASE_URL` | ✅ (server) | Same URL for SSR/edge functions |
| `SUPABASE_PUBLISHABLE_KEY` | ✅ (server) | Same key for SSR/edge functions |
| `VITE_CASHFREE_APP_ID` | 💳 | Cashfree App ID (client-side) |
| `CASHFREE_SECRET_KEY` | 💳 | Cashfree Secret (server-side only!) |

> ⚠️ **Never commit `.env`** — it's in `.gitignore`. Use `.env.example` as a safe template.

---

## 🔒 Security Checklist Before Publishing

- [ ] Enable Row Level Security (RLS) on all Supabase tables
- [ ] Verify `.env` is in `.gitignore` and not tracked by Git
- [ ] Cashfree `SECRET_KEY` is only in server-side env (never `VITE_`-prefixed)
- [ ] Add your production domain to Supabase "Allowed URLs" settings

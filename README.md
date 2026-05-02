# Chaos Journal 

A high-speed, high-vibe thought dumping ground. Built to catch ideas before they disappear, automatically delete the garbage, and permanently store the gems. 

## The Architecture (The Stack)

This project uses a decoupled Monorepo structure.

**Backend (The Engine):**
*   **Golang**: Core logic and speed.
*   **Gin**: Lightweight HTTP web framework for REST API routing.
*   **MongoDB Atlas**: Database storage with native TTL (Time-To-Live) index support.

**Frontend (The Vibe):**
*   **React (Vite) + TypeScript**: Fast, unbloated UI rendering.
*   **Tailwind CSS**: Utility-first styling.
*   **Shadcn UI**: Pre-built, customizable component system.
*   **Framer Motion**: Smooth, non-boring animations (fade-outs, expiration shakes).
*   **Lucide-React**: Clean, consistent iconography.

---

## 🧠 The Core Mechanics (How It Works)

The journal is divided into four distinct buckets, fed by a single "Quick Dump" input.

1.  **Random ⏱️**: The default landing zone. Thoughts live here temporarily. MongoDB automatically deletes them after a set time via TTL indexes unless they are promoted.
2.  **Useful 🔍**: The cheatsheet zone. Standard storage for things like commands, links, or facts. Equipped with fuzzy search to find things instantly.
3.  **Immortal 🏛️**: The permanent gallery. High-contrast, clean UI for top-tier ideas and long-term storage. No expiration.
4.  **Graveyard 🪦**: The purgatory. Where expired "Random" thoughts go to sit for 30 days before permanent deletion.

### "The Magic" Features
*   **Auto-Decay**: Zero background-jobs required. MongoDB handles the timers.
*   **Promotion System**: One-click API endpoints to move a document from "Random" to "Immortal" or "Useful".
*   **Fuzzy Search**: Instantly filter the "Useful" tab based on tags or partial text matches.

---

## 📂 Project Structure
```text
chaos-journal/
│
├── backend/                 # Golang API Engine
│   ├── db/                  # MongoDB connection and queries
│   ├── handlers/            # API route logic (Promote, Delete, Fetch)
│   ├── models/              # Go structs defining our 4 data buckets
│   ├── main.go              # Server initialization
│   └── .env                 # Database URI and Port
│
├── frontend/                # React/Vite UI
│   ├── src/
│   │   ├── components/      # Shadcn components (Cards, Inputs)
│   │   ├── pages/           # The 4 main view tabs
│   │   ├── api/             # Fetch calls to the Go backend
│   │   └── App.tsx          # Main layout and router
│   ├── tailwind.config.js   # Styling rules
│   └── package.json         # UI dependencies
│
└── README.md                # You are here

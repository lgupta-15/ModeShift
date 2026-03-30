# ModeShift — Architecture Overview

## System Architecture

ModeShift follows a standard **client-server architecture**:

- The **Flutter mobile app** is the client — what the user sees and interacts with
- The **Node.js + Express backend** is the server — handles all logic, data, and communication
- The **PostgreSQL database (Supabase)** stores all user data, mode configurations and logs
- **Twilio API** handles all SMS and call interception

---

## Architecture Diagram
```
┌─────────────────────────────────────────────────────┐
│                   Flutter Mobile App                 │
│         (User Interface + Mode Controls)             │
└───────────────────────┬─────────────────────────────┘
                        │ HTTPS REST API
                        ▼
┌─────────────────────────────────────────────────────┐
│              Node.js + Express Backend               │
│         (Business Logic + API Endpoints)             │
└──────────┬─────────────────────────┬────────────────┘
           │                         │
           ▼                         ▼
┌─────────────────┐       ┌─────────────────────────┐
│   PostgreSQL DB  │       │        Twilio API        │
│   (Supabase)     │       │  (Calls + SMS Handling)  │
└─────────────────┘       └─────────────────────────┘
```

---

## How it Works — Step by Step

1. User opens the Flutter app and selects a mode (e.g. Driver Mode)
2. App sends a request to the backend — "activate driver mode for this user"
3. Backend updates the database — stores the active mode
4. An incoming call or SMS hits Twilio
5. Twilio asks our backend — "what should I do with this call/SMS?"
6. Backend checks the database — sees Driver Mode is active
7. Backend tells Twilio — "send an auto-reply, check if it's an emergency"
8. Twilio handles the call/SMS accordingly

---

## Key Design Decisions

| Decision | Reason |
|----------|--------|
| Flutter for mobile | Cross-platform — works on Android and iOS from one codebase |
| Node.js for backend | Fast to develop, JavaScript everywhere, huge community |
| Supabase for DB | Real PostgreSQL, built-in auth, real-time capable, free tier |
| Twilio for calls/SMS | Industry standard, reliable, well-documented API |
| Railway for deployment | Simplest deployment experience, free tier, GitHub integration |

---

## Tech Stack Versions

| Technology | Version |
|-----------|---------|
| Flutter | Latest stable |
| Node.js | v20 LTS |
| Express | v4 |
| PostgreSQL | v15 |
| Supabase JS SDK | Latest |
| Twilio SDK | Latest |

---

*Last updated: March 2025*

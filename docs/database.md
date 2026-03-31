# ModeShift — Database Design

## Overview

ModeShift uses **PostgreSQL** hosted on **Supabase** as its database.
All user data, mode configurations, contact rules and activity logs are stored here.

---

## Tables

### 1. `users`
Stores all registered users.

| Column | Type | Description |
|--------|------|-------------|
| `id` | `uuid` | Primary key, auto-generated |
| `email` | `varchar` | User's email address |
| `password_hash` | `varchar` | Hashed password — never stored as plain text |
| `phone_number` | `varchar` | User's phone number for Twilio |
| `created_at` | `timestamp` | Account creation time |
| `updated_at` | `timestamp` | Last update time |

---

### 2. `modes`
Stores system-wide mode definitions. Shared across all users.

| Column | Type | Description |
|--------|------|-------------|
| `id` | `uuid` | Primary key, auto-generated |
| `name` | `varchar` | Mode name (e.g. Drive, Sleep, Study) |
| `description` | `text` | What this mode does |
| `icon` | `varchar` | Icon identifier for the UI |
| `created_at` | `timestamp` | When this mode was added |

**V1 modes:**
- 🚗 Drive Mode
- 😴 Sleep Mode
- 📚 Study Mode

---

### 3. `user_mode_configs`
Stores each user's personal configuration for each mode.

| Column | Type | Description |
|--------|------|-------------|
| `id` | `uuid` | Primary key, auto-generated |
| `user_id` | `uuid` | Foreign key → `users.id` |
| `mode_id` | `uuid` | Foreign key → `modes.id` |
| `auto_reply_message` | `text` | Custom auto-reply text |
| `allow_emergency` | `boolean` | Whether to allow emergency calls through |
| `emergency_keyword` | `varchar` | Keyword that triggers emergency (e.g. "urgent") |
| `allowed_contacts` | `text[]` | List of contacts always allowed through |
| `is_active` | `boolean` | Whether this mode is currently active |
| `created_at` | `timestamp` | When config was created |
| `updated_at` | `timestamp` | Last update time |

---

### 4. `activity_logs`
Stores a log of every call/SMS handled by ModeShift.

| Column | Type | Description |
|--------|------|-------------|
| `id` | `uuid` | Primary key, auto-generated |
| `user_id` | `uuid` | Foreign key → `users.id` |
| `mode_id` | `uuid` | Foreign key → `modes.id` |
| `contact_number` | `varchar` | The number that called or texted |
| `type` | `varchar` | `call` or `sms` |
| `action_taken` | `varchar` | `auto_replied`, `allowed`, `blocked` |
| `was_emergency` | `boolean` | Whether it was flagged as emergency |
| `created_at` | `timestamp` | When this event happened |

---

## Relationships
```
users
  └── user_mode_configs (one user → many mode configs)
        └── modes (many configs → one mode)

users
  └── activity_logs (one user → many logs)
        └── modes (many logs → one mode)
```

---

## Key Design Decisions

| Decision | Reason |
|----------|--------|
| UUID as primary keys | Harder to guess than integers — more secure |
| Separate `modes` and `user_mode_configs` tables | Mode definitions are shared — user settings are personal |
| `password_hash` not `password` | Never store plain text passwords |
| `allowed_contacts` as array | A user can whitelist multiple contacts per mode |
| Separate `activity_logs` table | Keeps history clean and separate from config |
| `is_active` on config level | Only one mode should be active at a time per user |

---

*Last updated: March 2026*

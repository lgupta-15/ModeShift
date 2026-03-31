# ModeShift 📱

> A smart, context-aware phone mode application that automatically manages your calls, messages, and notifications based on your current activity.

![Status](https://img.shields.io/badge/Status-In%20Development-yellow)
![License](https://img.shields.io/badge/License-All%20Rights%20Reserved-red)
![Platform](https://img.shields.io/badge/Platform-Android%20%7C%20iOS-blue)

---

## 🧠 What is ModeShift?

ModeShift lets you activate a **context mode** based on what you're doing — and your phone handles everything automatically from there.

No more manually silencing your phone. No more missed emergencies. No more distractions.

---

## 🚦 Modes

| Mode | What it does |
|------|-------------|
| 🚗 **Driver Mode** | Auto-replies to calls/texts, detects emergencies, picks up only if critical |
| 😴 **Sleep Mode** | Blocks everything except close contacts and alarms |
| 📚 **Focus Mode** | Silences all, sends auto-reply "I'm currently focusing" |
| 💪 **Gym Mode** | Blocks calls, allows music notifications only |
| 💼 **Meeting Mode** | Professional auto-reply, calendar-aware |

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Mobile App | Flutter |
| Backend | Node.js + Express |
| Database | PostgreSQL (Supabase) |
| Authentication | Supabase Auth |
| SMS/Call Handling | Twilio API |
| Deployment | Railway (backend) + Supabase (DB) |

---

## 📁 Project Structure
```
ModeShift/
├── README.md
├── .gitignore
├── docs/
│   ├── architecture.md
│   ├── api.md
│   ├── database.md
│   └── setup.md
├── backend/
│   └── (Node.js + Express server)
└── frontend/
    └── (Flutter mobile app)
```

---

## 📄 Documentation

- [Architecture Overview](docs/architecture.md)
- [API Documentation](docs/api.md)
- [Database Design](docs/database.md)
- [Setup Guide](docs/setup.md)

---

## 🗺️ Roadmap

- [ ] Project setup & folder structure
- [ ] Backend — authentication & user management
- [ ] Backend — mode configuration APIs
- [ ] Flutter app — UI & mode switching
- [ ] Twilio integration — call & SMS handling
- [ ] Testing & bug fixes
- [ ] Deployment

---

## 👨‍💻 Author

**lgupta-15**
© 2025 lgupta-15. All rights reserved. You may copy this code but may not modify or redistribute it.

---

> *"Your phone should adapt to your life — not interrupt it."*


ModeShift — The Plan
What it does:
You activate a mode (Drive, Sleep, Focus, Gym, Meeting) and ModeShift automatically handles your calls and messages intelligently based on that context.
The Stack I'd recommend for you:
LayerTechWhyMobile AppFlutterYou already know itBackendNode.js + ExpressSimple, JS everywhere, huge communityDatabasePostgreSQL + SupabaseEasy to set up, real-time capable, free tierAuthSupabase AuthBuilt-in, saves tons of timeSMS/Call handlingTwilio APIIndustry standardDeploymentRailway (backend) + Supabase (DB)Free tiers, easy

Month breakdown:

Week 1 — Backend basics, auth, database, REST APIs
Week 2 — Flutter app, connect to backend, mode switching UI
Week 3 — Twilio integration, call/SMS handling per mode
Week 4 — Polish, testing, deploy everything

Why Flutter — obvious, you know it already. No debate there.

Why Node.js over the alternatives:

Python (Django/FastAPI) — great, very popular, but you'd have to learn Python syntax + a new framework from scratch. Node.js is JavaScript which is closer to Dart (Flutter's language) in style, so the mental jump is smaller.
Java/Spring Boot — very traditional, used heavily in enterprises, but extremely verbose and slow to get started. Not ideal for a one-month project.
Go — modern, fast, but small community and steeper learning curve for beginners.
Node.js — JavaScript runs everywhere, massive community, tons of tutorials, fast to prototype. Best choice when you want to move fast and learn deeply at the same time.


Why Supabase over the alternatives:

Firebase — most famous, but Google-owned, can get expensive, and hides a lot of the backend from you. You'd learn less about how databases actually work.
Raw PostgreSQL on a VPS — great for learning but too much DevOps overhead for month one.
MongoDB — popular but NoSQL, and for an app like ModeShift relational data (users, modes, rules, contacts) fits SQL much better.
Supabase — gives you real PostgreSQL, built-in auth, real-time, and a simple dashboard. Open source. Free tier is generous. And you actually learn SQL properly.


Why Railway over alternatives:
AWS/GCP/Azure — powerful but overkill and confusing for a first deployment. You'd spend a week just on configuration.
Heroku — was the classic choice but killed its free tier.
Railway — simplest deployment experience right now, free tier, deploys directly from GitHub. Perfect for first project.
Simply put:
Right now if you build an app, it runs on your laptop. Only you can use it. The moment you close your laptop, it's gone.
Deployment means putting your app on a computer that's always on, always connected to the internet — so anyone in the world can access it, anytime, even when your laptop is off.
That "always on computer" is called a server — and companies like Railway, AWS, Vercel etc. basically rent you that server.

What actually happens when you deploy:

You push your code to GitHub
Railway (or wherever) picks it up
It runs your code on their servers
They give you a public URL like modeshift.up.railway.app
Anyone types that URL → they're using your app


For ModeShift specifically you'll deploy:

The backend (Node.js) → on Railway
The database (PostgreSQL) → on Supabase
The mobile app (Flutter) → on Play Store / App Store or as an APK for now

The Core Concept — Branches
Never work directly on the main branch. Think of it like this:

main = the live, working, production version of your app. Sacred. Never broken.
You always create a separate branch to work on a feature, then merge it back when it's done and tested.


The Professional Workflow Step by Step:
1. Project Structure on GitHub

One repo for the whole project — modeshift
A good README.md from day one — what the app is, how to run it, tech stack
A .gitignore file — so passwords and junk files never get uploaded
Protect your main branch — no direct pushes allowed


2. Branch Naming Convention
Always name branches clearly:
feature/driver-mode
feature/user-auth
fix/login-crash
chore/setup-database
docs/update-readme

3. The Daily Workflow
1. Pull latest main
2. Create a new branch for your task
3. Write code
4. Commit regularly with clear messages
5. Push branch to GitHub
6. Open a Pull Request (PR)
7. Review it yourself (or with others)
8. Merge into main
9. Delete the branch

4. Commit Messages — the right way
Bad commits (what most beginners do):
"fixed stuff"
"changes"
"asdfgh"
"final version"
"final version 2"
Good commits (professional):
"feat: add driver mode auto-reply logic"
"fix: crash when no contacts found"
"chore: setup supabase connection"
"docs: add setup instructions to README"
This format is called Conventional Commits — used across the industry.

5. Issues + Project Board
Use GitHub's built-in tools:

Issues — every feature or bug is an issue. Like a to-do list tied to your code.
Project Board — a Kanban board (To Do → In Progress → Done) right inside GitHub
Link every branch and PR to an issue — keeps everything traceable


6. The Full Picture
Issue created → branch created → code written → 
commits made → PR opened → merged → issue closed
Every single change in your codebase has a story. You can look back 6 months later and know exactly why you wrote something.

For ModeShift specifically I'd suggest:

main — production only
dev — your main working branch, merge features here first
feature/xyz — individual features branch off from dev
Only merge dev into main when a full version is ready

C:\Users\erlak>git --version
git version 2.45.2.windows.1

C:\Users\erlak>git config --global --list
user.name=lgupta-15
user.email=erlakshitanitj@gmail.com

AWS/GCP/Azure — powerful but overkill and confusing for a first deployment. You'd spend a week just on configuration.
Heroku — was the classic choice but killed its free tier.
Railway — simplest deployment experience right now, free tier, deploys directly from GitHub. Perfect for first project.


FieldValueRepository namemodeshiftDescriptionA smart context-aware phone mode appVisibilityPublicAdd a README✅ Check thisAdd .gitignoreChoose Node from the dropdownChoose a licenseMIT License
Why Public visibility?

Private means only you can see the code. Public means anyone can.
For a learning project, public is better because:

It builds your portfolio — employers and collaborators can see your work
It shows your GitHub activity (the green squares on your profile)
The open source community can give you feedback


You're not building anything secretive here, so public makes total sense


Why .gitignore?
When you write code, your project folder will have files that should never be uploaded to GitHub:

Secret keys and passwords (like your Supabase key, Twilio key)
Heavy folders like node_modules (thousands of files, not your code)
System junk files like .DS_Store on Mac

.gitignore is a file that tells Git — "ignore these files, never upload them."
Without it you could accidentally push your passwords to the internet. It's happened to thousands of developers and it's a serious problem.

Why MIT License?
A license tells people what they can and can't do with your code. Without a license, legally nobody can use or learn from your code even if it's public.
MIT License is the most common open source license — it basically says:

Anyone can use, copy, learn from this code
Just give me credit
I'm not responsible if something breaks

It's the standard choice for personal and open source projects.

Now let's add them
Adding .gitignore:

In your repo on GitHub click Add file → Create new file
Name it exactly .gitignore (with the dot)
Go to 👉 https://gitignore.io
Type Node and Flutter → click Create
Copy everything → paste it into your .gitignore file on GitHub
Scroll down → click Commit changes → Commit directly to main


Adding License:

In your repo click Add file → Create new file
Name it LICENSE
On the right side GitHub will show a button Choose a license template — click it
Select MIT License
Put your name in the name field
Click Review and submit
Commit it to main

Keep Twilio in the architecture — but mock it during development.
Meaning your backend will have the exact same logic, same API structure, same database — but instead of actually sending SMS during dev, we log it to the console. Then when you're ready to demo, you use Twilio's free trial credit for just that demo.
This way:

Your portfolio shows real full stack architecture
You learn the correct patterns
You spend zero dollars during building
You can swap real Twilio in with literally one config change

Flutter → Route → Middleware → Controller → Model → Database
                                    ↓
                                Services
                                (Twilio)


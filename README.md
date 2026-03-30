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

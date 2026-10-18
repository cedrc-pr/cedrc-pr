# Hi, I'm Cédric

Full-stack developer, currently heading toward DevOps. Third-year student at École 89 (alternance / work-study program), aiming for a DevOps master's next.

**Open to a DevOps alternance starting September/October 2027**: [LinkedIn: cedric-prin](https://www.linkedin.com/in/cedric-prin) - cedric.prin@free.fr

> **Why is my GitHub so quiet?**
> 
> All of my school, work and personal projects live on private Git servers or on my own self-hosted Forgejo instance. I treat this GitHub profile as a showcase and portfolio rather than my day-to-day workspace.

# Infra & DevOps

Infrastructure and DevOps are my main focus for the future, I’m already teaching myself about those subjects alongside my studies and my work-study program.

**Infrastructure**

Linux (fedora, debian, ubuntu), networking (VPC/VCN, subnets, routing, security rules), Bash, systemd (service management), SSH (hardening), ufw/firewalld, CrowdSec/fail2ban

**Automation**

Ansible (playbooks, roles, vault), Terraform (Infrastructure as Code), Oracle Cloud Infrastructure (OCI), ghcr.io (container registry), GitHub Actions (workflows, CI/CD pipelines)

**Containers**

Docker, Docker compose, Docker networking (custom subnets, container ↔ host communication), Traefik (reverse proxy, secure headers, Let's Encrypt)

**Monitoring**

Prometheus, Grafana, node-exporter, cAdvisor

I've also had an introduction covering the basics of AWS, and have since been working with Terraform and Oracle Cloud Infrastructure (OCI) for my own infrastructure.

> **Why OCI?**
> I’m teaching myself all these concepts, and OCI offers a very interesting ‘always free’ tier.

## DevOps projects

### Full CI/CD project

Three of my projects work together as a small CI/CD system built around my home server: **infra** provisions the server, **copit** is the app deployed on it, and **deployer** is the daemon that safely triggers each redeploy.

[infra](https://github.com/cedrc-pr/infra) — Terraform and Ansible infrastructure project:
- Terraform provisions the cloud resources on Oracle Cloud Infrastructure (OCI), including the network, subnet, routing, security rules and ARM virtual machine.
- Ansible then configures the servers from scratch: SSH hardening, automatic security updates, ufw or firewalld, CrowdSec or fail2ban, Docker, and Traefik as a reverse proxy with Let's Encrypt and secure headers.
- It also contains the roles that deploy copit and deployer themselves.

[copit](https://github.com/cedrc-pr/copit) — password-protected chat rooms for sharing code snippets or long links between devices. Built with a Rust API (WebSockets, Redis) and a React frontend; it's the app this whole CI/CD pipeline was first built around.

[deployer](https://github.com/cedrc-pr/deployer) — a Rust daemon that receives an authenticated request from GitHub Actions after an image push and runs the redeploy script for the matching service. Runs as a systemd service, bound to a dedicated Docker subnet so the Traefik container can reach it without exposing it directly or sharing the host network.

**Workflow**: a push on copit's main branch can lead to building and pushing the images to ghcr.io, then calls deployer with a bearer token to redeploy — no SSH access needed on the CI side. The deployer runs a script that try to deploy the new version, and rollback if any error occurs.

### Python projects

[python projects repository](https://github.com/cedrc-pr/python-projects)
- [Log watcher](https://github.com/cedrc-pr/python-projects/tree/main/log-watcher), simulating nginx logs and monitors the status of services in real time.
- [Project cleaner](https://github.com/cedrc-pr/python-projects/tree/main/project-cleaner), it deletes generated folders.
- [Process watcher](https://github.com/cedrc-pr/python-projects/tree/main/process-watcher), monitors processes and displays their CPU and memory usage in real time.

## Home server

My own home server is basically a permanent DevOps sandbox: it runs Vaultwarden, Forgejo, and Seafile behind Traefik with automatic HTTPS, SSH hardening, and CrowdSec (used fail2ban before), and I maintain the whole thing myself (backups, certificate renewal, security, the full cycle).

# Development skills

**Languages**

Rust, TypeScript, JavaScript, Python, C#, C, SQL, HTML, CSS

**Frontend**

React, TanStack (Query, Router, Form), Tailwind CSS, Vite, Axios, Nuqs, Zod, date-fns

**Backend**
- Node.js:
  Fastify, Postgres, Resend, OpenRouter, Zod, date-fns, Dotenv, Jose
- Rust:
  Tokio, Poem, Redis, WebSocket, Serde, Lettre, Tracing, SQLx, Clap, Thiserror, Strum, Chrono, Inquire, Dotenvy
  
**Python**

psutil, rich, questionary

**Security & Authentication**

Argon2, JOSE/JWT, LDAP, CORS

**Tooling**

Git, Bun, npm, pnpm, yarn, Biome, ESLint

**Concepts**

REST API, HTTP, WebSockets, API design, database transactions, caching (Redis), OOP (Object Oriented Programming), Regex, async programming, error handling, testing, authentication/authorization, hashing (OWASP)

**Design & Collaboration**

Figma, UI/UX, Accessibility, MCD, use case diagram

> **Where do I create MCDs and use case diagrams?**
> 
> I was surprised to find that there aren’t really any completely free tools for these diagrams, but fortunately I’ve found some ‘code-based’ alternatives that I like: [Mocodo](https://www.mocodo.net/) for MCDs and [plantUML](https://www.plantuml.com) for use case diagrams.

## Development projects

### Full-stack 

- **School administration app** — manages information for ~200 students; **currently in production** and used daily by staff.
- **AI-assisted exercise assessment** — a teacher creates an exercise, an **LLM** generates questions from it, a student answers them, and a report is generated to estimate the student's level and readiness for the exercise. Built as a clean, working prototype (POC) to validate the concept ahead of a larger initiative exploring **how AI can be integrated meaningfully into teaching at my school**.
- [Copit](https://copit.cedric-prin.dev) ([repo](https://github.com/cedrc-pr/copit)) - a web app where you can create a chat room where only those with the password can join, perfect for sharing snippets of code or long links with colleagues or between devices.
- **Venueflow** ([repo](https://github.com/cedrc-pr/venueflow)) — an event and activity manager handling queues, delays, and live display screens.
- **Real-time bus schedule app** — consumes a public transit API to show live arrival times.

### Rust

- **LDAP management CLI**: simplifies school authentication management with built-in **email** sending.
- [Copit backend](https://github.com/cedrc-pr/copit/tree/main/be/): an API where I learned about WebSockets and Redis.
- [An experimental REST API](https://github.com/cedrc-pr/rust-projects/tree/main/rust-api), built mainly to discover how to write APIs in Rust.
- [Hoarder dragon](https://github.com/cedrc-pr/rust-projects/tree/main/projects-cleaner-cli): a CLI tool that scans project folders and cleans up temporary files.
- [Runner](https://github.com/cedrc-pr/rust-projects/tree/main/raycasting-engine): a raycasting engine that turns a text file into a pseudo-3D maze.

### C# & C

[Dungeon adventure](https://github.com/cedrc-pr/dungeon-adventure): a C# game in the terminal where I learnt about OOP.

C projects:
- [Clavardage](https://github.com/cedrc-pr/c-projects/tree/main/2024_chat): A multi-client chat server with a built-in command interpreter.
- [Vector](https://github.com/cedrc-pr/c-projects/tree/main/2024_vector): A generic vector implementation capable of storing any data type.
- [`stu_dprintf`](https://github.com/cedrc-pr/c-projects/tree/main/2024_printf): a partial reimplementation of `dprintf` (`stu` standing for student).
- A recode of [`ls`](https://github.com/cedrc-pr/c-projects/tree/main/2024_ls), [`tr`](https://github.com/cedrc-pr/c-projects/tree/main/2024_tr) and [`cat`](https://github.com/cedrc-pr/c-projects/tree/main/2024_cat).

# About me

## Professionally

I'm in my third year of a full-stack & DevOps bachelor's program, finishing summer 2027, and I'm aiming to continue with a DevOps master's afterward — currently looking closely at programs in Île-de-France.

I'm also on a work-study contract as a full-stack/DevOps developer and teaching assistant at my own school — I was hired directly by the head of the programming and cybersecurity bachelor's programs.

## Soft skills

**Teaching.** I record course videos, write course material, and teach. I've always liked passing on what I know — I listen, use storytelling to keep people engaged, and simplify concepts when needed.

**Curiosity & Depth**. I genuinely like understanding things. When something doesn’t make sense to me, I’ll ask questions, dig deeper, and keep exploring until I have a solid grasp of it.

**Autonomy.** My school runs almost entirely on project-based learning — projects can run up to a month, solo or in groups, starting from year one. At one point my mentor asked me to build a web app with nothing but a need and two keywords: "React + Node.js." I had to figure out what that meant and how to use it on my own. It’s a bit like being a photographer and being asked to make a film.

**Patience & persistence.** I've been that way since I was a kid, spending weeks optimizing a Redstone system in Minecraft to make it cheaper, faster, and smaller.

**Fast learner.** I think in a fairly logical, systems-oriented way — years of building Redstone systems in Minecraft turned out to be great training for programming logic.

## Where I still have room to grow

**Introverted but hands-on when it matters** — I'm the "indoor cat" type; my social battery needs quiet time to recharge, and I won't necessarily be the loudest person by the coffee machine. But as soon as it's about discussing, contributing or exchange ideas, I'm all in.

**Focus & context-switching** — when I'm deep in code, I'm fully in the zone. If I get interrupted for something completely unrelated, my brain needs a few seconds to "reboot." It's the price of concentration.

**Aesthetics UI** — I’m comfortable building clean, functional, and accessible interfaces, but I’m less confident when it comes to the creative and artistic side of design. 

**Balancing strictness with speed (Over-engineering)** — Because I love strict typing and robust architectures, I sometimes catch myself spending too much time perfecting the underlying structure of a simple project instead of just shipping it. I'm learning to better identify when a "quick and dirty" POC is enough, versus when full architectural rigor is actually required.

## My engineering philosophy

### Strict ecosystem

I love this rule: Never trust the user. It’s important to me to have reliable code and to minimize uncertainty as much as possible.

I use TypeScript with strict Zod schemas for my API, and I even use a DOM sanitizer (even though React protects against XSS). That’s also why I use Tanstack Form — it works very well with Zod.

I also really like Rust for this reason: strict types from the start, but very useful tools to make working with them easier.

### Me and AI

I only work with an LLM in my browser. That might sound shocking these days, but I need to understand. Getting stuck on a problem, running tests, encountering bugs: that’s all part of the learning process. So I ask the AI lots of questions to really understand, but I don’t let it write the code for me.

Once I’m really good at this and comfortable with the concepts, then I’ll be able to give it precise instructions to produce high-quality code.

## My setup

- Arch Linux with GNOME (simple but clean)
- Obsidian for notes (long live Markdown and Vim bindings)
- Zed as my IDE (minimalist, fast and lightweight)
- Zen as my browser (Firefox-based, privacy-respecting)
- LibreOffice

## Outside of code

I stay active: calisthenics, running, climbing, parkour and scuba diving.

I'm also a gamer — I like challenging FPS/TPS games (DayZ, Arc Raiders, Hunt Showdown, Arena Breakout Infinite, Gray Zone Warfare), but I also enjoy management sims like Cities Skylines and Planet Coaster.

I listen to a lot of music, from soul and jazz to house and rap.

---

**Let's talk:** [LinkedIn](https://www.linkedin.com/in/cedric-prin) - cedric.prin@free.fr

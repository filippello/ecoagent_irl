# EcoAgent IRL · Hackathon

> Telegram Agent + Crowdfunding platform that coordinates micro‑tasks for cleaning public spaces. Payments and smart contracts on **CELO** using **GoodDollar (G$)**.

## Disclaimer
All the code was created specifically for this hackathon, **except** for the **irl-agents** repository, which is an idea we had been iterating on before and adapted for this event.

## Repositories and Components
- **Telegram Agent** · orchestration and conversational UX: `ecoAgent`  
  https://github.com/filippello/ecoAgent
- **Crowdfunding Web + Contracts** · CELO + GoodDollar  
  https://github.com/Sixela33/celo#
- **IRL Tool** · planning, task assignment, and verification (previous iteration, completed and integrated with GoodDollar, CELO, and the crowdfunding platform)  
  https://gitlab.com/irl-agents

---

## What is EcoAgent IRL
EcoAgent IRL allows anyone to report simple civic cleaning issues, raise funds within minutes, and hire someone nearby to solve them. The Telegram agent guides the process, orchestrates the tasks, verifies with photos, and releases payments on‑chain.

But this is just the beginning — the idea is to expand beyond cleaning tasks. Cleaning serves as an example of its potential, but in the future, it could support donations for building basic services, repairs, or specific community aid projects.

**Use case for this version:** cleaning of public spaces (sidewalks, parks, signs, bins, small waste areas).

## How It Works (Flow)
1. A community member contacts our Telegram agent via @ecoagentetestbot and describes the issue.

<img width="879" height="245" alt="image" src="https://github.com/user-attachments/assets/430e4e05-7c33-4bde-98c5-7d3be6d0a624" />

2. The bot requests a description, photos, and the location of the problem.  
3. A basic cost estimate is generated, and a crowdfunding campaign is created on the web: https://crowdfund.irl-agents.xyz/
4. Once the goal is reached, the system splits the job into micro‑tasks and assigns them to nearby workers.

<img width="1038" height="403" alt="image" src="https://github.com/user-attachments/assets/07035395-059e-4364-9215-6af6ce171f05" />

5. Workers connect through the Telegram miniapp that opens our IRL app via @irl_agents_bot. When a task is assigned, they can complete it, upload evidence, and the system verifies it.
6. Payments are released on‑chain through CELO using GoodDollar.

<img width="652" height="279" alt="image" src="https://github.com/user-attachments/assets/50098c1a-a4f3-4cd8-b596-285c7fec549c" />

## Architecture (Overview)
- **Telegram Bot**: FastAPI/Node or Python (depending on repo), connected to database and queues.
- **Crowdfunding dApp**: Web front + CELO contracts. Handles G$ contributions and milestone releases.
- **IRL Engine**: Geo‑based task assignment, evidence validation, task state management.
- **Payments**: CELO + GoodDollar contracts. Non‑custodial design.

> Note: Detailed technical information for each module is in its respective repository.

## Verification System
Some tasks require additional verification beyond automatic validation. In these cases, the task generates a *verifier role* — a person responsible for checking that completed work meets requirements.

<img width="675" height="299" alt="image" src="https://github.com/user-attachments/assets/27e60a7b-d59d-4464-9161-bd5027de259b" />

This also enables a **reputation system** for users of our app.

<img width="638" height="384" alt="image" src="https://github.com/user-attachments/assets/f6d9ab72-1b22-48f0-a8f9-5a0bf0ec6ef8" />

## Reputation and Work History
Much of the informal labor in Latin America goes unrecorded. With this tool, we can start documenting completed tasks, offering training, and helping workers improve their skills and opportunities by performing useful, verified jobs.


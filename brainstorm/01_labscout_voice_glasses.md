# LabScout Voice + Glasses

> Links to: Main hackathon pick; extends existing LabScout protocol + glasses schema

## Problem
Labs and robotics companies in Japan want international technicians, but SOPs and safety briefings are Japanese-only, so onboarding is slow and risky.

## Who it's for
New international lab/robotics hires; lab managers; HR onboarding teams.

## Solution
A bilingual voice guide (Sato-san) reads each protocol step in Japanese then English, while Even Realities glasses show the short step text. The hire confirms by voice ("完了"), and every step is logged.

## ElevenLabs tools
ElevenAgents (live guide), Voice Design (Sato-san), Text to Speech (pre-made alerts), Sound Effects (step chime).

## Even Realities glasses role
Glasses show the step title and a 1-line instruction; voice plays from phone or earbuds (display-first, no robot control).

Note: Even Realities glasses are display-first (text on the lenses, mic input). Audio plays from the phone or earbuds.

## Chart 1 — Technical workflow pipeline
```mermaid
flowchart LR
    A[Protocol YAML<br/>rack inspection] --> B[FastAPI backend<br/>protocol engine]
    B --> C[Step text JA + EN]
    C --> D[ElevenLabs TTS / Agent<br/>Sato-san voice]
    C --> E[Even Hub app<br/>glasses text card]
    D --> F[Phone / earbuds audio]
    G[Hire says 完了 / stop] --> H[Speech to Text]
    H --> I{Safety gate}
    I -- confirm --> B
    I -- stop --> J[Pause all steps]
    B --> K[(Audit log CSV)]
```

## Chart 2 — Business flowchart
```mermaid
flowchart LR
    A[Company hires<br/>international technician] --> B[Buys LabScout Voice<br/>per-seat subscription]
    B --> C[Uploads its SOPs]
    C --> D[Hire trains hands-free<br/>in 2 languages]
    D --> E[Faster ramp-up<br/>fewer safety errors]
    E --> F[Manager dashboard<br/>+ audit logs]
    F --> G[Renewal + more SOPs]
    G --> B
```

## 60-minute hackathon scope
Agent + Sato-san voice running the 6-step protocol live; screenshot of glasses card mockup from the dashboard.

## Main risk and mitigation
Voice misrecognising Japanese in a noisy room -> use headset mic, allow tap confirm as backup.

## Next step
- [ ] Discuss, score (impact / effort), decide keep or drop

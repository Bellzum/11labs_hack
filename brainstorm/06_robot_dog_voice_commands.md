# Robot Dog Voice Safety Layer

> Links to: Extends Freenove dashboard + FastAPI backend

## Problem
Beginners controlling robots panic and can't reach the e-stop button; lab robots need hands-free safe stop.

## Who it's for
Robotics learners, lab automation teams, educators.

## Solution
A voice layer on top of the existing FastAPI safety gate: saying 'stop' or '止まれ' triggers the emergency stop endpoint instantly; the robot confirms status aloud and on glasses. Movement by voice stays disabled (display + stop only).

## ElevenLabs tools
ElevenAgents or Speech to Text (stop word), Text to Speech (status replies), Voice Design (robot voice).

## Even Realities glasses role
Glasses show e-stop state, battery, obstacle warning; they never send movement commands.

Note: Even Realities glasses are display-first (text on the lenses, mic input). Audio plays from the phone or earbuds.

## Chart 1 — Technical workflow pipeline
```mermaid
flowchart LR
    A[User says stop / 止まれ] --> B[ElevenLabs STT / Agent]
    B --> C[Intent: stop only]
    C --> D[POST /api/robot/emergency-stop]
    D --> E[Safety gate]
    E --> F[Freenove adapter<br/>mock mode]
    E --> G[(Experiment log CSV)]
    E --> H[TTS: Emergency stop active]
    E --> I[Even glasses status card]
```

## Chart 2 — Business flowchart
```mermaid
flowchart LR
    A[Robotics classroom / lab] --> B[Adds voice safety kit]
    B --> C[Faster stop reaction<br/>safer learning]
    C --> D[Logged incidents<br/>for teachers]
    D --> E[Curriculum licence]
    E --> A
```

## 60-minute hackathon scope
Mock mode only: agent recognises stop words and calls a mock e-stop; dashboard shows the state change.

## Main risk and mitigation
Voice latency too slow for real safety -> physical e-stop stays primary; voice is an extra layer.

## Next step
- [ ] Discuss, score (impact / effort), decide keep or drop

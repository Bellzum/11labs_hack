# 11labs_hack

**LabScout Voice** — a bilingual (Japanese / English) voice guide that onboards new international lab and robotics technicians in Japan, step by step.

Built for the **ElevenLabs Meetup Tokyo: Build with ElevenCreative** (Oct 9, 2026, Mercari, Roppongi Hills).
Challenge theme: *Solving Career & Hiring Challenges in Japan*.

## The problem

Labs and robotics companies in Japan want international talent, but day-one training, SOPs and safety briefings are often Japanese-only. New hires feel lost in their first weeks, and managers hesitate to hire.

## The idea

"Sato-san", a calm senior lab technician voice agent, talks a new hire through a lab protocol:

1. Says each step in polite Japanese, then simple English.
2. Waits for the person to say "done" / "完了" before moving on.
3. Answers questions in the language they were asked in.
4. Pauses everything when the person says "stop" / "止めて".
5. Ends with a bilingual summary and one useful lab Japanese phrase.

## ElevenLabs tools used

| Tool | Use |
| --- | --- |
| ElevenAgents | The live, talk-back voice guide |
| Voice Design | The "Sato-san" voice and a BioScout Dog alert voice |
| Text to Speech | Pre-recorded bilingual step and alert messages |
| Sound Effects / Music | Step-complete chime, emergency-stop tone, background track |

No code is needed for the hackathon build — everything is configured in the ElevenLabs web app.

## How it connects to LabScout

This is the voice layer of my long-term LabScout / BioScout Dog robotics platform (Freenove robot dog + FastAPI backend + future Even Realities smart glasses).

- Protocol steps come from `protocols/examples/glasses_guided_sample_rack_inspection.yaml` in the LabScout repo.
- Each smart-glasses message type (instruction, confirmation request, warning, short result) gets a voice version.
- Safety rules carry over: voice "stop" pauses the workflow, and the agent never tells anyone to move a robot.

## Repository layout

```text
11labs_hack/
  README.md
  prompts/
    labscout_voice_agent.md   # system prompt + first message for the ElevenAgents agent
  docs/
    prep_plan.md              # 10-day practice checklist and night-of checklist
    demo_script.md            # 60-minute build plan + 2-minute pitch
  assets/
    voices/                   # notes on the voices created in Voice Design
    audio/                    # exported TTS, chimes, music (mp3)
  recordings/                 # backup demo recordings
```

## Status

- [ ] ElevenLabs account created
- [ ] Sato-san voice designed
- [ ] Agent built and tested
- [ ] Audio assets exported
- [ ] Full 60-minute rehearsal done

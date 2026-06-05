<div align="center">

# FocusBot

**A focus companion that helps you work in deep, healthy, distraction-free sessions.**

![Flutter](https://img.shields.io/badge/Mobile-Flutter-02569B?style=flat-square&logo=flutter&logoColor=white)
![Dart](https://img.shields.io/badge/Language-Dart-0175C2?style=flat-square&logo=dart&logoColor=white)
![Flask](https://img.shields.io/badge/Backend-Flask-000000?style=flat-square&logo=flask&logoColor=white)
![Firebase](https://img.shields.io/badge/Backend-Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=black)
![Raspberry Pi](https://img.shields.io/badge/Hardware-Raspberry%20Pi-A22846?style=flat-square&logo=raspberrypi&logoColor=white)

</div>

---

## Overview

FocusBot is a cross-platform productivity app that combines task management and the Pomodoro technique with **physical focus monitoring**. A Raspberry Pi setup observes posture during work sessions, so FocusBot nudges you not just to stay on task but to stay healthy while doing it — bridging a software productivity tool with real-world hardware sensing.


---

## Features

- **Task Management** — create, organise and track tasks for each work session.
- **Pomodoro Timer** — structured focus/break cycles to sustain concentration.
- **Focus Tracking** — logs completed sessions and focus time over the day.
- **Posture Monitoring** — a Raspberry Pi camera/sensor flags poor posture during sessions.

---

## Architecture

```
┌──────────────────────┐        ┌──────────────────────┐
│   Flutter Mobile App │        │   Raspberry Pi        │
│  Tasks · Pomodoro ·  │        │  Camera / posture     │
│  Focus dashboard     │        │  sensing              │
└──────────┬───────────┘        └──────────┬────────────┘
           │  REST                          │  posture events
           ▼                                ▼
        ┌────────────────────────────────────────┐
        │        Flask Backend (REST API)         │
        │   Session logic · posture processing    │
        └──────────────────┬─────────────────────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │     Firebase     │
                  │  Auth · storage  │
                  └──────────────────┘
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Mobile app | Flutter (Dart) |
| Backend | Flask (Python) |
| Hardware | Raspberry Pi (posture monitoring) |
| Cloud / data | Firebase |

---

## Project Structure

```
focusbot/
├── app/              # Flutter mobile application
├── backend/          # Flask backend + Raspberry Pi integration
├── .gitattributes    # Keeps generated platform code out of language stats
└── README.md
```

---

## Getting Started

### Mobile app

```bash
cd app
flutter pub get
flutter run
```

### Backend

```bash
cd backend
pip install -r requirements.txt
python app.py
```

Add a `.env` (or `firebase_config`) with your Firebase credentials and backend URL. **Never commit credentials** — keep them in `.gitignore`.

### Raspberry Pi (posture monitoring)

Connect the camera/sensor, then run the posture service on the Pi and point it at the backend URL. See `backend/` for the integration script.

---

## Roadmap

- On-device posture detection to reduce dependence on the Pi.
- Weekly focus and posture analytics.
- Smart break suggestions based on session history.

---

## About

Built as an academic project exploring how a software productivity tool can integrate with real-world hardware sensing for healthier, more focused work.

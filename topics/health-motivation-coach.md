# 🌱 Health Motivation Coach

## What?
An app that connects to Apple Health and only motivates you. Reads your weight, height, and exercise data. When it sees you're losing weight, it cheers you on. Minimal inputs — just reads from HealthKit.

## Why does it interest me?
- Most fitness apps are complex and require tons of input
- People need motivation, not another tracker
- Apple Health already has all the data — why enter it twice?
- Simple concept: read data → send encouragement

## Notes
- **Core insight:** The app does ONE thing — motivate. No logging, no meal plans, no workout suggestions. Just "hey, you're doing great!"
- **Key interaction:** Prompts you to weigh yourself regularly, then infers how you're doing from ALL your Health data
- **HealthKit data to infer from:**
  - Weight (historical to see trend) — THE key metric
  - Height (for context/BMI)
  - Workouts/exercise minutes
  - Steps
  - Active calories burned
  - Sleep (maybe — affects weight loss)
  - Resting heart rate (fitness indicator)
- **The magic:** Combines all signals to give you a holistic "how am I doing?" instead of just weight
  - Lost weight + more workouts = "You're crushing it! 🔥"
  - Weight stable + lots of exercise = "Building muscle? Scale doesn't tell the whole story 💪"
  - Weight up + no exercise + bad sleep = "Rough week? Let's get back on track"
- **Motivation triggers:**
  - Weight going down → celebrate
  - Consistent workouts → acknowledge streak
  - Hit a plateau but exercising → encourage (muscle vs fat)
  - Weight going up → gentle nudge with context
- **Tone:** Supportive friend, not drill sergeant
- **Possible features:**
  - "Time to weigh in!" reminder (configurable frequency)
  - Daily/weekly motivation based on all data
  - Progress visualization (simple, not overwhelming)
  - Milestones celebration (every kg lost, etc.)
- **Monetization?** Premium for advanced insights? Or keep it free and simple?

## Questions
- How often should it prompt to weigh? Daily? Weekly?
- How to handle weight fluctuations (water weight, etc.) without false positives?
- What's the right notification frequency for motivation?
- How to be motivating without being annoying?

---
*Created: 2026-02-01*

# Physical Freedom Tracker — V0.1 Project Specification

## Purpose

Build a simple personal training and symptom-tracking app that supports self-reliance, progressive rebuilding of strength and conditioning, and clearer decisions around exercise tolerance.

The app is not an injury-only tracker. The current right-sided glute/back/possible nerve irritation is one layer inside a broader physical-freedom system whose long-term goals are to maintain and build strength, muscularity, conditioning, movement confidence and participation in life.

## V0.1 priorities

V0.1 should answer three questions quickly:

1. What do I do today?
2. What happened when I trained?
3. Is my capacity improving, stable or worsening over time?

The interface should be mobile-friendly, fast to log during training, and require minimal typing.

## Core screens

### 1. Today

Show:

- Date
- Morning symptom check
- Daily 15-minute capacity routine
- Today’s programmed workout
- Quick links to History and Programme

Morning symptom fields:

- Right glute first-load pain: 0–10
- Right glute general tightness/pain: 0–10
- Calf: none / awareness / pain
- Back: none / awareness / pain
- Time for morning symptoms to settle: minutes
- Optional note

### 2. Daily Capacity Routine

Initial V0.1 routine:

1. Easy movement / walking — 2–3 min
2. Petersen or 6-inch step-down — 2 × 6–8 each side
3. Hip abduction — 2 × 10–15
4. Dead bug — 2 × 6–8 each side
5. Suitcase carry — 2 × 30–45 sec each side
6. Controlled calf raises — 2 × 10–15

Each item should have a simple completion toggle. Routine items should be editable later.

Do not frame this as mandatory rehabilitation. It is a daily capacity/control practice.

## Exercise response model

Every programmed strength exercise should allow a very fast response log.

### During

Symptom location:

- None
- Local glute
- Back
- Calf
- Other

Intensity: 0–10, optional unless symptoms are present.

### 5–10 minutes after

- Better
- Baseline / same
- Worse

### Next morning

- Better than baseline
- Baseline / same
- Worse than baseline
- Distal/calf symptoms present: yes/no

This is deliberately more important than a generic pain score because the current clinical boundary is distal calf symptoms and persistent worsening.

## Training decision rules shown in app

These rules should appear unobtrusively on relevant screens:

- Local glute/back awareness does not automatically mean stop.
- Calf symptoms are a stronger warning signal. Stop or regress the provoking exercise if calf symptoms appear.
- If an exercise causes worsening that persists afterwards, regress or remove the current dose.
- If symptoms occur locally but settle rapidly back to baseline, record them rather than automatically removing the exercise.
- Do not chase posterior-chain tightness with passive stretching if stretching is provocative.

This app supports decision-making but does not diagnose the cause of symptoms.

## Workout 001 — Home Lower Body Test / Build Session

This should be pre-programmed as the first workout.

### Warm-up

Easy walking / bike / general movement — 4–5 minutes.

### 1. Petersen or 6-inch step-down

- 2 × 8 each side
- Goal: right pelvic control / unilateral control
- Track reps and optional note

### 2. Elevated Barbell Deadlift

- Ramp-up sets as needed
- 3 working sets
- Initial target: RPE 6–7, roughly 2–3 reps in reserve
- Start bar around mid-shin or another elevated height that allows meaningful loading without increasing distal symptoms

Experiment question:

> Does raising the deadlift starting position allow meaningful posterior-chain loading with less right-glute tightening and no calf response?

Log:

- height / setup
- load
- reps
- RPE or RIR
- during symptoms
- 5–10 min response
- next-morning response

### 3. Nordic Hamstring Curl

- 3 × 4–6
- First set can be controlled eccentric reps with hands catching the descent
- Goal: high hamstring stimulus without relying on the long-length hinge position currently associated with posterior-chain tightness

Experiment question:

> Can Nordics provide hard hamstring loading without provoking the familiar glute/calf pattern?

### 4. Split Squat

- 3 × 8–10 each side
- Moderate load
- Aim around RPE 7 initially
- Goal: unilateral strength and hypertrophy while observing right-side tolerance

### 5. Hip Thrust / Hip Thruster Lite

- 3 × 8–12
- Progressive but controlled loading
- Local glute awareness can be logged without automatically treating it as failure

### 6. Standing Cable or Band Hip Abduction

- 2 × 12–15 each side
- Start light
- Goal: rebuild lateral glute capacity without recreating the previous excessive-dose response

### 7. Suitcase Carry

- 2 × 30–45 sec each side
- Meaningful load with controlled trunk position
- Goal: anti-lateral-flexion trunk capacity and integrated hip control

### 8. Tib Raises + Calf Raises

- 2 × 12–15 each
- Controlled tempo
- Goal: lower-leg capacity without repeatedly strength-testing the nerve pathway

## Workout logging requirements

For every exercise:

- exercise name
- variation / setup
- load
- reps
- sets
- optional RPE/RIR
- symptom location during exercise
- symptom intensity if relevant
- immediate/5–10 min response
- optional notes

For unilateral exercises, allow side-specific notes when useful.

## History

V0.1 history should show:

- previous workouts by date
- morning symptom entries by date
- exercise-specific exposure history

Example future insight:

> Elevated deadlift: 5 exposures, 0 calf responses, 1 local-glute flare, 4 next-morning baseline/better outcomes.

V0.1 does not need sophisticated analytics yet, but the data model should support this later.

## Programme structure — future-ready

The app should be able to grow into a four-day training architecture:

- Lower A — knee/quad + capacity emphasis
- Upper A
- Lower B — hinge/posterior-chain emphasis
- Upper B

Additional modules later:

- Conditioning
- Running / Norwegian intervals
- Circuits
- Jive / general activity
- Sled progression
- Recovery/readiness
- Sleep
- Compex sessions
- Measurements / physique
- MRI / clinical notes
- Experiments
- Trend visualisations

## Compex — planned V0.2 feature

Potential use:

- supplementary right-glute stimulus 2–3 times weekly
- not a replacement for voluntary resistance training
- exact programme/electrode setup to be selected only after reviewing the specific Compex SP 8.0 options

Track:

- programme
- muscle/side
- duration
- intensity
- response

## Design principles

- Mobile first
- Very little typing during workouts
- Large tap targets
- Clear distinction between local symptoms and distal/calf symptoms
- No alarmist injury language
- Capacity and progression should be visually prominent, not just pain scores
- Preserve strength, physique and conditioning goals
- Self-reliance over dependence
- Keep clinical hypotheses separate from observations

## Technical direction

Suggested initial stack:

- React
- TypeScript
- Vite
- Local-first persistence initially (localStorage or IndexedDB)
- GitHub Pages deployment when the first working version is ready

Avoid a backend in V0.1 unless there is a clear reason to add one.

## Initial data entities

### DailyCheckIn

- id
- date
- firstLoadGlutePain
- gluteGeneral
- calfStatus
- backStatus
- settlingMinutes
- note

### Exercise

- id
- name
- category
- defaultPrescription

### Workout

- id
- date
- title
- exerciseEntries[]
- overallNote

### ExerciseEntry

- exerciseId
- setup
- sets[]
- duringSymptomLocation
- duringSymptomIntensity
- shortTermResponse
- nextMorningResponse
- nextMorningCalfSymptoms
- note

### SetEntry

- load
- reps
- rpe
- rir

### DailyRoutineCompletion

- date
- items[]

## V0.1 definition of done

A usable first version should allow the user to:

1. Open Today.
2. Record morning symptoms in under 30 seconds.
3. Tick off the daily routine.
4. Start Workout 001.
5. Log sets/load/reps for each exercise.
6. Record symptom location and immediate response with a few taps.
7. Complete a next-morning follow-up.
8. Review previous entries in History.
9. Have data persist after closing/reopening the app.

That is enough for V0.1. Do not add complexity until this workflow is genuinely useful in real training.

# Iron Log

A black-and-white gym tracker for machine training. Log sets, reps and weights,
track personal bests, see which days you trained what, and get workout
suggestions based on the machines your gym actually has.

It is a static site with no build step, so it runs on GitHub Pages and works
offline in the gym once it has been opened.

## What's in here

| File | What it does |
|---|---|
| `index.html` | The whole app |
| `sw.js` | Saves the app on your phone so it opens without signal |
| `manifest.webmanifest`, `icon-*.png`, `apple-touch-icon.png` | Lets you add it to your home screen like an app |
| `jsQR.js` | QR code reader used on iPhone ([jsQR](https://github.com/cozmo/jsQR), Apache 2.0, see `jsQR-LICENSE.txt`) |
| `three.module.min.js` | 3D engine for the body model ([three.js](https://threejs.org) r170, MIT licence in the file header) |

## Put it on GitHub Pages

1. Create a repository (for example `gym`) and upload all the files to the root of the `main` branch.
2. In the repository, open **Settings → Pages**, set **Source** to *Deploy from a branch*, pick `main` and `/ (root)`, and save.
3. After a minute it is live at `https://<your-username>.github.io/gym/`.
4. Open that address on your phone and add it to the home screen
   (Safari: Share → Add to Home Screen. Chrome: menu → Add to Home screen).

It also works from a subfolder of an existing Pages repository, because every path is relative.

## Sync your log through GitHub (optional)

Your log is always saved on the device first. To back it up and see the same
data on your phone and laptop, turn on sync in **Settings → Sync with GitHub**:

1. On GitHub, go to **Settings → Developer settings → Personal access tokens → Fine-grained tokens** and generate a token.
2. Repository access: *Only select repositories* → this repository.
3. Permissions: **Contents → Read and write**.
4. Paste the token into the app on each device.

The log is written to `gym-log.json` on a separate `gym-data` branch, so saving
a set never triggers a Pages rebuild. The token stays in the browser and is
never committed. If the repository is public, the log file is public too.

## QR codes and NFC tags

- **QR codes** work on any phone. Tap *Scan machine*, point at the code on the
  machine, and pick which machine it is the first time. After that, scanning it
  opens that machine's log straight away. Each machine needs its own distinct code;
  if your gym uses the same code everywhere, choose the machine from the list instead.
- **NFC tags** can only be read by a web app in Chrome on Android. iPhones do not let
  websites read NFC, so use the QR codes there.
- You can also make your own stickers: a link like
  `https://<your-username>.github.io/gym/?m=leg-press` opens that machine directly.

## Using it

- **Today**: this week at a glance and today's session. Under *Train today*, a 3D body
  shows which muscles are in today's plan. Drag it to turn it, tap muscles to add or
  remove them, or pick a preset (Push, Pull, Legs and so on). The machine list below
  updates to match, with target weights. Muscles trained in the last two days get their own shade.
- **Logging**: scroll the weight stack or use the − / + buttons, set the reps, tap
  *Log set*. The rest timer starts on its own. Tap a logged set to edit or delete it.
  Note seat and pad settings once per machine.
- **Targets**: when two sets hit the top of the rep range (12 reps for presses and
  rows, 15 for single-joint machines), the next target adds one weight step.
- **Personal bests**: a new heaviest set, rep record or estimated 1-rep max triggers a
  full-screen celebration. Tap it to carry on.
- **Body**: weigh-ins on a sliding scale with a 7-day average trend, goal weight and BMI;
  tape measurements (chest, waist, hips, arms, thighs and more) with history charts; and
  fitness, with cardio sessions on machines, weekly minutes against the WHO 150-minute
  guideline, resting heart rate and VO2 max.
- **Progress**: training calendar, volume per week, muscle balance and personal bests.
- **Settings**: rest length, black or white theme, your gym's machines, backups, sample data.

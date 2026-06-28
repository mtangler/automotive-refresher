# 🍔 CTS Burger

> Android Automotive certification explained like a burger.

---

## What even is CTS?

CTS = **Compatibility Test Suite**

You built car software.

Google says:

> Cool. Now prove you didn't break Android.

Pass → certification possible  
Fail → back to kitchen 🍔

---

## 🍟 Burger Ingredients

### 🥩 CTS — Compatibility Test Suite
- Android framework
- APIs
- permissions
- services
- UI behavior

Meaning:

> Does Android behave like Android?

### 🥬 VTS — Vendor Test Suite
- HAL
- vendor layer
- kernel interactions
- AIDL / HIDL

Meaning:

> Does hardware talk correctly?

### 🧀 GTS — Google Test Suite
- Google requirements
- Play services
- certification checks

### 🍅 XTS — eXtended Test Suite
- automotive specifics
- custom extensions

---

## Build → Test

### Step 1 — Build available

```text
car_build_version.img
```

### Step 2 — Start CTS

```bash
cts-tradefed
run cts
run cts-dev
```

Tradefed:
- executes tests
- collects logs
- generates reports

### Step 3 — Wait

Complete run:

**8–24+ hours**

---

## Scale Of The Monster

Reality:

- thousands and thousands of modules
- hundreds of thousands → millions (yes, millions) of tests
- Android revisions
- CTS revisions

Usually:

- smoke plan
- regression plan
- certification plan

---

## 🔁 Weekly Development Loop

```text
Developer codes
↓
Build arrives
↓
Run CTS
↓
Failures
↓
Analyze
↓
Fix
↓
New build
↓
Run again
```

This repeats weekly during development.

Yesterday's green dashboard can become today's disaster.

---

## 📊 Reports

Outputs:

- XML
- HTML
- logs
- metrics

Often visualized in:

- Grafana
- Jenkins
- custom dashboards

---

## 🔎 Failure Investigation

Questions:

- Setup issue?
- Flaky?
- Actual bug?
- Vendor issue?
- CTS issue?

Then:

- root cause
- task creation
- reproduce
- verify
- rerun

---

## 🛠 Daily CTS Powers

- rigs
- vehicles
- emulator
- retries
- adb magic

```bash
adb shell
adb root
adb logcat
adb bugreport
```

---

## 🐧 Another Layer Of The Burger → Linux Powers

```bash
tmux
oh-my-zsh
grep
awk
sed
ssh
watch
vim
```

Eventually terminal becomes your garage workshop.

---

## 🍔 Final Burger

```text
Requirement
↓
Developer
↓
Build
↓
Flash
↓
CTS
↓
Dashboard
↓
Root Cause
↓
Fix
↓
Repeat
↓
Release
```

---

## Work Translation

People think:

> CTS = clicking Run

Reality:

- automation
- Linux
- debugging
- framework
- ADB
- infrastructure
- root cause analysis

Half tester.
Half developer.
Half detective.
(yes that is 150%)

> ### 📡 Quantum CTS Theory 🌀 
>
> After enough CTS runs one can say that some tests do not pass or fail. They simply exist in superposition until someone opens the report.

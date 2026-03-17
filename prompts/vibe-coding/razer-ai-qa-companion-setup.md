# Razer AI QA Companion — Developer Setup Guide

> **GDC 2026 (March 17):** Razer launched AI Pipeline Tools for game developers. The QA Companion-AI automates bug detection, test case generation, and gameplay issue spotting — reducing QA cycles by up to 60%.

## What You Get
Integrate Razer's AI QA agent into your game testing pipeline. It watches gameplay sessions, detects visual/logic bugs, auto-generates test cases, and creates structured bug reports with reproduction steps.

## Quick Start — CLI Setup

```bash
# 1. Install Razer Dev Tools CLI
npm install -g @razer/devtools-cli

# 2. Authenticate with your Razer Developer account
razer-dev auth login

# 3. Initialize QA Companion in your project
razer-dev qa init --engine unreal5  # or unity, godot, custom

# 4. Run your first AI-assisted QA session
razer-dev qa watch --session "playtest-001" \
  --capture-video \
  --detect-bugs \
  --generate-reports
```

## Configuration — `.razer-qa.yml`

```yaml
# .razer-qa.yml — Place in project root
project:
  name: "my-game"
  engine: "unreal5"  # unreal5 | unity | godot | custom
  genre: "fps"       # Helps AI understand expected behaviors

qa_companion:
  # Bug detection sensitivity
  visual_glitch_threshold: 0.7    # 0.0 (lenient) → 1.0 (strict)
  physics_anomaly_detection: true
  ui_overlap_detection: true
  performance_drop_alert: 30      # Alert if FPS drops below this

  # Test generation
  auto_generate_tests: true
  test_framework: "pytest"        # pytest | jest | googletest | custom
  coverage_target: 0.8            # 80% gameplay path coverage

  # Reporting
  report_format: "github_issue"   # github_issue | jira | markdown | json
  screenshot_on_bug: true
  video_clip_seconds: 10          # Capture N seconds before/after bug

  # Integrations
  ci_integration: "github_actions"
  notify_slack: "#qa-channel"
```

## Bug Detection Categories

| Category | What It Catches | Example |
|----------|----------------|---------|
| Visual Glitches | Texture pop-in, z-fighting, clipping | Character arm through wall |
| Physics Anomalies | Objects flying, stuck, wrong gravity | NPC floating after death |
| UI Issues | Overlapping elements, unreadable text | Button behind HUD element |
| Performance | FPS drops, memory spikes, stuttering | Loading screen freeze |
| Logic Bugs | Unreachable areas, broken quests | Door locked after collecting key |
| Audio Sync | Dialogue timing, missing SFX | Explosion sound 2s late |

## GitHub Actions — Automated QA on Every Build

```yaml
# .github/workflows/qa-companion.yml
name: Razer AI QA
on:
  push:
    branches: [main, develop]

jobs:
  ai-qa:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: razer-dev/qa-companion-action@v1
        with:
          engine: unreal5
          session-duration: "5m"
          bug-threshold: "medium"
          report-to: "github-issues"
          fail-on-critical: true
```

## Supported Engines
- **Unreal Engine 5.4+** — Full plugin integration
- **Unity 6+** — Package Manager install
- **Godot 4.3+** — GDExtension
- **Custom engines** — REST API + video feed

---

> 💡 **Want the full AI QA Production Pipeline?** Multi-engine orchestration, regression tracking dashboard, team QA workflow configs, Jira/Linear integration, and CI/CD quality gates → [AI Dev Toolkit PRO](https://ai-dev-toolkit-five.vercel.app) — $9 one-time

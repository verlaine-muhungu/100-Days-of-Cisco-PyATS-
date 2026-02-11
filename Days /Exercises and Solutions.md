# 100 Days of pyATS — Exercises and Solutions

This workbook gives you **one practical exercise per day** with a concise solution.

> [!NOTE]
> Solutions are intentionally short so learners can still implement them hands-on.

## Days 1–11: pyATS Discovery

| Day | Topic | Exercise | Solution (Expected Outcome) |
|---|---|---|---|
| 1 | NetDevOps foundations | Write a short paragraph explaining where pyATS fits in NetDevOps. | pyATS provides structured testing, repeatability, and post-change validation in automation pipelines. |
| 2 | Install pyATS | Install pyATS in a virtual environment and confirm version. | `python3 -m venv venv && source venv/bin/activate && pip install pyats[full] && pyats version`. |
| 3 | Testbed YAML basics | Build a `testbed.yaml` with one IOS XE device. | File loads successfully with `pyats validate testbed testbed.yaml`. |
| 4 | Multi-device testbed | Add two more devices and credentials inheritance. | Parent credentials work for all devices without repetition. |
| 5 | Connection aliases | Define `cli` and `netconf` connections in testbed. | `device.connect(alias='cli')` and optional netconf connection available. |
| 6 | Testbed validation | Intentionally break YAML indentation, then fix it. | Validation fails first, then passes after correction. |
| 7 | AEtest structure | Create script with `CommonSetup`, one `Testcase`, and `CommonCleanup`. | Script runs and prints section order correctly. |
| 8 | AEtest parameters | Pass a parameter (device name) to testcase. | Script reads parameter and connects to selected device. |
| 9 | Steps API | Use `steps.start()` with two sub-steps in a test. | Report shows both steps and their status separately. |
| 10 | Skip/Pass/Fail | Add logic that skips if interface is admin down. | Test is marked `skipped` when condition is met. |
| 11 | Job file intro | Build a simple job file to launch one testscript. | `pyats run job job.py` executes script with runtime args. |

## Days 12–37: pyATS Exploration

| Day | Topic | Exercise | Solution (Expected Outcome) |
|---|---|---|---|
| 12 | Parser intro | Parse `show version` on one device. | `device.parse('show version')` returns a dictionary. |
| 13 | Parser traversal | Extract hostname and software version from parsed data. | Values printed without regex. |
| 14 | Multiple command parsing | Parse `show ip interface brief` and `show inventory`. | Two structured outputs stored in Python variables. |
| 15 | Error handling | Handle parser unsupported command gracefully. | Use fallback with `device.execute()` and log warning. |
| 16 | Data export | Save parsed output as JSON. | JSON file created with `json.dump(parsed, f, indent=2)`. |
| 17 | TDD basics | Write a failing test for interface count threshold. | Test fails first (`red`) before implementation. |
| 18 | Implement to pass | Add logic to satisfy threshold test. | Test passes (`green`) with minimal code. |
| 19 | Refactor | Refactor validation function without changing behavior. | Tests still pass after refactor. |
| 20 | Pytest + pyATS style | Add unit tests for helper function used by pyATS script. | `pytest` validates helper logic independently. |
| 21 | Boundary tests | Add tests for empty parser data and missing keys. | Function returns safe defaults instead of crashing. |
| 22 | TDD report | Document red/green/refactor cycle in README note. | Clear commit history shows incremental TDD flow. |
| 23 | Documentation snapshot | Capture hostname, version, serial into markdown report. | One markdown report generated per device. |
| 24 | Interface inventory | Build CSV of interfaces and IP addresses. | CSV includes headers and normalized values. |
| 25 | Config backup | Save running config for each device to files. | Timestamped config files created in backups folder. |
| 26 | Jinja2 intro | Render a small interface config template. | Template variables replaced correctly per device. |
| 27 | Report bundling | Merge inventory + config references into one report. | Final report links to all generated artifacts. |
| 28 | Test assertions | Build AEtest check for NTP server presence. | Pass/fail based on parsed running-config lines. |
| 29 | Interface state tests | Validate critical interfaces are `up/up`. | Fail section lists interfaces not meeting state. |
| 30 | Routing checks | Verify OSPF neighbors are in full state. | Parsed neighbor states all equal expected values. |
| 31 | BGP checks | Validate BGP summary has established peers. | Non-established peers flagged with details. |
| 32 | Golden baseline | Compare current output to golden JSON baseline. | Differences shown in structured diff output. |
| 33 | Trigger concept | Run built-in trigger in dry run mode. | Trigger loads and plans actions successfully. |
| 34 | Trigger execution | Execute simple interface flap trigger in lab. | Post-trigger verification confirms recovery. |
| 35 | Verification intro | Add verification for CPU threshold after trigger. | Test fails if CPU exceeds defined threshold. |
| 36 | Trigger + verification | Chain one trigger and two verifications. | End-to-end health result produced per device. |
| 37 | Reporting | Export trigger/verification result summary to HTML. | Shareable HTML report generated from runinfo. |

## Days 38–74: pyATS Odyssey (Core Advanced)

| Day | Topic | Exercise | Solution (Expected Outcome) |
|---|---|---|---|
| 38 | Config management intro | Create config snippet to enable logging buffered. | Snippet applied with `device.configure()` safely. |
| 39 | Idempotent config | Prevent duplicate configuration statements. | Script checks before pushing config changes. |
| 40 | Pre-check/post-check | Validate state before and after config deployment. | Pre/post comparison proves intended change only. |
| 41 | Rollback strategy | Save config checkpoint and rollback on failure. | Failure path restores previous running state. |
| 42 | Change audit | Log who/when/what for each config push. | Audit trail JSON generated per run. |
| 43 | Snapshot intro | Capture `learn interface` snapshot. | Snapshot file stored as baseline artifact. |
| 44 | Snapshot compare | Compare fresh snapshot with baseline. | Added/removed/changed entries displayed. |
| 45 | Feature snapshots | Capture snapshots for `routing` and `platform`. | Multi-feature baseline available for regression. |
| 46 | Drift detection | Flag unauthorized config or state drift. | Report identifies drift severity and scope. |
| 47 | Scheduled snapshots | Build script to take daily snapshots. | Timestamped snapshots created automatically. |
| 48 | Snapshot retention | Keep last 7 snapshots only. | Older files pruned by retention logic. |
| 49 | Record traffic | Use pyATS recording during test execution. | Session record created for replay. |
| 50 | Playback basics | Replay a recorded session without device access. | Parser-driven tests run on mocked responses. |
| 51 | Mock testbed | Build mock testbed for two devices. | Offline validation works for both nodes. |
| 52 | Unit tests with playback | Use playback in CI-friendly test execution. | Deterministic tests pass without lab dependency. |
| 53 | Record refresh | Re-record session after software upgrade. | Fixtures updated and tests remain stable. |
| 54 | API basics | Call REST API endpoint and parse JSON response. | HTTP status check + JSON schema validation passes. |
| 55 | Auth handling | Implement token-based API auth securely. | Token reused and refreshed when expired. |
| 56 | API + device correlation | Compare API inventory with CLI parsed inventory. | Mismatch report highlights inconsistencies. |
| 57 | API-driven test data | Generate testcase inputs from API payload. | Dynamic parameterization from external source works. |
| 58 | API exception paths | Handle 429/500 responses with retry/backoff. | Retries succeed or fail with clear reason. |
| 59 | pcall intro | Run the same check on many devices concurrently. | Reduced runtime versus sequential execution. |
| 60 | Thread-safe logging | Add per-device log context in pcall tasks. | Logs remain readable and non-overlapping. |
| 61 | Parallel parser runs | Parse command set concurrently for inventory. | Results merged into consolidated dictionary. |
| 62 | Timeout tuning | Set worker timeout and error capture for slow devices. | Hung tasks terminate cleanly with error metadata. |
| 63 | Concurrency benchmark | Compare sequential vs pcall run durations. | Benchmark table proves performance gain. |
| 64 | Clean basics | Build minimal clean YAML with reload stage. | `pyats clean` starts and executes declared stages. |
| 65 | Device recovery | Add password recovery stage for lab router. | Device returns to reachable state after failure. |
| 66 | Image management | Validate and copy target image before upgrade. | Clean process verifies image integrity. |
| 67 | Golden config apply | Apply base config as part of clean workflow. | Device finishes with expected baseline config. |
| 68 | Clean verification | Add post-clean checks for management reachability. | Post stage confirms SSH/API access restored. |
| 69 | Clean reporting | Export clean summary with stage durations. | Report shows success/failure per stage. |
| 70 | Blitz basics | Write first blitz YAML action sequence. | Command, parse, and verify actions run in order. |
| 71 | Conditional logic | Add `if`/`else` branching in blitz actions. | Flow adapts based on parsed values. |
| 72 | Looping actions | Run same validation across interface list in blitz. | Loop emits per-interface result entries. |
| 73 | Variable reuse | Store output and reuse variables in later actions. | Captured variables resolve correctly. |
| 74 | Blitz report polish | Add clear section names and comments in blitz file. | Human-readable blitz report improves troubleshooting. |

## Days 75–100: pyATS Odyssey (Ecosystem + Mastery)

| Day | Topic | Exercise | Solution (Expected Outcome) |
|---|---|---|---|
| 75 | Container basics | Run pyATS in Docker and mount local workspace. | Container executes `pyats version` successfully. |
| 76 | Reproducible env | Build Dockerfile with pinned pyATS dependencies. | Team uses same image for consistent runs. |
| 77 | Containerized job | Execute job file from inside container. | Artifacts generated on mounted host path. |
| 78 | Compose workflow | Create docker-compose for pyATS + mock service. | One command boots full dev test environment. |
| 79 | Container CI | Use same container image in local and CI pipeline. | No “works on my machine” drift observed. |
| 80 | Health check intro | Enable pyATS health check plugin in test run. | Health sections appear before/after tests. |
| 81 | Custom health profile | Define CPU/memory/interface thresholds. | Health evaluation uses custom limits. |
| 82 | Continuous health | Run health checks periodically with scheduler. | Time-series health snapshots collected. |
| 83 | Alerting | Send alert when health check fails. | Webhook/email notification generated on failure. |
| 84 | Health dashboard input | Export health results in dashboard-friendly JSON. | JSON can be ingested by Grafana/ELK pipeline. |
| 85 | XPRESSO onboarding | Connect testbed and run first task in XPRESSO UI. | Job visible with pass/fail and logs in UI. |
| 86 | XPRESSO artifacts | Attach reports and logs to XPRESSO task results. | Centralized artifact tracking available. |
| 87 | Team workflow | Create shared XPRESSO project with role separation. | Team members can run/audit tests by role. |
| 88 | XPRESSO scheduling | Schedule recurring nightly regression in XPRESSO. | Runs execute automatically at configured time. |
| 89 | CI pipeline basics | Add pyATS run stage to GitHub Actions or Jenkins. | Pipeline runs tests on each push/PR. |
| 90 | Quality gates | Fail pipeline when critical pyATS tests fail. | Merge blocked until critical checks pass. |
| 91 | Artifact publishing | Upload pyATS logs/reports as CI artifacts. | Run diagnostics available for each build. |
| 92 | Branch strategy | Run smoke on feature branch, full regression on main. | Faster feedback with risk-based pipeline design. |
| 93 | Robot intro | Execute simple Robot test that calls pyATS library. | Robot report shows one passing pyATS-based keyword. |
| 94 | Robot data-driven | Parameterize Robot suite for multiple devices. | Same keyword validates each target device. |
| 95 | Robot + parser | Use pyATS parser output in Robot assertions. | Structured checks replace fragile text matching. |
| 96 | Robot in CI | Run Robot + pyATS suite in pipeline with reports. | XML/HTML reports published automatically. |
| 97 | AI-assisted test design | Use AI to draft a pyATS testcase from requirements. | Draft converted into runnable AEtest script. |
| 98 | AI-assisted troubleshooting | Feed failed logs to AI and review hypotheses. | Root-cause suggestions mapped to evidence lines. |
| 99 | AI guardrails | Define human review checklist for AI-generated tests. | Checklist prevents unsafe config/test operations. |
| 100 | Capstone day | Build end-to-end workflow: testbed → tests → report → CI. | Full demo run validates complete pyATS learning journey. |

---

## Capstone Solution Blueprint (Day 100)

Use this structure for the final challenge:

1. **Prepare**: valid `testbed.yaml`, credentials, and connectivity checks.
2. **Validate**: run AEtest scripts for baseline health and critical protocols.
3. **Verify drift**: compare snapshots against golden baseline.
4. **Report**: export HTML/JSON artifacts.
5. **Automate**: execute through CI pipeline on each change window.

Minimal command flow example:

```bash
pyats validate testbed testbed.yaml
pyats run job jobs/regression_job.py --testbed-file testbed.yaml
pyats logs view
```

You now have a reusable workbook to practice consistently from **Day 1 to Day 100**.

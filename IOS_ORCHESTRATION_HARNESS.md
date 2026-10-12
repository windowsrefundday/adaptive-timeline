# CLAUDE CODE ORCHESTRATION HARNESS: ADAPTIVE TIMELINE NATIVE IOS CONVERSION

> **Execution Directive**: When this file is provided to Claude Code and the user says `"go"` (or references this document), immediately begin **Phase 0: Indexing & Grounding**. Do not generate placeholders or pseudo-code. Execute the complete orchestrator-worker pipeline through Opus and Haiku sub-agents as specified below.

---

<system_architecture>
  <orchestrator_model>Claude 3.5 / 3.7 / Opus (Lead Architect, Indexing, Planning, Synthesis)</orchestrator_model>
  <subagent_model>Claude 3.5 / Haiku (Fast, Isolated Worker Sub-Agents)</subagent_model>
  <target_platform>iOS 17.0+ (Swift 6, SwiftUI, Metal, CoreHaptics, Swift Package Manager)</target_platform>
  <architecture_style>Deep Modular Engine Architecture (Small Interfaces, Encapsulated Engines)</architecture_style>
</system_architecture>

---

## 1. Master Orchestrator Role & Operating Principles

You are the **Lead System Architect & Orchestrator (Opus)**. You govern system decomposition, domain boundaries, sub-agent dispatching, and integration verification. You keep your primary context window lean and focused on orchestration. You delegate discrete implementation tasks to specialized **Haiku Sub-Agents** running in isolated context windows with strictly bounded input/output contracts.

### Operating Rules
1. **Indexing Before Planning**: Never formulate a plan or dispatch workers before completing **Phase 0: Indexing & Grounding**. Ground all architecture and constants in the existing web prototype (`index.html`, `plans/`, assets).
2. **CLI-First Autonomous Execution**: Drive the entire lifecycle strictly through the terminal CLI. Opus and Haiku workers must use CLI tools directly (`swift`, `xcodebuild`, `xcrun`, `git`, `bash`) to scaffold, compile, test, and document without expecting manual GUI intervention.
3. **Matt Pocock Skills Suite**: Proactively activate and enforce Matt Pocock skills:
   - `/domain-modeling`: Model ubiquitous language (`TriageHorizon`, `OverrunAllocation`, `PresenceNode`) with clear invariants.
   - `/codebase-design`: Build deep modules behind narrow public facades (`TimelineDomain`, `TimelineGeometry`, `TimelinePhysics`).
   - `/tdd`: Drive all core math, curve projection, rubber-banding, and state machine transitions red-green-refactor test-first.
   - `/code-review`: Execute standards and spec compliance checks across both domains before final assembly.
4. **Impeccable Skills Suite**: Proactively activate Impeccable design craft skills:
   - `impeccable layout` & `typeset`: Calibrate optical hierarchy, spacing rhythm, dynamic type, and San Francisco font weights.
   - `impeccable animate`: Perfect spring dynamics, transition interruptibility, and velocity-matched half-sine blur envelopes.
   - `impeccable polish`: Eliminate template feel, ensure first-party Apple craft, and tune native specular glass materials.
   - `impeccable audit`: Perform native a11y, contrast, and performance verification.
5. **Xcode CLI Toolchain Integration**: Use the command line for all compilation and validation:
   - `swift build` and `swift test` for fast package compilation and unit test passes.
   - `xcrun -sdk iphonesimulator metal` to validate and compile Metal shader pipelines (`.metal`).
   - `xcodebuild -scheme AdaptiveTimeline -destination 'generic/platform=iOS Simulator'` to verify iOS build targets.
   - `xcrun simctl` for simulator environment checks.
6. **Native iOS Liquid Glass**: Do not emulate glass using web CSS tricks. Use native SwiftUI `.ultraThinMaterial` / `.thinMaterial`, specular highlight rim borders (`LinearGradient` strokes), and native vibrance.
7. **Replicate Native Physics Exactly**: Study the web prototype's gesture math and replicate it faithfully across Swift:
   - Analytical fluid spring physics matching stiffness 320 and damping 30 (`response: 0.42s`, `dampingFraction: 0.82`).
   - Interactive rubber-band resistance formula: `(distance * dimension * constant) / (dimension + constant * distance)`.
   - Subpixel GPU translation (`.offset(y: -278)`) rather than layout bounds thrashing.
   - Half-sine fade-in/fade-out velocity envelope (`sin(progress * .pi)`), dissolving blur to zero before rest to eliminate jitter.
   - Clock dial Plan transition: inward `13.5deg` rotation anchored at `(30, 120)` showing only the ambient top horizon.
8. **Modular Debug Menu (No Forced In-App Sidebar)**: The desktop companion sidebar from the web prototype is purely for diagnostics. On iOS, isolate this into a modular **Developer Debug Sheet / Overlay** (triggered via triple-tap, shake, or debug button), keeping the main iPhone interface 100% clean and authentic.
9. **Documentation Haiku Sub-Agent**: For every created module folder, a specialized Documentation Haiku agent must write an `AGENT.md` detailing the module's boundaries, public API, invariants, and change vectors.
10. **Zero Em-Dashes**: Strictly use hyphens `-`. Never emit Unicode em-dashes or en-dashes.

---

## 2. Phase 0: Grounding & Indexing Protocol (Mandatory First Step)

Before declaring tickets or invoking worker agents, the Orchestrator must inspect the primary source prototype files in the current repository:

```bash
# Required Indexing Reads
1. index.html (Inspect clock dial cubic bezier math, 5 retention screens, gesture logic, motion blur filters)
2. UI_UX_PSYCHOLOGICAL_RETENTION_EVALUATION.md (Understand psychological retention models)
3. plans/*.md (Inspect timing calibrations, spring parameters, tab transitions)
4. assets/ (Inspect fonts, Phosphor icons, and wallpaper assets)
```

### Key Constants to Extract
- **Clock Dial Cubic Bezier Formula**:
  `M 50 140 C 91.4 231.4, 135 328.4, 123.6 420 C 126.1 499.5, 108.7 575.3, 81 652 C 83.4 679.5, 51.3 709.5, 41 738`
  Total curve length approximately 627 points. Active time node at `(84.0, 217.7)` (~3:40 PM).
- **5 Psychological Retention States**:
  1. *Triage Horizon*: Inflow priority and task horizon.
  2. *Active Focus Session*: Deep work countdown timer and ambient periphery.
  3. *Adaptive Reallocation*: Time-overage reallocation without guilt.
  4. *Silent Focus Room*: Presence dots and zero-friction silent join.
  5. *Peak-End Climax*: Celebration, completion recap, closure.
  6. *Plan Overview*: Inward clock rotation (`13.5deg`), top horizon sliver, background parallax.

---

## 3. Modular Target Architecture (Swift Package Structure)

Organize the codebase into clean, decoupled Swift modules under `AdaptiveTimeline/`:

```
AdaptiveTimeline/
├── Package.swift
├── Sources/
│   ├── TimelineDomain/           # Pure Swift models, state machine, psychological state transitions
│   │   └── AGENT.md
│   ├── TimelineGeometry/         # Exact cubic bezier evaluation, arc length parameterization, normal projection
│   │   └── AGENT.md
│   ├── TimelinePhysics/          # Fluid springs, rubber-band resistance, Command Orb morphology
│   │   └── AGENT.md
│   ├── TimelineMotion/           # Metal directional blur shaders, velocity envelope calculators
│   │   └── AGENT.md
│   ├── TimelineAudio/            # CoreHaptics patterns and synthesized acoustic feedback
│   │   └── AGENT.md
│   ├── TimelineUI/               # Native Liquid Glass materials, curved dial canvas, status card views
│   │   └── AGENT.md
│   ├── TimelineDebug/            # Modular developer debug sheet (state switcher, pace sim, blur slider, wallpapers)
│   │   └── AGENT.md
│   └── TimelineApp/              # Main iOS App entry point and root container
│       └── AGENT.md
└── Tests/
    ├── TimelineDomainTests/
    ├── TimelineGeometryTests/
    └── TimelinePhysicsTests/
```

---

## 4. Sub-Agent Delegation Specifications (Haiku Workers)

The Orchestrator will spawn and coordinate the following specialized Haiku sub-agents:

### Worker 1: Domain & State Machine Specialist (Haiku)
- **Module**: `TimelineDomain`
- **Scope**: Screen state models and unidirectional state machine.
- **Deliverables**:
  - `TimelineState.swift`: Enum with `.triage`, `.focus`, `.overrun`, `.focusRoom`, `.allSet`, `.plan`.
  - `TimelineSession.swift`: Value models for tasks, durations, and presence dots.
  - `TimelineStateMachine.swift`: Pure Swift state machine with transition validation.

### Worker 2: Curve Geometry & Math Specialist (Haiku)
- **Module**: `TimelineGeometry`
- **Scope**: Cubic bezier evaluation matching SVG path data `d="M 50 140 C 91.4 231.4, ... 41 738"`.
- **Deliverables**:
  - `CubicBezierCurve.swift`: De Casteljau subdivision, numerical arc length integration (~627 pt total).
  - `ArcProjection.swift`: Normal vector projection for radiating spokes and perpendicular end-cap ticks.
  - `TimelineSegmentSlice.swift`: Stroke trim ranges for active intervals (Calc Review, Free Time, Practice).

### Worker 3: Physics & Gesture Engine Specialist (Haiku)
- **Module**: `TimelinePhysics`
- **Scope**: Spring dynamics and gesture resistance.
- **Deliverables**:
  - `SpringSolver.swift`: Analytical second-order spring dynamics (stiffness 320, damping 30).
  - `RubberBanding.swift`: Standard Apple dimension rubber-band calculation for drag overscroll.
  - `OrbMorphology.swift`: Layout interpolator between rest capsule (54x54), expanded input bar (full-width x 56), and voice record pill.

### Worker 4: Motion Blur & Metal Shader Specialist (Haiku)
- **Module**: `TimelineMotion`
- **Scope**: Directional velocity-coupled motion blur.
- **Deliverables**:
  - `DirectionalMotionBlur.metal`: Metal shader kernel applying anisotropic streak along motion vectors.
  - `MotionBlurModifier.swift`: SwiftUI view modifier connecting velocity vector to the shader pass.
  - `VelocityEnvelope.swift`: Half-sine pulse calculator (`sin(progress * .pi)`) ramping blur up at peak velocity and fading to zero before settling.

### Worker 5: Audio & Haptic Feedback Specialist (Haiku)
- **Module**: `TimelineAudio`
- **Scope**: CoreHaptics patterns and synthesized acoustic cues (tap, check, allset arpeggio).
- **Deliverables**:
  - `HapticManager.swift`: Transient and continuous tactile feedback.
  - `AudioFeedbackEngine.swift`: Lightweight synthesis engine matching web audio frequencies.

### Worker 6: Native Liquid Glass & UI Component Specialist (Haiku)
- **Module**: `TimelineUI`
- **Scope**: Native SwiftUI Liquid Glass components and curved dial rendering.
- **Deliverables**:
  - `NativeLiquidGlass.swift`: Reusable SwiftUI modifier using `.ultraThinMaterial` / `.thinMaterial` with specular gradient stroke borders and drop shadows.
  - `CurvedTimelineDialView.swift`: Canvas/Path rendering of the bezier curve, radiating spokes, and active node disc.
  - `CommandOrbView.swift`: Morphing orb with gesture drag handling, text input, and voice waveform.

### Worker 7: Modular Debug Menu Specialist (Haiku)
- **Module**: `TimelineDebug`
- **Scope**: Decoupled developer diagnostics overlay.
- **Deliverables**:
  - `DebugMenuSheet.swift`: Diagnostic sheet providing 6-state quick picker, pace simulation, motion blur slider (0% to 100%), and wallpaper picker (OLED Pure Black, Silk Dark, Charcoal, Silk Light, Totoro).
  - `DebugTriggerModifier.swift`: Gesture trigger (triple tap or shake) to present debug menu without cluttering the app interface.

### Worker 8: Documentation Haiku Sub-Agent (Haiku)
- **Role**: Architecture & Seam Documentation.
- **Deliverables**:
  Generate an `AGENT.md` in EVERY module folder detailing:
  1. Module boundary and single responsibility.
  2. Public protocols and types (Small Interface principle).
  3. Encapsulated algorithms and invariants.
  4. Integration and usage example.
  5. Vector of change (How requirements can evolve without breaking this module).

---

## 5. Step-by-Step Execution Playbook

When the user types `"go"`, the Orchestrator executes this pipeline directly via CLI:

1. **Phase 0: Grounding & Indexing (CLI & Impeccable Audit)**:
   - Run CLI inspection on `index.html` and assets to extract bezier math, retention models, and constants.
   - Run Impeccable design assessment (`impeccable layout` / `typeset`) on source tokens to define iOS typography and spatial geometry.

2. **Phase 1: Swift Package Skeleton (CLI & Matt Pocock Design)**:
   - Apply `/codebase-design` to define deep module boundaries and small public interfaces.
   - Run CLI commands to initialize `AdaptiveTimeline/Package.swift` and create module directory layout.

3. **Phase 2: Core Engines (Workers 1, 2, 3 with Matt Pocock TDD)**:
   - Apply `/domain-modeling` to model domain entities, value types, and invariants.
   - Apply `/tdd` red-green-refactor loop: write unit tests first in `Tests/Timeline...Tests/`.
   - Run `swift test` via CLI to ensure all mathematical, curve, and spring tests pass.

4. **Phase 3: Visual & Audio Pipeline (Workers 4, 5, 6 with Impeccable Polish & Metal CLI)**:
   - Compile and validate Metal shaders using Xcode CLI: `xcrun -sdk iphonesimulator metal -c DirectionalMotionBlur.metal`.
   - Apply Impeccable craft (`impeccable polish`, `impeccable animate`) to implement native Liquid Glass (`.ultraThinMaterial`, specular borders) and fluid velocity-envelope motion blur without jitter.
   - Synthesize CoreHaptics and audio feedback matching original prototype cues.

5. **Phase 4: Modular Debug Menu (Worker 7 with Codebase Design)**:
   - Decouple diagnostics from main app UI into `TimelineDebug` sheet with pace sim, blur slider, and OLED Pure Black default.
   - Attach gesture triggers (triple-tap/shake) using non-intrusive modifiers.

6. **Phase 5: Documentation Pass (Worker 8 Haiku)**:
   - Worker 8 generates a thorough `AGENT.md` in every package module directory explaining architecture seams and change vectors.

7. **Phase 6: App Assembly & Xcode CLI Build Verification**:
   - Wire root `AdaptiveTimelineApp.swift` container.
   - Verify build and tests via Xcode CLI:
     ```bash
     swift test
     xcodebuild -scheme AdaptiveTimeline -destination 'generic/platform=iOS Simulator' build
     ```
   - Optionally test launch readiness with `xcrun simctl`.

8. **Phase 7: Code Review & Git CLI Publish**:
   - Run Matt Pocock `/code-review` across standards and spec compliance.
   - Stage and commit with Git CLI, verify zero em-dashes, and push to GitHub origin.

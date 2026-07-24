Markdown# ⚡ DawGroomer | AI Systems & Prompt Architect

```xml
<developer_profile>
  <entity>DawGroomer</entity>
  <role>Lead AI Systems Architect & Local-First Engineer</role>
  <organization>Kynolith LLC</organization>
  <visibility_notice status="classified">
    Primary production codebases (Kynolith-Core, Forge-Studio) remain housed in 
    private repositories to protect local configurations, API security, and proprietary IP.
  </visibility_notice>
  <core_competencies>
    <competency>Local-First Multi-Model Orchestration</competency>
    <competency>Deterministic System Contracts & XML Schemas</competency>
    <competency>Real-Time High-Throughput Telemetry Bridges</competency>
    <competency>Low-Latency Cue Scheduling & Guardrail Engineering</competency>
  </core_competencies>
</developer_profile>
🏛️ Featured Architecture Spec: Kynolith ApexXML<system_architecture_manifest>
  <system_name>Kynolith Apex</system_name>
  <type>Real-Time Telemetry & Agentic AI Driver Coaching Engine</type>
  <native_bridge>.NET 9 x64 Shared-Memory Bridge (LMU 3.8 Layouts)</native_bridge>
  <app_server>TypeScript (Node.js 22 / Electron Desktop Shell)</app_server>
  <ai_pipeline>Local-First LLM & Voice Execution Pipeline</ai_pipeline>
</system_architecture_manifest>
Packaged Windows ApplicationDownload the latest portable Windows executable from the repository's GitHub Releases page. Start Apex before opening LMU. The desktop application launches its embedded bridge and connects automatically when LMU exposes the supported shared-memory mappings.The current bridge targets LMU 3.8 shared-memory layouts and validates structure sizes before reading data. Unknown layouts are rejected instead of guessed.Run from sourceRequirements:Windows 10 or Windows 11, x64Node.js 22pnpm 10 or newer.NET 9 SDK for the native LMU bridgeLe Mans Ultimate with shared-memory telemetry enabledPowerShellgit clone [https://github.com/DawGroomer/Kynolith-Apex.git](https://github.com/DawGroomer/Kynolith-Apex.git)
cd Kynolith-Apex
pnpm install --frozen-lockfile
pnpm typecheck
pnpm test
pnpm start
Run pnpm dist:win. This publishes the self-contained x64 .NET telemetry bridge, verifies its LMU 3.8 structure sizes, compiles the TypeScript server, and packages both into a portable Electron executable under release/.Open http://127.0.0.1:4377. Source mode starts with a simulator data source so the dashboard and voice pipeline can be tested without entering LMU.Run the Electron desktop shell during development:PowerShellpnpm desktop
Build the Windows executablePowerShellpnpm dist:win
The build performs the following work:Publishes the self-contained x64 .NET telemetry bridgeValidates LMU telemetry and scoring structure sizesCompiles the TypeScript serverPackages the bridge, dashboard, and optional offline modelsWrites a portable executable under release/Tagged GitHub builds support Authenticode signing when the Kynolith certificate and password secrets are configured.Development commandsCommandPurposepnpm devStart the TypeScript server in watch modepnpm startStart the local serverpnpm desktopLaunch the Electron desktop applicationpnpm typecheckRun TypeScript validationpnpm testRun deterministic unit and integration testspnpm test:soak:acceleratedSimulate one hour of 67 Hz telemetrypnpm test:soakRun the one-hour telemetry soak in real timepnpm test:local-aiPopulate and verify local language modelspnpm test:local-voicePopulate and verify the local voice pipelinepnpm build:bridgePublish and validate the native LMU bridgepnpm buildCompile TypeScriptpnpm models:stageStage offline models for packagingpnpm dist:winBuild the portable Windows applicationValidation strategyXML<validation_harness>
  <ci_pipeline>
    <check>TypeScript static analysis & compilation</check>
    <check>Deterministic coaching & integration tests</check>
    <check>Recorded, sanitized LMU fixture replay</check>
    <check>Accelerated 1-hour telemetry soak testing</check>
    <check>Native shared-memory bridge build & layout validation</check>
  </ci_pipeline>
  <telemetry_metrics>Accepted, processed, dropped, out-of-order, queue-depth, latency</telemetry_metrics>
</validation_harness>
The telemetry pipeline records accepted, processed, dropped, out-of-order, queue-depth, and latency metrics. Reference comparisons use distance interpolation and disclose uncertainty instead of presenting sample-boundary estimates as exact.Known limitationsWindows and Le Mans Ultimate onlyThe native bridge is version-sensitive by designRaw proprietary MoTeC .ld files are not parsed directlyCalibration requires representative human expert labels; Apex does not fabricate themOffline model staging produces a large Windows packageApex supplements—but does not replace—LMU flags, mirrors, visual spotters, or driver awarenessProject structurePlaintextbridge/          Native .NET LMU shared-memory bridge
electron/        Electron desktop entry point
public/          Cockpit dashboard and settings interface
scripts/         Packaging, migration, reference, and soak tools
src/             Coaching, telemetry, analysis, voice, and server modules
test/fixtures/   Sanitized LMU telemetry fixtures
offline-models/  Optional staged local model assets
Third-party acknowledgementsThe cue scheduler's priority, expiry, revalidation, and hard-section concepts are informed by Crew Chief V4. Apex is an independent application and does not distribute Crew Chief source code. See THIRD_PARTY_NOTICES.md for attribution and dependency notices.StatusKynolith Apex is under active development. Data-quality status, calibration confidence, and telemetry health are exposed deliberately so drivers can distinguish measured evidence from provisional guidance.Built by Kynolith LLC for drivers who want a coach—not another dashboard.

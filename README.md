### Packaged Windows application

Download the latest portable Windows executable from the repository's GitHub Releases page. Start Apex before opening LMU. The desktop application launches its embedded bridge and connects automatically when LMU exposes the supported shared-memory mappings.

The current bridge targets LMU 3.8 shared-memory layouts and validates structure sizes before reading data. Unknown layouts are rejected instead of guessed.

### Run from source

Requirements:

- Windows 10 or Windows 11, x64
- Node.js 22
- pnpm 10 or newer
- .NET 9 SDK for the native LMU bridge
- Le Mans Ultimate with shared-memory telemetry enabled

```powershell
git clone https://github.com/DawGroomer/Kynolith-Apex.git
cd Kynolith-Apex
pnpm install --frozen-lockfile
pnpm typecheck
pnpm test
pnpm start
```

Run `pnpm dist:win`. This publishes the self-contained x64 .NET telemetry bridge, verifies its LMU 3.8 structure sizes, compiles the TypeScript server, and packages both into a portable Electron executable under `release/`.
Open `http://127.0.0.1:4377`. Source mode starts with a simulator data source so the dashboard and voice pipeline can be tested without entering LMU.

Run the Electron desktop shell during development:

```powershell
pnpm desktop
```

## Build the Windows executable

```powershell
pnpm dist:win
```

The build performs the following work:

1. Publishes the self-contained x64 .NET telemetry bridge
2. Validates LMU telemetry and scoring structure sizes
3. Compiles the TypeScript server
4. Packages the bridge, dashboard, and optional offline models
5. Writes a portable executable under `release/`

Tagged GitHub builds support Authenticode signing when the Kynolith certificate and password secrets are configured.

## Development commands

| Command | Purpose |
| --- | --- |
| `pnpm dev` | Start the TypeScript server in watch mode |
| `pnpm start` | Start the local server |
| `pnpm desktop` | Launch the Electron desktop application |
| `pnpm typecheck` | Run TypeScript validation |
| `pnpm test` | Run deterministic unit and integration tests |
| `pnpm test:soak:accelerated` | Simulate one hour of 67 Hz telemetry |
| `pnpm test:soak` | Run the one-hour telemetry soak in real time |
| `pnpm test:local-ai` | Populate and verify local language models |
| `pnpm test:local-voice` | Populate and verify the local voice pipeline |
| `pnpm build:bridge` | Publish and validate the native LMU bridge |
| `pnpm build` | Compile TypeScript |
| `pnpm models:stage` | Stage offline models for packaging |
| `pnpm dist:win` | Build the portable Windows application |

## Validation strategy

The Windows CI pipeline runs:

- TypeScript type checking
- Deterministic coaching and integration tests
- Recorded, sanitized LMU fixture replay
- Accelerated one-hour telemetry soak testing
- Native shared-memory bridge build and layout validation
- Production TypeScript compilation
- Portable Windows packaging

The telemetry pipeline records accepted, processed, dropped, out-of-order, queue-depth, and latency metrics. Reference comparisons use distance interpolation and disclose uncertainty instead of presenting sample-boundary estimates as exact.

## Known limitations

- Windows and Le Mans Ultimate only
- The native bridge is version-sensitive by design
- Raw proprietary MoTeC `.ld` files are not parsed directly
- Calibration requires representative human expert labels; Apex does not fabricate them
- Offline model staging produces a large Windows package
- Apex supplements—but does not replace—LMU flags, mirrors, visual spotters, or driver awareness

## Project structure

```text
bridge/          Native .NET LMU shared-memory bridge
electron/        Electron desktop entry point
public/          Cockpit dashboard and settings interface
scripts/         Packaging, migration, reference, and soak tools
src/             Coaching, telemetry, analysis, voice, and server modules
test/fixtures/   Sanitized LMU telemetry fixtures
offline-models/  Optional staged local model assets
```

## Third-party acknowledgements

The cue scheduler's priority, expiry, revalidation, and hard-section concepts are informed by Crew Chief V4. Apex is an independent application and does not distribute Crew Chief source code. See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for attribution and dependency notices.

## Status

Kynolith Apex is under active development. Data-quality status, calibration confidence, and telemetry health are exposed deliberately so drivers can distinguish measured evidence from provisional guidance.

Built by **Kynolith LLC** for drivers who want a coach—not another dashboard.

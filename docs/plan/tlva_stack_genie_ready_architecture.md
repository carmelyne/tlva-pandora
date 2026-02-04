# TLVA Stack + Genie-Ready Architecture (Draft)

## Goals
- Support Android TV, Apple TV (tvOS), mobile, and web.
- Keep the client thin; push learning logic, AI rules, and content to shared backend.
- Design a “world model slot” from day one so Genie (or any provider) can be added later.

## Recommended Stack (Aligned to TS/Rust)
- Web: SvelteKit
- Mobile + TV: thin native shells
  - Android / Android TV: Kotlin + Compose for TV
  - iOS / tvOS: SwiftUI/UIKit
- Backend core: TypeScript (Node)
- Real-time/streaming gateway: Rust
- Data: Postgres + Redis
- Storage/CDN: S3-compatible + CDN

## Architecture Overview
Clients speak a small, stable protocol. The backend chooses the provider for each scene.

```
Client (TV/Mobile/Web)
  ↕ input_events (HTTP)
  ← scene_state (SSE)
  ← media (HLS / static assets)
         |
         v
World Orchestrator (TS)
  → provider.select(scene, user)
  → provider.render(context)
         |
         v
Provider (Authored | Hybrid | World-Model)
```

## World Model Slot (Provider Interface)
Each provider implements:
- `capabilities()` → input types, latency budget, render mode
- `start(scene_context)` → initializes session
- `input(event)` → accepts user input
- `stream()` → outputs frame/audio/state events
- `stop()`

Provider types:
- `authored`: default content (videos + scripted interactions)
- `hybrid`: authored base + model overlays
- `world_model`: future Genie-like provider

## Streaming Plan
### POC (No WebSocket)
- Downlink: Server-Sent Events (SSE) for state updates
- Uplink: HTTPS POST for inputs
- Media: HLS for video segments

### Genie-Ready Phase
- Media + input over WebRTC
- Optional data channel for low-latency inputs
- Fallback to SSE/HTTP if WebRTC unavailable

## Why This Works
- Thin clients keep platform-specific code minimal.
- The provider interface isolates future world-model integration.
- SSE + HTTP keeps the POC simple without locking out future WebRTC.
- HLS is stable on Apple devices and easy to serve from CDNs.

## Phase 1 Scope (POC)
- One region (Word Forest)
- Authored content provider
- Basic input + feedback loop
- Metrics: session length, replay rate, accuracy, help usage

## Phase 2+ (Genie-Ready)
- Add `world_model` provider
- AB-test provider selection per scene
- Introduce low-latency transport (WebRTC)

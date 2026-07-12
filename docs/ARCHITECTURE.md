# Architecture — TraceMap

## High-Level Design (HLD)
TraceMap instruments services with OpenTelemetry and stitches spans into end-to-end traces, so I can see exactly where latency and errors originate across the system.

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#ffffff','lineColor':'#2563eb','mainBkg':'#ffffff'}}}%%
graph LR
    A([Request])
    B([OTel Spans])
    C([Trace Assembly])
    D([Visualization])
    A --> B
    B --> C
    C --> D
    style A fill:#eff6ff,stroke:#2563eb,stroke-width:2px,color:#1e40af
    style B fill:#eff6ff,stroke:#2563eb,stroke-width:2px,color:#1e40af
    style C fill:#eff6ff,stroke:#2563eb,stroke-width:2px,color:#1e40af
    style D fill:#eff6ff,stroke:#2563eb,stroke-width:2px,color:#1e40af
```

**Flow:** Request → OTel Spans → Trace Assembly → Visualization

## Low-Level Design (LLD)
- **Components:** `OpenTelemetry`, `Node.js`
- **Interfaces / contracts:** to be finalized during implementation.
- **Data model:** to be defined per component.

## Decision Log
- **Why this stack:** **OpenTelemetry** — distributed tracing; **Node.js** — application runtime / service layer.
- **Antigravity constraint:** run logic/state/UI locally; offload heavy reasoning to cloud APIs; target modest hardware.

## Concept Deep Dive
Propagating trace context cleanly across async boundaries so traces stay complete.

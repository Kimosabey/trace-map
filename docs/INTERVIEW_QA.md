# Interview Q&A — TraceMap

### "Tell me about this project."
TraceMap is distributed tracing that follows a request across every service it touches. TraceMap instruments services with OpenTelemetry and stitches spans into end-to-end traces, so I can see exactly where latency and errors originate across the system.

### "What was the hardest part?"
Propagating trace context cleanly across async boundaries so traces stay complete.

### "Why did you choose this stack?"
- **OpenTelemetry** — distributed tracing.
- **Node.js** — application runtime / service layer.

### "How does it fit the rest of your portfolio?"
It follows my "Antigravity" model — local logic/state/UI, cloud reasoning where it earns its cost — and shares the documentation and deployment conventions used across all my projects (#43).

---
layout: home
title: Anthony Eckmann
---

<p><strong>Real-time streaming pipelines, ML microservices, and data-quality engineering for mobility analytics.</strong></p>

## About

I build robust systems that turn noisy real-world movement data into accurate, privacy-aware insights. My work spans streaming pipelines, map-matching and journey-reconstruction logic, ML microservices, and operational improvements that make models and pipelines easier to run in production.

## Projects

### Posmo Streaming — real-time movement recording pipeline
- Built and improved streaming logic to reliably detect and persist moving and non-moving events.
- Added open-idle extension logic and guards to avoid duplicate or premature persistence.
- Fixed edge cases (short noisy walk segments, static point checks) to reduce false positives in mode detection.

Repository: https://github.com/datamapio/posmo_streaming

---

### Public-transport (PT) map-matching & journey reconciliation
- Reconciled fragmented PT journeys and improved station-detection to produce continuous and accurate transit journeys from noisy sensor data.
- Implemented map-matching and reconciliation pipelines to merge incomplete PT journeys into continuous journeys.

Repository: [Posmo Streaming — PT work](https://github.com/datamapio/posmo_streaming)

---

### ML microservice optimizations (posmo-ml-microservice)
- Reduced cold-start time by limiting model downloads to only what's necessary.
- Fixed prediction output handling so results align with supported transport modes.

Repository: https://github.com/datamapio/posmo-ml-microservice

---

## Contact
- GitHub: [aecki](https://github.com/aecki)
- Email: anthony95<at>gmx.com

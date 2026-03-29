# Space Mission Protocol — MissionLink & TelemetryStream

A distributed communication system built in Python for the Computer Communications course at the University of Minho.

The project simulates a space mission where a Mothership coordinates a fleet of autonomous Rovers on a planetary surface. Communication between entities is handled by two custom application-layer protocols built on top of UDP and TCP.

## Protocols

**MissionLink (UDP)** — handles critical mission transactions including assignment, progress reports and conclusion. Since UDP offers no delivery guarantees, a reliability layer was implemented from scratch, including sequence numbers, ACKs, retransmission timers and exponential backoff.

**TelemetryStream (TCP)** — handles continuous real-time monitoring of each Rover's position, battery level and operational state, using fixed-size 39-byte messages for efficient parsing.

## Architecture
- Client-server with automatic service discovery — Rovers register with the Mothership on startup
- Multi-threaded server capable of handling multiple Rovers concurrently
- RESTful monitoring API (`GET /api/status`) consumed by a CLI Ground Control dashboard
- Persistent storage of mission history and telemetry logs in JSON

## Tech Stack
Python, sockets (UDP/TCP), threading, HTTP, JSON

## How to Run
```bash
python mothership.py
python rover_main.py
python ground_control.py
```

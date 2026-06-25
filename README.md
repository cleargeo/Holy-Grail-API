# Semantic Sieve Engine v1.1

## What it is

A priority-based event routing and monitoring system for HermIt categorizes events into three- **Resonance** (silent, self-healing baseline)
- **Harmonic Shift** (strategic trends, no notification)
- **Foundation** (critical anomalies requiring your attention)

## Architecture

```
Monitored Resources -> Sieve Engine -> Tier Router -> Delivery
                                                     |
                                                     v
                                              causatio_state.json  (Foundation events only)
                                                     |
                                                     v
                                              --resolve <id> -> resolved
                                              TTL auto-resolve after 300s
```

## Commands

| Command | Description |
|---------|-------------|
| (none) | Run all checks, show Foundation alerts |
| --check-foundation | Show current Foundation alerts |
| --check-harmonic | Show harmonic shift digest |
| --report [foundation\|harmonic\|all] | Full tier report |
| --recent-foundation | Unresolved Foundation events (last 24h) |
| --resolve <event_id> | Mark as resolved |
| --event <json> | Inject manual event |
| --full | Full check across all tiers |
| --audit | Causation state audit |
| --reset-state | Reset all state files |

## Files

- ~/.hermes/scripts/semantic_sieve/sieve_engine.py (main engine)
- ~/.hermes/scripts/semantic_sieve/config.yaml (configuration)
- ~/.hermes/scripts/semantic_sieve/causation_state.json (Foundation event DB)
- ~/.hermes/scripts/semantic_sieve/sieve_state.json (health check state)
- ~/.hermes/logs/resonance.log (Tier 1 log)
- ~/.hermes/logs/foundation_critical.log (Tier 3 log)
- ~/.hermes/logs/harmonic_digest.md (Tier 2 digest)

## Monitoring Targets

- WSL memory (/proc/meminfo)
- Windows C: disk (wmic via cmd.exe)
- Network hosts (ping)
- GitHub repos (gh api, every ~2.5 hours, via cmd.exe)
- Home Assistant (disabled pending HA token)

## Resolution Policy

Foundation events auto-resolve 300s (5 min) after creation if not re-triggered.

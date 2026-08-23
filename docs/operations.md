# Operational behavior

## Normal cycle

1. The client reads local device, printer, and backup state.
2. It sends a heartbeat over an authenticated TLS channel.
3. The server updates the endpoint's current status and appends audit metadata.
4. A background check evaluates heartbeat freshness and backup age.
5. Operators use the dashboard to investigate exceptions rather than polling every device.

## Failure states

| Condition | Signal | Expected response |
|---|---|---|
| Server temporarily unavailable | Heartbeat request fails | Client retains local status and retries with bounded backoff |
| Device stops reporting | Heartbeat age exceeds policy | Server raises an offline alert and avoids duplicate notifications |
| Backup becomes stale | Recent heartbeat, old backup timestamp | Server raises a backup-specific alert |
| Printer problem | Local print check fails | Kiosk presents a support workflow behind the appropriate access boundary |
| Configuration change | Authorized action occurs | Validate, persist securely, and append an audit event |

## Validation strategy

The design calls for unit tests around threshold and deduplication rules, integration tests for heartbeat persistence and authorization, client tests for view-model state transitions, and deployment checks for TLS trust, kiosk lockdown, printer access, and restart recovery.

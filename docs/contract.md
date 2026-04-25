# Gateway ↔ PicoClaw Agent Contract

`agsale-agent-proto` is the source of truth for gRPC/protobuf contracts between:

- `agsale-backend` Gateway
- `picoclaw-agent-svc` PicoClaw wrapper

Rules:

1. Gateway owns persistence, routing, and outbound dispatch.
2. PicoClaw never sends channel messages directly.
3. Gateway calls PicoClaw through `AgentRuntimeService` only.
4. `ProcessInbound` is MVP RPC.
5. `human_only` should not require PicoClaw; `assist_only` returns suggested reply; `bot_auto_reply` returns sendable reply or escalation.

# 🚨 RespondChain

> AI-powered incident response automation with blockchain auditability

[![WeilChain](https://img.shields.io/badge/Built%20on-WeilChain-blue)](https://weilchain.com)
[![Rust](https://img.shields.io/badge/Rust-1.75+-orange)](https://www.rust-lang.org)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

## 🎯 Problem

When production breaks, companies lose **$5,600/minute** due to:
- ⏱️ Slow manual triage (15-30 min to start response)
- 🎲 Inconsistent routing (who do we page?)
- 📝 Poor audit trails (what happened during the incident?)
- 🔔 Alert fatigue (everything feels urgent)

## 💡 Solution

**RespondChain** uses AI to instantly analyze incidents, intelligently route them, and maintain an immutable on-chain audit trail.

```
Production API down → AI analyzes severity → Pages on-call engineer
                                          → Creates war room
                                          → Updates status page
                                          → Logs everything on-chain
                                          
All in under 5 seconds.
```

## ✨ Key Features

- 🤖 **AI-Driven Triage**: Natural language incident intake via Icarus
- 🌳 **Smart Routing**: Conditional branching based on severity (P0/P1/P2/P3)
- 🔗 **Multi-Service Integration**: Slack, Email, SMS, Zoom, Jira
- ⛓️ **Blockchain Audit Trail**: Immutable record of all decisions
- ⚡ **Sub-5 Second Response**: From incident report to first notification

## 🏗️ Architecture

```
┌─────────────────┐
│  Icarus (AI)    │  ← Natural language incident input
└────────┬────────┘
         │
    ┌────┴────┐
    │   MCPs  │
    └────┬────┘
         │
    ┌────┴─────────────────────┐
    │                          │
┌───▼────┐              ┌──────▼──────┐
│On-Chain│              │ Off-Chain   │
│ MCPs   │              │    MCPs     │
├────────┤              ├─────────────┤
│• Triage│              │• Slack      │
│• Route │              │• Email/SMS  │
│• Audit │              │• Zoom       │
└────────┘              │• Jira       │
                        └─────────────┘
```

### On-Chain MCPs (Smart Contracts)
- **incident_manager**: Register and track incidents
- **severity_analyzer**: Classify as P0/P1/P2/P3
- **routing_engine**: Determine who to notify
- **audit_logger**: Immutable incident log

### Off-Chain MCPs (External Integrations)
- **slack_integration**: Real-time alerts
- **communication_hub**: Email/SMS/Paging
- **collaboration_tools**: Zoom, Google Docs
- **ticketing_integration**: Jira, Linear

## 🔀 Conditional Workflows

| Severity | Actions |
|----------|---------|
| **P0** (Critical) | Page on-call → Create war room → Start Zoom → Update status page |
| **P1** (High) | Alert senior eng → Create incident doc → Escalate if unresolved |
| **P2** (Medium) | Assign to team queue → Standard notification |
| **P3** (Low) | Add to backlog → Weekly digest |

## 🚀 Quick Start

### Prerequisites
- Rust 1.75+
- WeilChain CLI
- Node.js 18+ (for off-chain MCPs)

### Deploy On-Chain MCPs

```bash
# Build
cd rust-mcps/incident_manager
cargo build --target wasm32-unknown-unknown --release

# Deploy
widl generate incident_manager.widl server rust
weilliptic deploy --file-path target/wasm32-unknown-unknown/release/incident_manager.wasm \
                  --widl-file incident_manager.widl

# Note the contract address
```

### Run Off-Chain MCPs

```bash
cd offchain-mcps/slack-integration
cargo run
```

### Register in Icarus

Add each MCP with its contract address or server URL to Icarus.

### Test It!

Type in Icarus:
```
"Production payment API is down, 5000 users affected. Handle this incident."
```

Watch RespondChain:
1. Register incident (INC-001)
2. Analyze → P0 Critical
3. Find on-call engineer
4. Page engineer via SMS
5. Create Slack war room
6. Start Zoom meeting
7. Update status page
8. Log all steps on-chain

## 📊 Demo Scenarios

### Scenario 1: Critical Outage (P0)
```
Input: "Payment API returning 500 errors, 5000 users cannot checkout"
→ Pages Alice via SMS + call
→ Creates #incident-001 Slack channel
→ Starts zoom.us/j/123456789
→ Updates statuspage.io to "Major Outage"
```

### Scenario 2: Database Issue (P1)
```
Input: "Database queries timing out, affecting 200 users"
→ Alerts senior DBA in Slack
→ Creates incident doc
→ Assigns Jira ticket
```

### Scenario 3: UI Bug (P3)
```
Input: "Button alignment issue on profile page"
→ Creates backlog ticket
→ Adds to weekly digest
```

## 💰 ROI

| Metric | Before | After | Savings |
|--------|--------|-------|---------|
| **Response Time** | 15-30 min | <5 sec | 180x faster |
| **Cost per Incident** | $20-75 | $0.50 | $19-74 saved |
| **Monthly Cost (500 incidents)** | $10K-37.5K | $250 | **$9.75K-37.25K saved** |

## 🎯 Tech Stack

- **Smart Contracts**: Rust → WebAssembly
- **Blockchain**: WeilChain
- **AI Orchestration**: Icarus
- **Off-Chain**: Rust with MCP SDK
- **APIs**: Slack, Twilio, SendGrid, Zoom

## 🏆 Competitive Advantages

| Feature | RespondChain | PagerDuty | Opsgenie |
|---------|--------------|-----------|----------|
| AI-Driven Routing | ✅ | ❌ | ❌ |
| Natural Language | ✅ | ❌ | ❌ |
| Blockchain Audit | ✅ | ❌ | ❌ |
| Open Architecture | ✅ | ❌ | ❌ |
| Setup Time | Minutes | Days | Days |

## 📈 Business Model

- **Startup**: $99/mo (100 incidents)
- **Growth**: $499/mo (1000 incidents)
- **Enterprise**: $2,499/mo (unlimited)
- **On-Premise**: Custom pricing

## 🗺️ Roadmap

- [x] Core MCPs (incident, severity, routing, audit)
- [x] Slack integration
- [x] Email/SMS notifications
- [ ] PagerDuty integration
- [ ] Machine learning for severity prediction
- [ ] Mobile app
- [ ] Multi-region deployment
- [ ] MCP marketplace

## 📚 Documentation

- [API Reference](docs/API.md)
- [Deployment Guide](docs/DEPLOYMENT.md)
- [Demo Script](docs/DEMO.md)
- [Contributing](CONTRIBUTING.md)

## 🤝 Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## 📄 License

MIT License - see [LICENSE](LICENSE) for details

## 🙏 Acknowledgments

Built on [WeilChain](https://weilchain.com) using the Model Context Protocol (MCP)

## 📞 Contact

- **Demo**: [Live Demo Link]
- **Email**: [your-email]
- **Discord**: [your-discord]
- **Twitter**: [@RespondChain]

---

**Built for the WeilChain Hackathon 2026** 🚀

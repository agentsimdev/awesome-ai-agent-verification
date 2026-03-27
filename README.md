# Awesome AI Agent Verification [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of tools, libraries, and resources for phone verification in AI agent workflows.

AI agents increasingly need phone verification to create accounts, pass 2FA, and access phone-gated services. This list catalogs every solution available — from real SIM providers to VoIP APIs to open-source libraries.

## Contents

- [Why This Matters](#why-this-matters)
- [Real SIM Providers](#real-sim-providers)
- [VoIP / Virtual Number APIs](#voip--virtual-number-apis)
- [Open Source Libraries](#open-source-libraries)
- [MCP Servers](#mcp-servers)
- [Browser Automation + Verification](#browser-automation--verification)
- [OTP / 2FA Libraries](#otp--2fa-libraries)
- [Temporary Number Services](#temporary-number-services)
- [Articles & Guides](#articles--guides)
- [Communities](#communities)
- [Related Awesome Lists](#related-awesome-lists)

## Why This Matters

Most services now detect and block VoIP numbers during phone verification:

| Service | Blocks VoIP? | Detection Method |
|---------|-------------|-----------------|
| Stripe | ✅ Yes | Carrier lookup (LERG) |
| Google | ✅ Yes | HLR query |
| WhatsApp | ✅ Yes | Carrier type check |
| Microsoft | ✅ Yes | Reputation scoring |
| Banks | ✅ Yes | Multiple methods |
| Discord | ❌ No | Basic validation |
| GitHub | ❌ No | Format only |

AI agents need real mobile numbers that pass these checks.

## Real SIM Providers

Providers that offer actual SIM-backed mobile numbers (pass carrier lookup as "mobile"):

| Provider | Pricing | MCP Support | API | Countries | Notes |
|----------|---------|-------------|-----|-----------|-------|
| [AgentSIM](https://agentsim.dev) | $0.99/session | ✅ Native | REST + SDK | US | Real T-Mobile SIM, built for AI agents, 10 free/month |
| [VoidMob](https://voidmob.com) | $19.99/mo | ❌ | REST | US, UK | Dedicated numbers, monthly subscription |
| [JoltSMS](https://joltsms.com) | $50/mo+ | ❌ | REST | US | Enterprise focused, higher volume |
| [GetSMSCode](https://getsmscode.com) | Per-use | ❌ | REST | Multiple | Physical SIM bank, variable availability |
| [5SIM](https://5sim.net) | Per-use | ❌ | REST | Multiple | Mix of real and virtual numbers |
| [SMSPool](https://www.smspool.net) | Per-use | ❌ | REST | Multiple | Marketplace model, quality varies |

## Agent Phone Platforms

Full phone infrastructure for AI agents (calls + SMS, not verification-focused):

| Provider | Pricing | Features | Verification? |
|----------|---------|----------|--------------|
| [AgentPhone](https://agentphone.to) | Free to start | Voice + SMS webhook, real-time transcription, MCP | ⚠️ Numbers likely fail carrier lookup |
| [Vapi](https://vapi.ai) | Per-minute | Voice AI agents, low latency | No verification focus |
| [Bland AI](https://bland.ai) | Per-minute | Enterprise phone agents | No verification focus |
| [Retell AI](https://retellai.com) | Per-minute | Conversational voice AI | No verification focus |

## VoIP / Virtual Number APIs

⚠️ These provide VoIP numbers that may be blocked by major services:

| Provider | Pricing | Best For | Limitation |
|----------|---------|----------|------------|
| [Twilio](https://twilio.com) | $1-5/number + usage | SMS/Voice apps | Detected as VoIP by most services |
| [Vonage](https://vonage.com) | Per-use | Enterprise comms | VoIP classification |
| [Plivo](https://plivo.com) | Per-use | Bulk messaging | VoIP classification |
| [Bandwidth](https://bandwidth.com) | Per-use | Enterprise | Some numbers pass as mobile |
| [Telnyx](https://telnyx.com) | Per-use | Developer-friendly | VoIP classification |
| [MessageBird](https://messagebird.com) | Per-use | Global coverage | Most numbers are VoIP |
| [Sinch](https://sinch.com) | Per-use | Verification APIs | VoIP classification |

## Open Source Libraries

### Phone Verification for Agents

| Repository | Stars | Language | Description |
|-----------|-------|----------|-------------|
| [transitive-bullshit/sms-number-verifier](https://github.com/transitive-bullshit/sms-number-verifier) | 215 | JavaScript | SMS verification for automated systems |
| [Shelex/free-otp-api](https://github.com/Shelex/free-otp-api) | 32 | TypeScript | Aggregates free phone numbers for OTP testing |

### OTP Servers

| Repository | Stars | Language | Description |
|-----------|-------|----------|-------------|
| [knadh/otpgateway](https://github.com/knadh/otpgateway) | 520 | Go | Standalone OTP verification with pluggable providers |
| [CuriousLearner/django-phone-verify](https://github.com/CuriousLearner/django-phone-verify) | 292 | Python | Django phone verification via SMS |
| [TheBund1st/daming](https://github.com/TheBund1st/daming) | 94 | Java | SMS verification for Spring Boot |

### Mobile OTP UI Components

| Repository | Stars | Language | Description |
|-----------|-------|----------|-------------|
| [faizalshap/react-native-otp-verify](https://github.com/faizalshap/react-native-otp-verify) | 286 | Java | React Native SMS verification |
| [kfit-dev/OTPTextField](https://github.com/kfit-dev/OTPTextField) | 67 | Obj-C | iOS OTP input field |
| [pushpalroy/ComposeOtpVerify](https://github.com/pushpalroy/ComposeOtpVerify) | 63 | Kotlin | Android Jetpack Compose OTP |

## MCP Servers

Model Context Protocol servers for phone verification in Claude, Cursor, and other MCP clients:

| Server | Provider | Tools | Description |
|--------|----------|-------|-------------|
| [AgentSIM MCP](https://github.com/Fato07/agentsim) | AgentSIM | `provision_number`, `wait_for_otp`, `release_number` | Real SIM numbers via MCP |

## Browser Automation + Verification

Tools for combining browser automation with phone verification:

| Tool | Stars | Description | Phone Support |
|------|-------|-------------|--------------|
| [browser-use](https://github.com/browser-use/browser-use) | 81K+ | AI browser automation | Needs external phone provider |
| [Notte](https://github.com/nottelabs/notte) | 1.7K | Stealth browser for agents | Built-in personas, VoIP numbers |
| [Skyvern](https://github.com/Skyvern-AI/skyvern) | 10K+ | CV+LLM browser automation | No native phone support |
| [Playwright](https://github.com/microsoft/playwright) | 68K+ | Cross-browser automation | No native phone support |
| [Puppeteer](https://github.com/puppeteer/puppeteer) | 88K+ | Chrome automation | No native phone support |

## Temporary Number Services

⚠️ Shared/public numbers — NOT suitable for production:

| Service | Type | Reliability | Notes |
|---------|------|-------------|-------|
| [Quackr](https://quackr.io) | Free shared numbers | Low | Numbers shared publicly, codes visible to all |
| [Receive-SMS-Free](https://receive-sms-free.cc) | Free shared numbers | Very Low | Frequently blocked |
| [TextNow](https://textnow.com) | Free VoIP | Low | Blocked by most major services |
| [Google Voice](https://voice.google.com) | Free VoIP | Low | Ironically blocked by Google services |

## Articles & Guides

### Technical Deep Dives

- [Why Your AI Agent's Phone Number Gets Blocked](https://dev.to/fathin_dosunmu/why-your-ai-agents-phone-number-gets-blocked-and-how-to-fix-it-48k5) - Comprehensive VoIP blocking explainer with code
- [How to Automate 2FA and Account Creation](https://dev.to/nottelabs/how-to-automate-2fa-and-account-creation-for-ai-agents-5c6p) - NotteLabs guide on agent identity
- [Building AI Agents That Handle 2FA](https://voidmob.com/blog/building-ai-agents-2fa-sms-verification) - VoidMob's SMS verification guide
- [The Agentic Browser Landscape in 2026](https://www.nohackspod.com/blog/agentic-browser-landscape-2026) - Overview of agent browser tools
- [Setting up 2FA Testing with Playwright](https://mailosaur.com/blog/automate-2fa-mfa-testing-playwright) - Testing automation guide

### Industry Reports

- [AI Agents Market: $7.6B → $10.9B in 2026](https://zealousys.com/blog/ai-agents-statistics/) - Market size and growth
- [Reddit Implements Human Verification](https://techcrunch.com/2026/03/25/reddit-bots-new-human-verification-requirements/) - Verification requirements increasing

## Communities

Where developers discuss phone verification for AI agents:

### Reddit
| Subreddit | Members | Focus |
|-----------|---------|-------|
| [r/AI_Agents](https://reddit.com/r/AI_Agents) | 325K+ | AI agent building and tooling |
| [r/mcp](https://reddit.com/r/mcp) | 75K+ | Model Context Protocol |
| [r/MCPservers](https://reddit.com/r/MCPservers) | 15K+ | MCP server discovery |
| [r/LLMDevs](https://reddit.com/r/LLMDevs) | 136K+ | LLM development |
| [r/ClaudeCode](https://reddit.com/r/ClaudeCode) | Growing | Claude Code development |
| [r/automation](https://reddit.com/r/automation) | 200K+ | General automation |

### Discord
| Server | Members | Focus |
|--------|---------|-------|
| [MCP Discord](https://discord.gg/model-context-protocol) | 11.5K+ | MCP ecosystem |
| [CrewAI](https://discord.gg/crewai) | 8K+ | Multi-agent systems |
| [n8n](https://discord.gg/n8n) | 50K+ | Workflow automation |
| [Vapi](https://discord.gg/vapi) | Growing | Voice AI agents |

### Forums
| Forum | Members | Focus |
|-------|---------|-------|
| [n8n Community](https://community.n8n.io) | 50K+ | OTP/SMS workflows |
| [CrewAI Forum](https://community.crewai.com) | 10K+ | Agent orchestration |
| [mcpservers.org](https://mcpservers.org) | Growing | MCP server discovery |

## How Carrier Lookup Works

When a phone number is submitted for verification, services query databases like LERG (Local Exchange Routing Guide) and NPAC (Number Portability Administration Center):

```json
// VoIP number (BLOCKED)
{
  "phone_number": "+16505551234",
  "carrier": "Twilio Inc.",
  "line_type": "voip",
  "mobile_country_code": "311"
}

// Real SIM number (ACCEPTED)
{
  "phone_number": "+14155551234",
  "carrier": "T-Mobile USA",
  "line_type": "mobile",
  "mobile_network_code": "026"
}
```

## Contributing

Contributions welcome! Please read the [contribution guidelines](CONTRIBUTING.md) first.

- Add new tools via Pull Request
- Keep descriptions factual and concise
- Include pricing and limitation info
- Verify links are working

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

This list is released under CC0. To the extent possible under law, the author has waived all copyright and related rights to this work.
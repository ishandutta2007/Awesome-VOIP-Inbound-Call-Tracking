# Awesome-VOIP-Inbound-Call-Tracking

# Top VoIP & Inbound Call Tracking Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Cloud Telephony, Call Attribution & Self-Hosted Voice Infrastructure*  
**Last updated: October 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **VoIP & Inbound Call Tracking**. These tools enable businesses to manage inbound and outbound voice calls, attribute calls to marketing sources, record and analyze conversations, and build programmable telephony workflows—turning voice from a black-box channel into a measurable, automatable part of the customer journey.

**Examples** include HubSpot Inbound Calling, Aircall, Talkdesk, RingCentral, CallRail, Nextiva, Dialpad, 8x8, CloudTalk, and Vonage (the category leaders).

**Open-source emphasis**: VoIP & Inbound Call Tracking is a domain where open-source tooling is **fragmented but genuinely capable at the infrastructure layer**. The strongest active project is **VoIPbin**, a production-grade, fully self-hostable CPaaS platform with modular services for call routing, AI callbots, conferencing, recording, and multi-channel messaging . **Comcent Community Edition** provides a turnkey contact center with browser dialers, queues, transcription, and AI voice bots—installable on a single Linux box with a SIP trunk . **CXMind** offers a non-invasive analytics engine that passively taps SIP/RTP traffic via HEP for real-time quality monitoring and AI agent assistance, without touching your PBX . For call detail record (CDR) analysis, **CDR-Stats** provides reporting and fraud detection, though it has been dormant for over a decade . The critical gap: **no open-source project replicates CallRail's marketing attribution**—tying a phone call back to the specific ad click or web session that drove it—which requires dynamic number insertion (DNI) and integration with ad platforms that commercial tools own.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-products)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[HubSpot Inbound Calling](https://www.hubspot.com/)**  
  Native calling within HubSpot CRM; click-to-call from contact records, automatic call logging, recording, and voicemail drop, with calls tied directly to deal and contact timelines.

- **[Aircall](https://aircall.io/)**  
  Cloud phone system built for sales and support teams; features call routing, IVR, recording, voicemail, SMS, and deep integrations with CRMs (HubSpot, Salesforce, Pipedrive) and helpdesks (Zendesk, Intercom) .

- **[Talkdesk](https://www.talkdesk.com/)**  
  Cloud contact center platform with AI-powered agent assistance, speech analytics, workforce management, and omnichannel routing; positioned for enterprise customer experience.

- **[RingCentral](https://www.ringcentral.com/)**  
  Unified communications platform with cloud PBX, video meetings, team messaging, and contact center; comprehensive but broad rather than call-tracking-specific.

- **[CallRail](https://www.callrail.com/)**  
  The leading **call tracking and analytics** platform; uses dynamic number insertion to attribute inbound calls to marketing sources (Google Ads, organic, direct mail), records calls, and provides conversation intelligence. Plans start at $50/month for the Call Tracking tier .

- **[Nextiva](https://www.nextiva.com/)**  
  Business communications platform with cloud phone, contact center, and analytics; features call recording, IVR, and CRM integrations.

- **[Dialpad](https://www.dialpad.com/)**  
  AI-powered cloud communications with voice, video, and messaging; features real-time transcription, sentiment analysis, and integration with CRM and helpdesk tools.

- **[8x8](https://www.8x8.com/)**  
  Unified communications and contact center platform for enterprises; includes voice, video, chat, and contact center analytics.

- **[CloudTalk](https://www.cloudtalk.io/)**  
  Cloud call center software with call routing, IVR, recording, and analytics; positioned for sales and support teams at mid-market pricing.

- **[Vonage](https://www.vonage.com/)**  
  Business communications platform with cloud PBX, contact center, and programmable APIs (Vonage API) for building custom voice applications.

## Open-Source GitHub Projects

### Full CPaaS & Contact Center Platforms

- **[VoIPbin](https://github.com/voipbin/monorepo)**  
  The most comprehensive open-source **CPaaS backend platform** available, explicitly positioned as "the only production-grade open-source CPaaS platform that you can fully self-host" . Monorepo architecture with modular services: **bin-call-manager** (call routing/control), **bin-flow-manager** (programmable call flows via JSON/API), **bin-ai-manager** (AI chatbot and LLM orchestration), **bin-campaign-manager** (outbound dialing), **bin-conference-manager**, **bin-queue-manager**, **bin-number-manager** (DID provisioning), and **bin-rag-manager**. Use cases include programmable IVRs, AI-powered callbots, mass outbound campaigns, and scalable conferencing. Deployable on GCP or any Kubernetes setup . **The strongest foundation for building a custom call tracking or contact center platform**—but it is a backend monorepo requiring engineering effort to deploy and operate.

- **[Comcent Community Edition](https://github.com/comcent-io/comcent-ce)**  
  Open-source **contact center** installable on a single Linux box (Ubuntu 22.04+/Debian 12+, $12/mo droplet sufficient) . Bring your own SIP trunk (Twilio, Telnyx, Bandwidth), run one install script, and get: browser-based dialers for agents, phone numbers, queues, **call recording**, **call transcription**, AI summaries, sentiment analysis, semantic search, a **real-time AI voice bot**, multi-tenant orgs, API keys, and webhooks . Requires Docker and a domain for HTTPS . **The fastest path to a working self-hosted contact center with AI features**—but it is a contact center, not a marketing call-tracking platform with attribution.

### Analytics & Monitoring (Non-Invasive)

- **[CXMind](https://github.com/Sonicwell/cxmind)**  
  Open-source **real-time VoIP analytics platform** (Business Source License 1.1, converting to Apache 2.0 in 2030) . **Non-invasive**—passively captures SIP/RTP traffic via **HEP tapping** with zero changes to your existing PBX . Components: **Ingestion Engine** (Go, processes SIP/RTP/RTCP, HEP v3), **Sniffer** (standalone capture agent), **PCAP Simulator** (traffic replay for testing), **Admin UI** (React dashboard), and **Copilot Extension** (Chrome extension for live AI agent coaching) . Benchmarked at 300+ concurrent calls on 4 cores/8GB RAM. Features **edge PCI-DSS DTMF masking** and PII sanitization . **The best open-source option for adding analytics to an existing telephony infrastructure** without replacing it.

### CDR Analysis & Reporting

- **[CDR-Stats](https://github.com/Star2Billing/cdr-stats)**  
  Open-source **Call Detail Record analysis and reporting** for FreeSWITCH, Asterisk, and other VoIP switches (Django/Python, PostgreSQL, Celery, MongoDB) . Features: browsing millions of CDRs, call rating, multi-switch and multi-tenant monitoring, **fraud detection** (unusual traffic patterns, dropped call increases, calls to disallowed countries), blacklisting, geographic alerts, and real-time reporting . **CAUTION**: last commit was over 11 years ago (dormant since ~2014) —the architecture is dated and dependencies are stale. Listed for reference but **not recommended for new deployments**.

### Telephony Infrastructure (Build Your Own)

- **[Asterisk](https://www.asterisk.org/)**  
  The foundational open-source PBX (GPL-2.0) that powers many commercial call tracking and contact center platforms . Provides call routing, recording, IVR, and CDR generation—but **no analytics, attribution, or UI**; you build the tracking layer on top . A canireplaceit.com analysis notes that Asterisk "covers most" of CallRail's functionality under GPL-2.0, but requires "real ops work" .

- **[FreeSWITCH](https://freeswitch.org/)**  
  High-capacity open-source softswitch (MPL 1.1) with built-in call recording and CDR—the engine under jambonz and most self-hosted call tracking stacks . **XML configuration is complex**, no analytics dashboard, and operating it takes real effort .

- **[OpenSIPS](https://opensips.org/)**  
  Open-source SIP router/proxy that can map campaign numbers to agents and emit call data for tracking—but it is **routing core only**: no media, no UI, just config . Best for teams building custom SIP routing logic.

### Additional Strong Open-Source Options

- **Wazo Platform** — Open-source unified communications platform with **wazo-call-logd** for generating call logs on Wazo servers . **Platform-specific**—provides call logging within the Wazo ecosystem.
- **HOMER** — 100% open-source SIP/VoIP/RTC **packet capture and monitoring** platform (sipcapture/homer) . **Monitoring-focused**—for network-level call quality analysis, not business call tracking.
- **Whitebox VoIP Plugin** — Passive observer + recorder that logs every ring/pickup/hangup, downloads recordings, transcribes via Whisper, and **assigns trackable phone numbers to web visitors** for session correlation (DNI-like behavior) . **Closest open-source pattern to CallRail's attribution**—but it is a plugin for the Whitebox platform, not a standalone product.

**Frameworks for building custom systems**: For a **full self-hosted CPaaS with programmable flows**, VoIPbin provides the most complete modular backend . For a **turnkey contact center with AI**, Comcent CE installs on a single server . For **adding analytics to an existing PBX**, CXMind's passive HEP tapping is non-invasive . For **raw telephony infrastructure**, Asterisk or FreeSWITCH provide the engine, but you must build the tracking and attribution layer. No open-source project replicates **CallRail's dynamic number insertion and ad-platform attribution** out of the box—Whitebox's plugin demonstrates the pattern but is not a standalone product.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- VoIP platforms handling call recordings and customer data must comply with applicable privacy regulations (GDPR, CCPA) and call recording consent laws (two-party consent states in the US, similar requirements elsewhere); **PCI-DSS compliance is required if calls capture payment card data**.
- **Open-source VoIP is strong at infrastructure and contact center layers**—VoIPbin provides a modular CPaaS backend , Comcent CE provides a turnkey contact center , and CXMind provides non-invasive analytics . However, **no open-source project replicates CallRail's marketing attribution** (dynamic number insertion + ad platform integration) as a standalone product, and **CDR-Stats is dormant** (last commit 11+ years ago) . Organizations requiring call tracking with attribution should evaluate commercial platforms or build custom atop Asterisk/FreeSWITCH with significant engineering effort.
- Verify license terms for commercial use; VoIPbin is open-source (check repository), Comcent CE is open-source, CXMind uses BSL 1.1 (converts to Apache 2.0 in 2030) , and Asterisk uses GPL-2.0.

---

**Made for telephony engineers, contact center operators, and developers building voice infrastructure.**  
Let's make VoIP and call tracking more open, but with clear eyes about the marketing attribution and turnkey tracking gaps that commercial platforms still fill.

# Awesome-Cloud-Data-Loss-Prevention

## Top Cloud Data Loss Prevention (DLP) Platforms Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**

*Focused on Sensitive Data Discovery, Exfiltration Prevention, Policy Enforcement & Compliance Monitoring*

**Last updated: September 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Cloud Data Loss Prevention (DLP)**. These tools help security teams discover sensitive data, prevent unauthorized exfiltration, enforce data handling policies, and maintain compliance across cloud applications, endpoints, and network traffic.



**Examples** include Microsoft Purview DLP, Netskope DLP, Symantec DLP, Forcepoint DLP, Proofpoint DLP, Google Cloud DLP, Digital Guardian, Trellix DLP, Endpoint Protector, and CoSoSys (the category leaders).



**Open-source emphasis**: Cloud DLP is one of the **most challenging categories for open-source alternatives**. No single open-source tool matches the breadth of commercial enterprise DLP platforms. Instead, open-source DLP is **compositional**—teams combine specialized tools for secrets scanning, PII detection, network monitoring, and content classification. The strongest options are **pleno-dlp** (multi-format secret/PII scanner with SARIF output), **Gitleaks/Betterleaks** (CI/CD secrets gating), **Nightfall's sensitive-data-scanner** (PII/API key discovery at rest), and **NeuVector** (Kubernetes DLP with regex rules). This section documents the full compositional landscape honestly.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents



- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[Microsoft Purview DLP](https://www.microsoft.com/en-us/security/business/microsoft-purview)**

  Integrated DLP across Microsoft 365, Windows endpoints, and cloud apps. Provides content-aware policy enforcement, adaptive protection, and insider risk management. Native integration with Teams, Exchange, SharePoint, and OneDrive.



- **[Netskope DLP](https://www.netskope.com/)**

  Cloud-native DLP with API-based inspection for SaaS apps and real-time inline enforcement for web traffic. Deep integration with the Netskope Security Cloud for CASB, SWG, and ZTNA.



- **[Symantec DLP](https://www.broadcom.com/products/cybersecurity/information-security/data-loss-prevention)**

  Enterprise DLP platform with endpoint, network, and discovery components. Provides comprehensive content inspection, exact data matching (EDM), and incident management workflows.



- **[Forcepoint DLP](https://www.forcepoint.com/)**

  Human-centric DLP with risk-adaptive protection. Monitors user behavior alongside data movement to distinguish malicious exfiltration from accidental leakage.



- **[Proofpoint DLP](https://www.proofpoint.com/)**

  Email and cloud DLP integrated with Proofpoint's threat protection platform. Focuses on preventing sensitive data loss via email, cloud apps, and insider threats.



- **[Google Cloud DLP](https://cloud.google.com/security/products/dlp)**

  Fully managed API for discovering, classifying, and redacting sensitive data (PII, PHI, financial) across GCP services. Supports data profiling, de-identification, and risk analysis at scale.



- **[Digital Guardian](https://digitalguardian.com/)**

  Data-centric DLP with endpoint, network, and discovery capabilities. Strong in intellectual property protection and regulated data compliance.



- **[Trellix DLP](https://www.trellix.com/)**

  Enterprise DLP (formerly McAfee DLP) with endpoint, network, and discovery modules. Provides content-aware policy enforcement and incident response.



- **[Endpoint Protector](https://www.endpointprotector.com/)**

  Multi-OS DLP and device control solution from CoSoSys. Provides content-aware protection for endpoints, email, web, and removable media.



## Open-Source GitHub Projects



### Multi-Format Scanners & CI/CD Gating



- **[pleno-dlp](https://github.com/plenoai/pleno-dlp)**

  **The most comprehensive open-source DLP scanner.** AGPL-3.0, Go-based. Scans filesystems, stdin, and archives (zip, tar, gzip) for 800+ secret types and PII patterns (SSN, credit cards with Luhn validation, emails, phones). Features **custom JSON rules**, **allowlisting** (by detector type, raw secret, regex, or path glob), **decode pipelines** (base64, hex, percent-encoded), and **verify URLs** for credential validation. Output formats: table, JSON, **SARIF** (GitHub Code Scanning compliant). Install via `go install` or pre-built archives with SBOMs. Ideal for CI/CD secret gating and filesystem scanning .



- **[Gitleaks](https://github.com/gitleaks/gitleaks)**

  **Industry-standard secrets scanner for repositories and CI workflows.** Now feature-complete; feature development has shifted to **Betterleaks**. Scans Git repos, files, and staged diffs using rule and regex-based detection. Supports pre-commit hooks and GitHub Actions. **MIT License** .



- **[Betterleaks](https://github.com/betterleaks/betterleaks)**

  **The next-generation secrets scanner** from Gitleaks' maintainers. Extends coverage beyond Git to GitHub/GitLab APIs, Hugging Face, S3-compatible storage, local files, and stdin. Adds **contextual filtering** and **optional active credential validation**. Designed for DevOps teams needing broader source coverage and preventive gating in CI/CD .



- **[Nightfall sensitive-data-scanner](https://github.com/nightfallai/sensitive-data-scanner)**

  Scans directories, exports, and backups for **PII and API keys** using Nightfall's DLP APIs. Discovers sensitive data at rest in data silos. Nightfall also provides **git-repo-scanner** (GitHub/GitLab repos) and SDKs (Java, Go, Node.js) for building custom DLP integrations .



### Network & Endpoint Monitoring



- **[Security Onion](https://github.com/Security-Onion-Solutions/securityonion)**

  Network security monitoring platform combining Suricata, Zeek, and Elasticsearch for intrusion detection, packet analysis, and threat hunting. **Can extract transferred files from network traffic**, providing network context for DLP investigations. **Not a content-aware DLP platform**—sensitive data classification and policy enforcement are separate functions. Community edition free; Pro license required for enterprise capabilities. Note: uses ELv2 license for some components .



- **[NeuVector](https://github.com/neuvector/neuvector)**

  Kubernetes-native container security platform with **DLP capabilities**. Can define **DLP regex rules for individual pods**, providing content-aware protection in containerized environments. Open source (SUSE) .



- **[Wazuh](https://github.com/wazuh/wazuh)**

  SIEM/XDR platform with **File Integrity Monitoring (FIM)** that can detect content changes and document **custom PAN scanning rules** for detecting unmasked payment card numbers. **Not a dedicated content-aware DLP platform**—provides telemetry and compliance monitoring alongside a separate DLP layer .



### AI-Focused & Local-First DLP



- **[privacy-firewall](https://github.com/privacyshield-ai/privacy-firewall)**

  **Local AI-powered DLP solution** with 219 stars. Designed to detect and protect sensitive data before it leaves the machine, addressing the growing risk of data leakage to AI chatbots and LLM pipelines .



- **[clawguard](https://github.com/Stanxy/clawguard)**

  DLP surveillance layer for **OpenClaw**—scans outbound content for secrets, PII, and policy violations before it leaves the machine. Covers **52 secret patterns** (AWS, GCP, Azure, GitHub, GitLab, Stripe, Slack, OpenAI, Anthropic, private keys, database URIs) and **10 PII patterns** (SSN with area code validation, credit cards with Luhn checksum, emails, phones, IPv4/IPv6). Policy engine supports **REDACT, BLOCK, MASK, HASH** actions with destination allowlists and per-destination rules .



- **[LLM Guard](https://github.com/protectai/llm-guard)**

  Open-source project for **sanitizing PII in application-integrated LLM prompts**. **Archived July 9, 2026**—no longer actively maintained. Previously used to detect and redact sensitive data before it reaches LLMs .



- **[AGI Sentinel DLP Shield](https://github.com/feras-khatib/agi-sentinel-dlp)**

  Local-first DLP engine for **AI/AGI pipelines**. Detects and redacts PII (emails, credit cards, SSN, passport), API keys (OpenAI, AWS, Google, GitHub, Slack), and AI-specific threats (prompt injection, jailbreak). Features parallel processing, bulk file support (CSV, JSON), secure JSON audit logs with zero PII storage, and Docker deployment. **AGPLv3 licensed** .



### Data Classification & Governance



- **[Apache Atlas](https://github.com/apache/atlas)**

  Data governance framework with **classification by tags** and data lineage in Hadoop/Spark ecosystems. Supports predefined types (PII, PHI, PCI) and custom Java rules. Native integration with Apache Ranger for access policy enforcement based on classifications. Ideal for organizations wanting full control over classification pipelines without cloud dependency .



- **[OpenMetadata](https://github.com/open-metadata/OpenMetadata)**

  Centralized metadata platform with **automatic classification** via configurable profilers for SQL databases, data lakes, and cloud services. **PII classification engine** detects columns containing personal data with **89% accuracy** on common types (names, emails, phones). Collaborative interface allows data stewards to validate and correct classifications via review workflows, improving detection through active learning .



### Legacy Open-Source DLP (Historical Reference)



- **[OpenDLP](https://github.com/OpenDLP/OpenDLP)**

  **Historically significant** open-source, agent-based DLP tool for discovering sensitive data at rest across thousands of systems. Deployed agents via SMB/NetBIOS and supported agentless scanning of network filesystems (Windows shares, Unix via SSH). **Abandoned since version 0.5.1 (August 2012)**—lacks modern OS, cloud, and SaaS support. Inadequate for production use but important as one of the first open-source DLP agents .



- **[MyDLP](https://github.com/MyDLP/MyDLP)**

  Open-source endpoint and network DLP platform monitoring web, email, USB, printers, and screenshots. Community Edition applied log/block rules for sensitive data. **Acquired by Comodo Group in May 2014**; open-source edition **unmaintained since early 2014**. Not suitable for modern enterprise DLP requirements .



### Additional Strong Open-Source Options



- **Secrets Scanning**: **pleno-dlp** (multi-format, SARIF), **Gitleaks** (repo-focused), **Betterleaks** (broader sources, validation), **TruffleHog** (800+ secret types, verification) .

- **Network Monitoring**: **Security Onion** (packet analysis, file extraction), **Snort** (rule-based IPS for custom DLP rules), **ModSecurity** (WAF for HTTP traffic DLP) .

- **Data Classification**: **Apache Atlas** (Hadoop/Spark lineage), **OpenMetadata** (89% PII accuracy, active learning) .

- **AI/LLM DLP**: **privacy-firewall** (local AI-powered), **clawguard** (outbound scanning with policy engine), **AGI Sentinel** (AI pipeline protection) .

- **Kubernetes DLP**: **NeuVector** (pod-level DLP regex rules) .



**Frameworks for building custom systems**: Combine **pleno-dlp** for filesystem and CI/CD scanning with SARIF output, **Gitleaks/Betterleaks** for repository secret gating, **Nightfall SDKs** for API-based PII discovery, **NeuVector** for Kubernetes DLP, and **Security Onion** for network-level visibility. Add **Apache Atlas** or **OpenMetadata** for data classification and governance. **Critical gap**: No single open-source tool provides unified policy management, endpoint agents, email/web channel enforcement, and incident workflows equivalent to commercial platforms.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Cloud DLP platforms handle sensitive data classification and prevention; ensure compliance with GDPR, CCPA, HIPAA, PCI DSS, and relevant data protection regulations.

- **Open-source reality**: **No single open-source tool provides enterprise-grade cloud DLP.** The practical approach is **compositional**—combining specialized tools for secrets scanning (**pleno-dlp**, **Gitleaks/Betterleaks**), network monitoring (**Security Onion**), data classification (**Apache Atlas**, **OpenMetadata**), and Kubernetes DLP (**NeuVector**). This requires significant integration effort and lacks unified policy management . Commercial platforms (Microsoft Purview, Netskope, Symantec, Forcepoint) remain the primary choice for organizations requiring comprehensive, content-aware DLP across all channels.

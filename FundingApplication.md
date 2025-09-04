# Omnipass Masterplan

## Executive Summary
Omnipass is a comprehensive ecosystem designed to simplify and secure cryptocurrency interactions through a phased rollout of wallet solutions and interoperability protocols. It begins with embedded light wallets for seamless user-provider interactions, progresses to cross-platform tools like browser extensions and mobile apps, and culminates in Omni ID, a universal naming service to reduce fragmentation across blockchains. The plan prioritizes user experience (UX) by minimizing friction while incorporating layered security options, such as optional secret salts and contexts for enhanced protection.

## Overall Objectives
- **Primary Goal**: Create a user-centric wallet ecosystem that bridges simple interactions with advanced security, ultimately enabling seamless cross-chain asset routing via a unified ID system.
- **Secondary Goals**:
  - Minimize UX friction for onboarding and transactions while offering optional high-security layers (e.g., secret salts and contexts only when maximum security is needed, to avoid bad UX).
  - Ensure compatibility with major blockchains (e.g., Ethereum, Bitcoin, Solana) and dApps.
  - Promote adoption through developer-friendly tools and enterprise integrations.
- **Target Audience**:
  - Retail users seeking simplicity in crypto management.
  - Developers building dApps who need easy wallet integrations.
  - Enterprises requiring secure provider integrations for blockchain-based services.

## Phased Roadmap
The plan is divided into four phases, each building on the previous. Below, each phase is detailed with its description, milestones, tasks, dependencies, timelines (adjusted from September 04, 2025), resources, risks, and success metrics. Phases incorporate features like passkey usage across multiple dApps, private key extraction for backups, and protocol-based routing for Omni ID.

### Phase One: Embedded Light Wallet
- **Description**: Embedded light wallet only usable on the relying party it was created on, delivered as an NPM package. Useful when a dApp needs to provide simple UX and onboarding. For more security, allow secret salt and contexts, but only use if you need max security—otherwise, this creates bad UX friction.
- **Milestones**:
  - Prototype ready for testing.
  - Integration with 3+ dApps.
  - Security audit completed.
  - NPM package published and documented.
- **Tasks**:
  - Design wallet architecture with passkey support.
  - Implement core features: key generation, transaction signing.
  - Package as an NPM module for easy dApp integration.
  - Test for UX friction and security.
  - Document API for dApp devs, including NPM installation instructions.
- **Dependencies**:
  - Blockchain SDKs (e.g., Web3.js for Ethereum).
  - Passkey libraries.
  - Node.js ecosystem for NPM packaging.
- **Timelines**: Q4 2025 – Q1 2026 (3-6 months).
- **Risks**:
  - Security vulnerabilities in passkey integration.
  - Low dApp adoption if UX not optimized.
  - Regulatory changes in crypto.
  - NPM registry issues or dependency conflicts.
- **Success Metrics**:
  - 80% user satisfaction in beta tests.
  - 10+ dApp integrations.
  - Zero critical security issues post-audit.
  - 1K+ NPM downloads in initial release.

### Phase Two: Browser Extension Wallet
- **Description**: Browser extension wallet: Allows for the passkey to be used on multiple dApps without the need to register and create a new light wallet for each site. If needed, you can also extract the private key from the light wallet, turning it into a normal browser extension wallet that is encrypted and stored in local storage. This allows the light wallet to serve more as a backup and a way to move to other places like the mobile app without downloading the private key itself. 
- **Milestones**:
  - Extension launch on Chrome/Firefox stores.
  - Multi-dApp compatibility tested.
  - Backup/migration features validated.
- **Tasks**:
  - Develop extension UI/UX.
  - Integrate passkey extraction and encryption.
  - Build API layer for coordination.
  - Conduct cross-browser testing.
- **Dependencies**:
  - Phase One wallet as base (including NPM package integration).
  - Browser APIs (e.g., Chrome Extension API).
  - dApp developer partnerships.
- **Timelines**: Q2 2026 – Q3 2026 (4-6 months).
- **Resources**:
  - Tools: React for UI, WebAssembly for performance.
- **Risks**:
  - Browser policy changes affecting extensions.
  - Privacy concerns with local storage.
  - Dependency on external dApp support.
- **Success Metrics**:
  - 50K+ downloads in first quarter.
  - 95% uptime for API features.
  - Positive feedback from 20+ dApp devs.

### Phase Three: Mobile App
- **Description**: Mobile app: This will be pretty much the same as the browser extension wallet. Only in this case, the app would hold the wallet and the browser.
- **Milestones**:
  - App release on iOS/Android stores.
  - Cross-device sync tested.
  - Security features for mobile verified.
- **Tasks**:
  - Port extension features to mobile (e.g., React Native).
  - Implement mobile-specific security (biometrics + passkeys).
  - Test for performance on devices.
  - Integrate in-app browser.
- **Dependencies**:
  - Phases One and Two completions.
  - Mobile SDKs (e.g., React Native, Swift/Kotlin).
  - App store approvals.
- **Timelines**: Q4 2026 – Q1 2027 (5-7 months).
- **Risks**:
  - App store rejection due to crypto policies.
  - Device fragmentation issues.
  - Higher security risks on mobile.
- **Success Metrics**:
  - 100K+ app installs.
  - 4.5+ star rating.
  - Successful sync for 90% of users.

### Phase Four: Omni ID
- **Description**: Omni ID: More of a protocol for wallet naming services, allowing users to send funds to each other based only on their username and the chain (e.g., swen@eth). If someone wanted to send him SOL tokens, they would just send it to that name, and in the background, the protocol would route the funds to a Solana wallet attached to that name. The @eth just tells the protocol where to look for a list of wallets and find the one on the same chain as the token being sent on.
- **Milestones**:
  - Protocol spec finalized.
  - Cross-chain routing live on 5+ chains.
  - Integration with existing wallets.
- **Tasks**:
  - Design protocol (smart contracts for naming/routing).
  - Build backend for lookups and routing.
  - Test cross-chain compatibility (e.g., Ethereum to Solana).
  - Launch governance for name registrations.
- **Dependencies**:
  - All prior phases.
  - Interoperability tools (e.g., Chainlink for oracles).
  - Partnerships with chains like Solana.
- **Timelines**: Q2 2027 – Q3 2027 (6-8 months).
- **Risks**:
  - Interoperability failures across chains.
  - Name squatting or disputes.
  - Scalability under high transaction loads.
- **Success Metrics**:
  - 1M+ registered names.
  - 99% successful cross-chain routes.
  - Adoption by 50+ dApps/enterprises.

## Future Features and Enhancements
Post-Phase Four, incorporate iterative improvements based on user feedback:
- **Wallet Creation if No Wallet Exists**: Automatically generate wallets during transactions if none are available for the specified chain.
- **Subwallets**: Hierarchical structures for organized asset management (e.g., swen@eth/fundrise).
- **Spam Wallet**: Dedicated wallets or filters to isolate and manage unsolicited transactions.

## Monitoring and Iteration
- **Overall Risks**: Market volatility, evolving regulations, competition from established wallets.
- **Mitigation Strategies**: Conduct regular security audits, gather user feedback via beta testing, and maintain agile development to adapt to changes.
- **Governance**: Post-Phase Four, establish a DAO for community-driven updates and feature prioritization.
- **Global Success Metrics**: Achieve 500K+ active users, 90% retention rate, and partnerships with 100+ dApps by end-2027.

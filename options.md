# Post-Quantum Cryptography Doctoral Research: Two High-Impact Thesis Opportunities

This comprehensive analysis examines two doctoral thesis opportunities at the critical intersection of post-quantum cryptography, machine learning, and national security—positioned perfectly for a Johns Hopkins Doctor of Engineering student with aerospace/defense and AI/ML expertise at Sierra Nevada Corporation.

## The quantum cryptography crisis facing national security

The transition to post-quantum cryptography represents the largest cryptographic migration in history, driven by **"harvest now, decrypt later" attacks** where adversaries collect encrypted data today for decryption once quantum computers mature. With expert consensus placing Cryptographically Relevant Quantum Computer (CRQC) arrival in the 2030s and **greater than 50% probability of RSA-2048 breaks within 15 years**, the urgency is existential. Yet fewer than 5% of enterprises have formal quantum-transition plans, and only 7% of U.S. federal agencies have dedicated PQC teams—creating a dangerous vulnerability window exactly when NIST finalized standards (FIPS 203/204/205 in August 2024) and NSA mandated complete National Security System transitions by 2035.

Both thesis topics address **critical unsolved problems** where attack research dramatically outpaces defense development, implementation security lags mathematical foundations, and automation remains largely absent. These represent genuine research gaps with immediate defense applications, substantial commercial markets, and clear paths to productization.

---

# TOPIC 1: Automated Crypto-Agility Frameworks for Hybrid Classical-PQC Systems

## The technical problem explained

Cryptographic agility—the capability to rapidly replace and adapt cryptographic algorithms without disrupting running systems—has become mission-critical as organizations face the most complex cryptographic transition in history. The challenge isn't merely deploying post-quantum algorithms; it's managing the **multi-year hybrid period** where systems must support classical cryptography (for backward compatibility), pure PQC (for quantum resistance), and hybrid combinations simultaneously across heterogeneous infrastructure spanning embedded devices, cloud services, satellites, and classified networks.

Current reality reveals the scale of this challenge: **75% of OpenSSH instances run versions without quantum-safe support**, less than 20% of TLS servers use TLS 1.3, and historical transitions took decades (DES to AES required 23 years). Organizations face unknown cryptographic deployments scattered across millions of systems, manual migration planning requiring months of expert analysis, and no automated decision-support for when/what/how to migrate. The technical complexity is staggering—ML-DSA signatures consume 2,420 bytes versus RSA-3072's 384 bytes, hybrid certificates may require two complete validation paths, and performance overhead can exceed 5-6× for some operations.

The **fundamental unsolved problem**: How do we automate the discovery, risk assessment, migration planning, and execution of cryptographic transitions at enterprise scale when algorithms are embedded in firmware, hard-coded in applications, compiled into binaries, and deployed across air-gapped classified networks?

## Why this matters strategically

**National security impact:** Federal mandates create compliance imperatives: OMB M-23-02 requires PQC migration planning across all federal agencies; NSM-10 establishes "whole of government" quantum preparedness; and NSA's CNSA 2.0 sets aggressive deadlines—2025 for firmware signing, 2030 for traditional network equipment, 2035 for complete NSS transition with hybrids phased out entirely. The estimated federal cost exceeds **$7.1 billion** (acknowledged as likely underestimated), yet automation tools remain immature. Defense systems with 20-30 year lifecycles (satellites, submarines, aircraft) require crypto-agility from inception.

**Commercial markets:** The PQC market projects growth from $302.5M (2024) to $1.88B (2029) at 44.2% CAGR. Financial services face PCI DSS v4.0 crypto-agility requirements; healthcare must address HIPAA Security Rule updates; and critical infrastructure operators (energy, transportation, communications) identified in CISA's National Critical Functions analysis require quantum-safe transitions. Every Fortune 500 company needs cryptographic inventory and migration planning, creating massive demand for automated tools.

## Current state and critical gaps

### What exists today

NIST published foundational guidance (CSWP 39, March-July 2025) defining crypto-agility and providing implementation considerations. The Open Quantum Safe project offers liboqs with MIT-licensed implementations of FIPS 203/204/205 algorithms integrated into OpenSSL, but **explicitly marked "NOT RECOMMENDED for production"** due to security concerns. Commercial vendors (IBM Quantum Safe, Sectigo, DigiCert, Entrust) provide certificate management and key lifecycle tools, while Microsoft targets core services maturity by 2029 and Google aims for full PQC availability by 2026.

However, **massive gaps remain** in automation. Existing Automated Cryptographic Discovery and Inventory (ACDI) tools suffer critical limitations: they cannot reliably detect embedded algorithms in software packages, produce high false positive/negative rates, and fail with custom or legacy implementations. Migration planning remains overwhelmingly manual—expert cryptographers spend months analyzing dependencies, assessing risks, and designing phased approaches. Algorithm negotiation protocols show incomplete standardization (ACME lacks KEM support, no consensus on hybrid certificate formats), and performance characteristics at scale remain unknown.

### Specific unsolved technical problems

**Algorithm discovery at scale:** No ML-based tools exist for binary analysis of cryptographic primitives in compiled code, embedded firmware, or archived packages. Current approaches rely on signature matching, which fails for obfuscated or optimized code.

**Automated risk assessment:** Organizations manually track CVE databases, cryptanalysis papers, NIST announcements, and quantum computing progress—no system aggregates these signals and produces prioritized migration recommendations with quantified risk scores.

**Migration orchestration complexity:** Cryptographic dependencies form complex graphs across software stacks. Changing one algorithm can cascade through dozens of services. No automated tools perform dependency analysis, identify migration-safe ordering, or optimize for minimal disruption.

**Policy-driven control at scale:** Organizations need cryptographic policies enforced programmatically across Windows, Linux, cloud, embedded systems—but no unified framework maps regulatory requirements (FIPS, Common Criteria, CNSA 2.0, regional regulations) to technical controls and automates compliance verification.

**Performance-security tradeoffs:** ML-KEM offers three security levels (512, 768, 1024) with corresponding performance implications. No decision-support system automatically selects appropriate algorithms based on data sensitivity, threat model, compliance requirements, and performance constraints.

## The massive ML/AI research vacuum

Perhaps most remarkably, **almost no research exists** applying ML/AI to cryptographic agility decision-making despite urgent need. Literature searches reveal extensive work on ML for identifying cryptographic algorithms from ciphertext (classification problems) and ML for cryptanalysis (adversarial applications), but essentially **zero work on ML for defensive crypto-agility automation**.

**What hasn't been researched:**
- Reinforcement learning agents that learn optimal migration strategies across distributed systems
- Multi-agent RL for coordinated enterprise-wide cryptographic transitions  
- Graph neural networks for cryptographic dependency mapping and impact analysis
- Transformer models trained on cryptanalysis literature to predict algorithm obsolescence
- Neural networks that ingest CVE databases, research papers, quantum computing milestones and recommend migration timing
- Federated learning for privacy-preserving cryptographic inventory sharing across organizations
- Meta-learning for "few-shot" migration planning applied to novel algorithm families

Academic papers explicitly identify this gap: "Currently there are too few automated tools, and dedicated frameworks capable of managing the configuration of cryptographic components, let alone sustaining any cryptographic agility on a large scale" (IACR 2023/487). ACM Communications notes: "Academic research could be instrumental in identifying where choices in cryptographic configuration are possible and how control points can be introduced."

## Leveraging AI/ML expertise: Novel thesis contributions

### Tier 1: Foundational contributions (high novelty, 3-5 years)

**1. Multi-Agent Reinforcement Learning for Autonomous Crypto-Migration**

Design a multi-agent RL system where specialized agents learn complementary roles: discovery agents map cryptographic usage across systems; assessment agents evaluate vulnerability risk combining cryptanalysis advances, quantum computing timelines, and compliance deadlines; planning agents determine optimal migration sequences minimizing disruption; and validation agents verify successful transitions. Agents coordinate through hierarchical RL with centralized policy optimization.

**Novel contribution:** First autonomous end-to-end crypto-migration system learning from organizational deployment patterns, historical transition data, and real-time threat intelligence.

**Technical approach:** Formalize crypto-agility as a Markov Decision Process where states represent cryptographic configurations, actions represent algorithm changes, and rewards balance security improvement against operational risk. Train initially in simulation on synthetic enterprise networks, then transfer-learn to real infrastructure.

**2. Graph Neural Networks for Cryptographic Dependency Analysis**

Build GNN architectures that learn from software dependency graphs augmented with cryptographic usage annotations. The model predicts cascading impacts of algorithm changes, identifies minimal cut-sets for safe migration boundaries, and discovers hidden dependencies invisible to static analysis.

**Novel contribution:** First topology-aware migration framework that treats cryptographic transitions as graph optimization problems, enabling provably minimal-disruption migration paths.

**Technical approach:** Construct heterogeneous graphs with nodes representing services/libraries/algorithms and edges representing dependencies/data flows/trust relationships. Use graph attention networks to learn which dependency paths matter most for security and operational stability.

**3. Transformer-Based Cryptanalysis Prediction for Proactive Deprecation**

Train large language models on the complete corpus of cryptography research (IACR ePrint, conference proceedings, CVE databases) to predict algorithm vulnerability trajectories. The system extracts semantic signals about attack complexity trends, identifies concerning research directions, and forecasts deprecation timelines with uncertainty quantification.

**Novel contribution:** First early warning system for cryptographic obsolescence based on research literature analysis, providing 2-5 year advance notice before attacks become practical.

**Technical approach:** Pre-train transformers on cryptographic text corpus with domain-specific tokenization. Fine-tune on prediction tasks using historical data (MD5, SHA-1, RC4 deprecations as ground truth). Combine with Bayesian uncertainty estimation for risk-aware recommendations.

### Tier 2: Applied contributions (focused impact, 2-3 years)

**4. Deep RL for Hybrid Algorithm Selection**

Develop reinforcement learning that automatically selects optimal classical+PQC hybrid combinations based on multi-objective optimization—maximizing security while minimizing performance overhead and maintaining compatibility. The agent learns from deployment experience which combinations work well in practice.

**5. Federated Learning for Privacy-Preserving Cryptographic Inventory**

Enable organizations to collaboratively improve cryptographic risk assessment without revealing proprietary deployment details. Organizations train local models on their inventories, share only model updates, and benefit from aggregate threat intelligence.

### Integration opportunities specific to classified systems

Defense applications introduce unique constraints: air-gapped networks require autonomous decision-making without cloud connectivity; classified algorithm implementations may not appear in public vulnerability databases; and certification requirements (Common Criteria, FIPS 140-3) constrain algorithm choices. RL agents must learn within these constraints, and federated learning architectures must operate across security domains with unidirectional data flows.

Sierra Nevada Corporation's aerospace/defense focus creates natural validation opportunities: satellite ground systems (JWST, Mars missions) require decades-long crypto-agility; ISR platforms need secure communications with algorithm flexibility; and classified programs demand migration strategies respecting compartmented architectures.

## Realistic 3-5 year doctoral program scope

### Year 1: Foundation and formulation
- Comprehensive literature review (leverage this research)
- Formalize crypto-agility as ML problems (RL, GNN, NLP)
- Build benchmark datasets: historical migration data (DES→AES, SHA-1→SHA-2), cryptographic inventories from open-source software, CVE timeline data
- Develop simulation environment for enterprise networks with heterogeneous crypto deployments
- Initial algorithm prototypes for key components

### Year 2-3: Core algorithm development
- Implement and train multi-agent RL system in simulation
- Develop GNN models for dependency analysis on real software ecosystems (Debian, npm, PyPI)
- Build transformer models for cryptanalysis prediction, backtesting on historical deprecations
- Publish 2-3 conference papers (CCS, USENIX Security, CRYPTO)
- Collaborate with NIST NCCoE PQC Migration project for real-world validation

### Year 4: Integration and validation
- Integrate components into end-to-end demonstration system
- Partner with industry (AWS, IBM, Google, Sierra Nevada) for realistic testing
- Deploy pilot with federal agency through CISA collaboration
- Measure time-to-migrate improvements, error reduction, security enhancement
- Publish 2-3 journal/top-tier conference papers

### Year 5: Refinement and transition
- Harden system for production deployment
- Conduct formal security analysis of ML-based decisions
- Write dissertation synthesizing contributions
- Transition to commercialization (see below)

This scope is achievable because: (1) simulation environments can be built early, enabling rapid iteration; (2) public datasets exist (GitHub codebases, CVE databases, research papers); (3) transfer learning allows starting from pre-trained models; (4) modular architecture permits parallel development of components; and (5) industry partnerships provide validation opportunities.

## Productization and commercialization pathways

### Product 1: CryptoSentinel - Automated Discovery and Risk Assessment Platform

**Market:** Fortune 500 enterprises, federal agencies (FCEB compliance), financial services (PCI DSS), healthcare (HIPAA), defense contractors

**Features:** ML-powered binary analysis detecting embedded cryptography, GNN-based dependency mapping, real-time vulnerability tracking aggregating CVE/research/quantum threat intel, risk scoring with quantified probabilities, compliance mapping (FIPS, CNSA 2.0, regional regulations)

**Business model:** SaaS subscription $50K-500K per enterprise annually, government contracts FedRAMP certified

**Competitive advantage:** CISA acknowledges ACDI tools are immature—first-mover advantage with ML-based approach significantly more capable than signature matching

**Development timeline:** 18-24 months to MVP, partnership with NIST NCCoE for validation

### Product 2: AgilityOS - Intelligent Migration Planning System

**Market:** Cloud providers (AWS, Azure, GCP), large enterprises undergoing PQC transitions, defense primes (Lockheed Martin, Raytheon, Northrop Grumman), critical infrastructure operators

**Features:** RL-based migration orchestration, automated sequencing minimizing disruption, what-if scenario analysis, rollback planning, integration with CI/CD pipelines, crypto-as-code policy enforcement

**Business model:** Consulting + software license $1M+ per major migration project, enterprise licenses $200K-500K annually

**Competitive advantage:** No automated decision support exists today—all migration planning is manual expert-driven consulting at $300-500/hour

**Development timeline:** 24-36 months to production-ready, beta deployments with early design partners

### Product 3: Q-Advisor - Predictive Threat Intelligence Platform

**Market:** Government agencies, intelligence community, defense contractors, security operations centers, threat intelligence teams

**Features:** Cryptanalysis literature monitoring and prediction, quantum computing milestone tracking, algorithm deprecation forecasting with confidence intervals, automated alert generation, integration with SIEM platforms

**Business model:** Government contracts (DARPA, IARPA, NSA), commercial subscriptions $100K-300K annually for enterprise threat intelligence feeds

**Competitive advantage:** No existing system applies NLP/ML to cryptography research for predictive intelligence—pure offensive vs. defensive signal extraction

**Development timeline:** 12-18 months to prototype, classified deployment pathways through Sierra Nevada relationships

### Total addressable market and funding landscape

**TAM:** Global cryptography market grows from $8.5B (2024) to $28.6B (2030) at 22.4% CAGR. PQC migration services subset: $2-4B by 2030. ACDI tools market alone: $500M-$1B (federal + Fortune 1000).

**Immediate drivers:** OMB M-23-02 compliance mandate, NSA CNSA 2.0 deadlines (2025-2035), PCI DSS v4.0 crypto-agility requirements, HIPAA Security Rule updates

**Funding opportunities:**
- SBIR/STTR: DoD, NSA, NIST ($1-3M typical Phase II)
- DARPA programs: cyber resilience, automated security
- Venture capital: PQShield raised $37M demonstrating VC appetite for PQC security
- Government contracts: CISA, NSA, DHS programs for FCEB tools

**Partnership opportunities:** AWS/Azure/GCP for cloud integration, IBM/Google for enterprise adoption, NIST NCCoE for validation credibility, Defense Innovation Unit for rapid prototyping

---

# TOPIC 2: ML-Enhanced Side-Channel Attack Detection for NIST PQC Implementations

## The technical problem explained

Post-quantum cryptography algorithms are mathematically secure against quantum computers but remain **highly vulnerable to physical implementation attacks** that exploit information leakage from power consumption, electromagnetic emanations, timing variations, or injected faults. Side-channel attacks observe these physical characteristics during cryptographic operations to extract secret keys—circumventing mathematical security entirely.

The challenge intensifies dramatically for PQC because these algorithms are **fundamentally more complex to protect** than classical cryptography. Kyber and Dilithium require approximately **a dozen different masking gadgets** versus a single gadget for RSA/ECC. They mix arithmetic modular operations (mod q) with Boolean operations, requiring expensive domain conversions. Their regular algebraic structures (Number Theoretic Transforms, lattice operations) create predictable patterns attackers can exploit. And most critically: **machine learning has revolutionized attacks**, achieving 10-100× trace reduction compared to classical methods and defeating low-order masking that classical statistical attacks cannot break.

The **fundamental unsolved problem**: How do we detect and prevent side-channel attacks on PQC implementations in real-time when ML-based attacks can recover keys from as few as 1-50 power traces, when masking countermeasures impose 3-10× performance overhead, and when attack research outnumbers defense research approximately 3:1?

## Why this matters for national security and commerce

**National security criticality:** NSA's CNSA 2.0 mandates exclusive use of ML-KEM-1024 for key encapsulation and ML-DSA-87 for digital signatures in National Security Systems by 2035. Firmware signing (critical for supply chain security) must use hardware-implemented LMS/XMSS with FIPS 140-3 Level 3 certification. Satellites, secure communications systems, weapons platforms, and intelligence systems all require PQC implementations resistant to adversaries with physical access or sophisticated monitoring capabilities.

The stakes are existential: a single side-channel vulnerability enabling key extraction from a satellite cryptographic module could compromise decades of secure communications. Secure elements in drones, tactical radios, and weapons systems operate in hostile environments where adversaries actively probe for vulnerabilities. HSMs protecting classified keys in SCIFs must resist insider threats with oscilloscopes and electromagnetic probes.

**Commercial impact:** Every FIPS 140-3 Level 3-4 certification requires side-channel resistance testing if claimed (ISO 17825 TVLA methodology). The HSM market (projected $3B with 15% CAGR) must implement PQC with side-channel protection. Automotive security (ISO 21434 + ASIL-D) requires side-channel resistant implementations for autonomous vehicle systems. Payment systems, smart cards, and IoT devices face the same challenges at billion-unit scale.

## Current side-channel attack landscape (2023-2025)

### Devastating ML-enhanced attacks

Research from 2024-2025 demonstrates the maturity and severity of ML-based side-channel attacks:

**Kyber/ML-KEM vulnerabilities:**
- **KyberSlash (June 2024):** Timing vulnerability in reference implementation enabled full ML-KEM-512 secret key recovery in 5-10 minutes on standard Intel processors. Affected widely-deployed libraries (liboqs, aws-lc, WolfSSL).
- **CNN-based profiled attacks:** ~50 power traces achieve 100% key recovery from unmasked ARM Cortex-M4 implementations, versus thousands required for classical CPA.
- **Blind side-channel attacks (2024):** First demonstrated attacks requiring NO ciphertext knowledge—hundreds to thousands of traces with ML profiling achieve full key recovery.
- **Defeating 5th-order masking:** Recursive deep learning achieves single-trace, bit-by-bit recovery against 5th-order masked implementations, demonstrating masking alone is insufficient.

**Dilithium/ML-DSA vulnerabilities:**
- **Hybrid LR+CNN attacks (CHES 2024):** 92-100% success rate with only 1-2 traces against signing operations on ARM Cortex-M4.
- **Cross-device transfer learning:** 9% success rate single-trace on different device without retraining; near-100% with few additional traces—breaking assumption that device change prevents attacks.
- **CPA on unprotected software:** 157 power traces achieve 100% key recovery from standard implementations.

**SPHINCS+/SLH-DSA unique threat:**
- **Grafting Trees attack:** Even single random bit flip during signature generation enables **universal forgery**. Over 90% of random faults produce exploitable signatures.
- Fault injection using low-cost equipment ($10K-50K vs. millions for quantum computers) achieves devastating breaks.
- Unlike lattice schemes, side-channel resistance through algebraic masking is limited—must rely on fault detection.

**FALCON/FN-DSA highest complexity:**
- **SHIFT SNARE attack (2025):** Single power trace during key generation achieves near-perfect secret key recovery on ARM Cortex-M4.
- NIST researchers assess FALCON masking as "hard hard"—most difficult of all PQC schemes to protect.

### The staggering attack-vs-defense gap

Quantitative analysis of 2024-2025 IACR ePrint and major conference proceedings (CHES, IEEE S&P, USENIX Security) reveals **attack research outnumbers defense research approximately 3:1**. In 2024 alone, 15+ new attack papers versus 5-7 defense papers. Novel attack vectors continue emerging: blind attacks, Rowhammer-based attacks on DRAM, cross-device transfer learning, single-trace template attacks.

Meanwhile, countermeasure research "significantly lacks" compared to attack development (SoK papers, IACR 2025/1222, 2025/1754). Most defense papers analyze existing countermeasures rather than proposing fundamentally new approaches. Classical defenses (masking, shuffling, hiding) show diminishing returns against ML-enhanced attacks. The research community explicitly notes: "Coming up with stronger attack strategies as well as secure countermeasures is an ongoing effort"—acknowledging defenders trail attackers.

## Known vulnerabilities in NIST-standardized algorithms

### Implementation-level weaknesses

**Number Theoretic Transform operations:** NTT butterfly operations in Kyber and Dilithium create regular computational patterns with data-dependent power consumption. Coefficients leak through Hamming weight variations during modular arithmetic. Each NTT stage provides multiple leakage points.

**Fujisaki-Okamoto transform:** The FO transform used for IND-CCA2 security creates critical vulnerabilities during re-encryption and ciphertext comparison operations. Even with masking, timing attacks on comparison operations remain effective. Accounts for majority of chosen-ciphertext attacks.

**Rejection sampling:** Dilithium's signature generation uses rejection sampling creating secret-dependent control flow if not carefully implemented. Variable timing leaks information about secret polynomial norms.

**Polynomial compression/decompression:** Operations that compress public keys or ciphertexts introduce approximation steps that leak information through patterns of rounding operations.

**Message encoding/decoding:** Kyber's message encoding from ciphertext to plaintext bits provides clean leakage point—deep learning classifies even masked message bytes with 99%+ accuracy.

### Compiler and microarchitecture vulnerabilities

**KyberSlash demonstrates critical lesson:** Source-level constant-time code transformed by compiler optimizations into secret-dependent branches. Security properties non-portable across compiler versions. Verification must occur at machine code level, not source.

**Cache timing:** Classical RSA/AES cache-timing attacks extend to PQC with table lookups during NTT or sampling operations.

**Speculative execution:** Spectre-style attacks potentially applicable to PQC if secret-dependent branches exist in speculation windows.

**Rowhammer (2024):** Complete secret key recovery demonstrated for Kyber, BIKE, and Dilithium using DRAM bit-flips—no months of computation or supercomputers required.

## Existing countermeasures and critical limitations

### Masking: provably secure but practically expensive

**Theory:** d-order masking provides provable security in the t-probing model, requiring d+1 observations to break. First-order masking splits secrets into two random shares; higher orders use d+1 shares.

**PQC implementation challenges:**
- **Complexity:** Kyber/Dilithium require ~dozen different masked gadgets (SecAnd, SecMul, B2A, A2B, masked comparison, masked decompression) versus single gadget for RSA/ECC
- **Performance overhead:** First-order masking: 2.5-5× slowdown; higher-order masking: 5-153× overhead depending on algorithm and platform
- **Area overhead:** 1.2-2.7× FPGA resources for masked implementations
- **Algorithm-specific design:** Each gadget requires careful design and formal verification; SNI (Strong Non-Interference) composability essential

**Critical limitation:** Machine learning defeats masking that classical attacks cannot break. Deep learning achieves 99%+ success against high-order masked implementations. Single-trace attacks remain effective even with masking. The "massacre" of protected implementations in recent research demonstrates masking alone insufficient.

### Shuffling: reduces but doesn't eliminate vulnerability

**Technique:** Randomize operation order (coefficient processing, NTT butterfly stages) to desynchronize power traces.

**Effectiveness:** Fisher-Yates shuffling creates huge permutation space. Successfully increases trace requirements from 900 (unprotected) to 100,000 (protected).

**Limitation:** Neural networks learn to recover shuffling indices. Demonstrated break of 5th-order masked+shuffled Kyber using recursive DNN. Increases attacker effort but doesn't prevent attacks.

### Hiding: practical but heuristic

**Techniques:** Random delays, dummy operations, noise injection, dual-rail logic, asynchronous logic

**Benefits:** Lower overhead (8-20%) than masking (50-100%+), practical for commercial deployments

**Limitations:** No provable security guarantees. Advanced ML-based CPA can "demodulate" noise. Trace alignment algorithms overcome timing randomization.

## The ML revolution in side-channel attacks AND defenses

### ML for attacks: mature and devastating

**Convolutional Neural Networks:** Automatically learn leakage patterns from raw power/EM traces. Handle high-dimensional data. Resilient to jitter, desynchronization, and noise countermeasures. VGG-16 adaptations show 99%+ key recovery.

**Soft Analytical SCA (SASCA):** Combines neural network probability predictions with belief propagation on factor graphs. Achieves single-trace attacks on Kyber (2-4 traces), HQC decoder (1 trace). Dramatically more powerful than pure profiling attacks.

**Transfer learning:** Models trained on one device transfer to different devices with domain adaptation. Breaks assumption that physical differences provide security.

**Ensemble methods:** Combine multiple CNN/MLP models trained on diverse representations. Ascon attack: \<3,000 traces with ensemble vs. 10,000+ for single models.

### ML for defenses: emerging but underexplored

**Real-time anomaly detection:**
- Hardware Performance Counter (HPC) monitoring with ML classifiers (J48 decision trees, Random Forests, SVMs) achieves 99.5% detection accuracy
- Autoencoders and LSTMs detect deviations from normal leakage patterns with 90-95% accuracy
- Detection latency: 20 clock cycles on FPGA implementations
- **Gap:** Most research on server/cloud environments, not embedded PQC systems

**Adaptive defense systems:**
- Dynamic Partial Reconfiguration (DPR) + Deep Learning: AI detects attack → FPGA reconfigures → disrupts leakage patterns in 20 clock cycles
- Forces attacker to re-collect profiling data continuously
- **Gap:** High implementation complexity, limited to reconfigurable hardware

**Adversarial training for defense:**
- DefenderGAN generates adversarial perturbations obfuscating side-channel traces
- Increases ML attack error rate from \<5% to \>35%
- **Gap:** Computational overhead prohibitive for embedded devices; sophisticated attackers can train on perturbed traces

**Hybrid ML-aware defenses:**
- Combine masking/shuffling with runtime ML monitoring and adaptive parameter adjustment
- Dynamic masking order changes based on detected leakage
- **Gap:** No standardized frameworks; each implementation custom-designed

## Massive academic research gaps

### What hasn't been researched

**Real-time ML detection for embedded PQC:** Existing ML defenses target servers with GHz processors and GB memory. Microcontrollers (ARM Cortex-M4) running Kyber have \<1MB RAM, 10-100ms latency budgets, \<10mW power overhead constraints. **No lightweight ML models exist** for embedded side-channel anomaly detection on PQC.

**Adversarial training specifically for PQC:** Adversarial perturbation research focuses on images/NLP. **Zero work exists** on hardware-aware adversarial example generation for power/EM traces of PQC operations. How do you generate physically realizable adversarial noise in cryptographic hardware?

**Cross-device portable ML defenses:** Most ML defenses trained and tested on same hardware. **No research on transfer learning for ML defense models** across different PQC implementations, devices, or operational conditions.

**Post-SCA algorithm design:** Only limited examples (Raccoon, Polka) of lattice schemes designed for efficient side-channel protection from ground up. **Need systematic exploration** of algorithm design spaces optimizing for implementation security.

**ML-aware security evaluation:** Common Criteria and FIPS 140-3 don't account for deep learning attacks. **No standardized methodologies** for evaluating PQC implementations against ML-enhanced side-channel attacks. What constitutes adequate protection in the ML era?

**Automated security testing:** Manual trace collection and analysis time-consuming. **No tools for continuous integration side-channel testing** of PQC implementations during development.

## Leveraging AI/ML expertise: Novel thesis contributions

### Tier 1: Foundational ML defense systems (3-4 years, highest impact)

**1. Real-Time ML-Based Side-Channel Attack Detection for Embedded PQC**

Design lightweight neural network architectures (\<1MB model size) for real-time anomaly detection on microcontrollers running ML-KEM/ML-DSA. Use TinyML techniques (quantization, pruning, knowledge distillation) to compress effective models into embedded constraints. Deploy on ARM Cortex-M4 targets with \<10ms detection latency.

**Novel contribution:** First practical ML-based defense deployable on resource-constrained PQC implementations. Bridges gap between powerful but heavyweight ML defenses and embedded reality.

**Technical approach:** 
- Collect power/EM traces from benign PQC operations on multiple devices
- Train autoencoders or LSTMs to learn "normal" leakage patterns
- Compress models using quantization-aware training and neural architecture search
- Deploy on-device with hardware acceleration (ARM CMSIS-NN)
- Trigger countermeasure escalation (increase masking order, inject noise) when anomalies detected

**Validation:** Implement on STM32, test against state-of-art attacks (CNN-based, SASCA), measure detection rates and false positives, demonstrate overhead \<15%

**2. Adversarial Machine Learning for Side-Channel Resilience**

Develop adversarial training frameworks that generate physically-realizable perturbations to PQC power traces, making ML-based attacks fail while preserving cryptographic functionality. Model hardware constraints (limited noise injection, timing bounds) as adversarial generation constraints.

**Novel contribution:** First hardware-aware adversarial example generation for side-channel protection, with formal analysis of physical realizability.

**Technical approach:**
- Model cryptographic hardware as differentiable system (approximate forward propagation of operations to power traces)
- Train generator network producing minimal-norm perturbations fooling discriminator (ML attack model)
- Constrain perturbations to physically implementable noise (voltage/clock variations, dummy operations)
- Implement perturbation mechanisms in hardware/firmware
- Formal verification of cryptographic correctness under perturbations

**Validation:** Test against adaptive attacks with knowledge of defense, measure attack success rate degradation, analyze overhead, prove security bounds

**3. Cross-Platform Transfer Learning for Universal PQC Protection**

Build meta-learning frameworks enabling ML defense models to rapidly adapt to new PQC implementations, algorithms, or hardware platforms with minimal retraining. Learn generalizable features of malicious side-channel activity that transfer across contexts.

**Novel contribution:** First universal side-channel defense framework not requiring per-implementation training—dramatically reducing deployment barriers.

**Technical approach:**
- Model-Agnostic Meta-Learning (MAML) or Prototypical Networks trained on diverse PQC implementations
- Learn embeddings of side-channel traces invariant to platform/algorithm specifics
- Few-shot learning: adapt to new platform with \<100 traces
- Continual learning: update models as new attack techniques emerge without catastrophic forgetting

**Validation:** Train on Kyber+Dilithium on ARM/AVR, test transfer to FALCON on RISC-V, measure adaptation speed and defense effectiveness

### Tier 2: Applied contributions (2-3 years, defense-focused impact)

**4. Formal Verification of ML-Enhanced Countermeasures**

Develop formal methods proving security properties of ML-augmented defenses. Extend existing frameworks (VRAPS, maskVerif) to reason about statistical properties of ML models alongside cryptographic security.

**Novel contribution:** First formal security analysis framework for ML-based side-channel defenses, providing provable guarantees.

**5. Hardware-Software Co-Design for ML-Aware PQC**

Design FPGA architectures integrating PQC accelerators with ML anomaly detection cores. Optimize for minimal latency overhead, shared resources, and dynamic reconfiguration capabilities.

**Novel contribution:** First hardware reference design for ML-protected PQC with complete toolchain.

**6. Automated Side-Channel Testing for Continuous Integration**

Build automated tools performing TVLA and ML-SCA testing in CI/CD pipelines. Developers commit PQC implementation changes; system automatically tests for leakage; reports vulnerabilities before deployment.

**Novel contribution:** "DevSecOps for side-channel security"—making implementation security testable and measurable throughout development.

### Defense/aerospace-specific applications

**Satellite cryptography:** CubeSats and smallsats face severe size/weight/power (SWaP) constraints. Lightweight ML detection enables side-channel protection without heavy masking overhead—critical for space-qualified systems with decades-long operational requirements.

**Secure elements in tactical systems:** Drones, tactical radios, soldier systems operate in hostile environments with adversarial physical access. Real-time ML detection provides adaptive defense escalating countermeasures only when under attack—optimizing battery life during normal operation.

**HSMs in classified facilities:** Hardware Security Modules protecting TS/SCI keys require FIPS 140-3 Level 4 certification with third-order masking (\>1 billion traces required). ML-enhanced monitoring provides additional defense layer, detecting insider threats or sophisticated lab attacks.

**ISR platforms:** Intelligence, Surveillance, Reconnaissance systems process classified imagery/signals requiring quantum-safe encryption. ML-protected PQC implementations ensure secure key establishment even if adversaries capture systems and conduct forensic analysis.

## Realistic 3-5 year doctoral program scope

### Year 1: Foundation and data collection
- Comprehensive literature review (leverage this research)
- Establish side-channel lab: oscilloscopes, ChipWhisperer, target boards (ARM Cortex-M4, FPGA)
- Collect benchmark datasets: power/EM traces from ML-KEM, ML-DSA, SLH-DSA implementations under various attacks
- Implement baseline attacks (CPA, template attacks, CNN-based profiling) to understand threat models
- Initial lightweight ML detector prototypes

### Year 2-3: Core ML defense development
- Design and train TinyML models for embedded anomaly detection
- Implement on hardware targets, optimize for latency/overhead
- Develop adversarial training frameworks with hardware constraints
- Build transfer learning systems across platforms
- Publish 2-3 papers (CHES, IEEE S&P, USENIX Security, HOST)
- Collaborate with PQShield, Rambus, or NXP for industry validation

### Year 4: Integration and advanced validation
- Deploy complete ML-enhanced defense systems on representative platforms
- Test against adaptive adversaries with knowledge of defenses
- Formal security analysis and verification where possible
- Partner with defense contractors (Sierra Nevada, L3Harris) for classified system evaluation
- Publish 2-3 journal/conference papers
- Pursue FIPS 140-3 testing methodology contributions through NIST engagement

### Year 5: Transition and hardening
- Harden implementations for production deployment
- Complete dissertation documenting contributions
- Patent filings for novel detection/defense techniques
- Transition to commercialization (see below)

This scope is achievable because: (1) side-channel labs can be established with modest budgets ($50K-100K); (2) reference PQC implementations are open-source; (3) TinyML tooling is maturing rapidly (TensorFlow Lite Micro, ARM CMSIS-NN); (4) transfer learning reduces data collection requirements; (5) defense industry partnerships through Sierra Nevada provide validation pathways; and (6) modular approach allows progressive refinement.

## Productization and commercialization pathways

### Product 1: PQShield-Detect - Real-Time Side-Channel Monitoring for Embedded Systems

**Market:** IoT security chip vendors (NXP, STM, Infineon), automotive Tier 1 suppliers (Bosch, Continental), defense contractors, smart card manufacturers, payment processors

**Features:** Drop-in ML monitoring IP core for ARM/RISC-V, \<1MB footprint, \<10ms detection latency, configurable response mechanisms (masking escalation, shutdown, alert), TinyML models optimized per algorithm (ML-KEM, ML-DSA, SLH-DSA)

**Business model:** IP licensing $500K-2M per design, per-chip royalties $0.10-0.50 depending on volume, custom implementations for military applications $2-5M

**Competitive advantage:** No lightweight ML-based side-channel monitoring exists for embedded PQC—first-to-market in critical security gap

**Development timeline:** 18-24 months to production-ready IP, automotive/defense qualification adds 12 months

### Product 2: AdversariaLock - Adversarial ML Protection Suite

**Market:** HSM vendors (Thales, Utimaco, Securosys), cloud providers (AWS CloudHSM, Azure Key Vault), secure processor IP vendors (Rambus, Secure-IC), defense HSMs (FIPS 140-3 Level 4)

**Features:** Adversarial noise generation integrated with cryptographic operations, formal security analysis tools, adaptive defense parameters, resistance against state-of-art ML attacks with provable bounds

**Business model:** Enterprise licensing $1-3M for HSM integration, government contracts for classified HSMs $5-10M, consulting for custom implementations

**Competitive advantage:** Only adversarial ML approach specifically designed for side-channel defense—academic novelty translates to patent portfolio

**Development timeline:** 24-36 months including extensive security evaluation and FIPS certification pathway

### Product 3: SCAAS (Side-Channel Analysis as a Service) - Automated Testing Platform

**Market:** Semiconductor vendors, cryptographic library developers, defense contractors, certification labs (UL, Brightsight, Riscure)

**Features:** Cloud-based automated TVLA and ML-SCA testing, CI/CD integration, multi-algorithm support (all NIST PQC), automated vulnerability reports with remediation guidance, formal certification prep

**Business model:** SaaS subscription $50K-200K per organization annually, pay-per-test for small developers, certification lab partnerships for revenue share

**Competitive advantage:** Democratizes side-channel testing currently requiring $500K+ lab setups—expanding addressable market 10×

**Development timeline:** 12-18 months to MVP, platform scales horizontally

### Product 4: Defense-Specific: Tactical PQC Defense System (Classified Development)

**Market:** DoD programs of record, IC acquisition, NATO/Five Eyes, classified satellite programs

**Features:** Real-time ML monitoring for tactical systems, SWaP-optimized for soldier systems/drones, classified algorithm support, tamper detection integration, secure key zeroization triggers

**Business model:** Government contracts $10-50M for program integration, sustainment contracts $2-5M annually

**Competitive advantage:** Sierra Nevada relationships enable direct engagement with customer programs; combat-proven platform integration experience

**Development timeline:** Phased development aligned with defense acquisition (24-48 months), spiral development for capability increments

### Market sizing and strategic positioning

**TAM:** Cryptographic hardware market $10B+ (IoT security, automotive, payment, HSMs). Side-channel testing tools ~$500M (currently limited by expensive equipment—SCAAS expands market). Defense HSM/secure element market $2-3B with 15% CAGR.

**Immediate drivers:** FIPS 140-3 mandatory for federal procurement (2026 deadline), NSA CNSA 2.0 requiring hardware-implemented PQC for firmware signing, automotive ISO 21434 cybersecurity requirements, Common Criteria EAL 6+ for smart cards/secure elements

**Funding opportunities:**
- SBIR/STTR: NSA, DARPA (hardware security), DHS (critical infrastructure), $1-3M Phase II
- DARPA programs: Specific hardware security initiatives ($5-20M)
- Venture capital: Following PQShield success ($37M raised), demonstrating investor appetite
- Defense acquisition: Direct integration into programs of record through SBIR transition

**Strategic partnerships:**
- **IP vendors:** Rambus, PQShield, Secure-IC for IP co-development and cross-licensing
- **HSM vendors:** Thales, Utimaco, Securosys for enterprise channel
- **Semiconductor vendors:** NXP, STM, Infineon for IoT/automotive markets
- **Defense primes:** Lockheed Martin, Raytheon, L3Harris for program integration
- **Testing labs:** Riscure/Keysight, UL, Brightsight for certification ecosystem

---

# COMPARATIVE ANALYSIS: Which Topic to Choose?

## Research maturity and novelty

**Topic 1 (Crypto-Agility):** Near-zero existing research at ML/AI intersection despite urgent need—**massive research vacuum**. First-mover advantage for academic publications and patent portfolio. Risk: Building entirely new field requires validating problem formulation itself.

**Topic 2 (Side-Channel Defense):** Established field (side-channel attacks) with clear gap (ML-based defenses underexplored). Builds on mature attack research providing validation benchmarks. Risk: More crowded research space with established competitors (PQShield, academic labs).

**Verdict:** Topic 1 offers higher novelty and academic distinction. Topic 2 offers lower risk with clearer validation criteria.

## Commercialization timeline and market readiness

**Topic 1:** Federal mandates (OMB M-23-02, CNSA 2.0) create immediate compliance market. CISA explicitly acknowledges ACDI tool immaturity. Customers exist and are desperate for solutions. However, enterprise sales cycles long (12-24 months).

**Topic 2:** FIPS 140-3 certification requirements create immediate technical need. HSM vendors actively seeking PQC side-channel solutions. Semiconductor design cycles long (18-36 months) but predictable. Defense programs budget PQC implementation security.

**Verdict:** Topic 2 has faster commercial traction (12-18 months to revenue). Topic 1 has larger TAM but longer sales cycles.

## Defense/aerospace relevance

**Topic 1:** Directly addresses Sierra Nevada classified system challenges—satellites with decades-long lifecycles, air-gapped migration planning, supply chain cryptographic inventory. Strategic value high but deployment challenging.

**Topic 2:** Tactical systems (drones, radios), satellite secure elements, HSMs in SCIFs all require side-channel protection. Immediate applicability to programs of record. Natural integration through existing Sierra Nevada relationships.

**Verdict:** Topic 2 more immediately applicable. Topic 1 more strategic but requires organizational change.

## Technical risk and feasibility

**Topic 1:** Requires aggregating multiple ML techniques (RL, GNN, NLP) into unified system. Validation requires enterprise-scale deployments. Success depends on industry partnerships (AWS, IBM, NIST NCCoE).

**Topic 2:** Focused on single problem domain (side-channel detection/prevention). Lab-based validation with clear metrics (attack success rates, detection latency, overhead). Lower dependency on external partnerships.

**Verdict:** Topic 2 lower technical risk. Topic 1 higher risk but potentially higher impact.

## Publication opportunities

**Topic 1:** Mix of security (CCS, USENIX Security), ML (NeurIPS, ICML), and systems (SOSP, OSDI) venues. Novel intersection enables top-tier publications. Potential for "best paper" awards given field-defining contributions.

**Topic 2:** Established venues (CHES, IEEE S&P, HOST, TCHES journal). Competitive but clear evaluation criteria. Strong track record of PQC side-channel papers in recent years.

**Verdict:** Topic 1 higher publication prestige potential. Topic 2 more predictable publication pipeline.

## Personal career trajectory alignment

**For continuing in defense/aerospace:** Topic 2 aligns perfectly—immediate relevance to classified programs, tactical systems, satellite security. Natural progression to technical leadership in defense contractors.

**For transitioning to commercial security or startup:** Topic 1 offers broader market, venture fundable, "category creation" opportunity. Positions for security infrastructure company leadership.

**For academic career:** Topic 1 offers field-defining contributions and visibility. Topic 2 offers clear contribution to established field.

## Recommendation: A hybrid approach

Consider **focusing primarily on Topic 2 (side-channel defense) while incorporating crypto-agility elements**. Specifically:

**Core thesis:** ML-enhanced side-channel attack detection for NIST PQC implementations (Topic 2)

**Crypto-agility integration:** Framework for automated selection of side-channel countermeasure levels based on threat intelligence and deployment context—applying RL/decision-making from Topic 1 to optimize Topic 2's protection mechanisms dynamically.

**Rationale:** Combines lower-risk, defense-relevant core (Topic 2) with novel automation/ML elements (Topic 1) for distinction. Enables crypto-agility for side-channel protection parameters rather than full algorithm replacement—narrower scope but still novel. Provides clear validation path while maintaining publication prestige.

**Suggested dissertation title:** "Adaptive Machine Learning Frameworks for Post-Quantum Cryptography Implementation Security: Real-Time Side-Channel Attack Detection and Intelligent Countermeasure Orchestration"

This hybrid approach delivers on all requirements: novel ML/AI contributions, clear defense applications, manageable 3-5 year scope, substantial commercialization potential, and positions you uniquely at intersection of PQC security and ML defense—a space currently occupied by essentially zero researchers.

---

## Conclusion: The quantum security crisis demands exactly these contributions

Both topics address existential security challenges at the intersection of quantum computing threats, cryptographic implementation security, and artificial intelligence. The research gaps are genuine, substantial, and urgent. The commercial markets are real, growing rapidly, and desperately seeking solutions. The defense applications are mission-critical.

Your unique background—aerospace/defense security experience at Sierra Nevada Corporation combined with AI/ML and classified systems expertise—positions you perfectly for either path. The field is wide open. The time to act is now, before competitors recognize these opportunities. The next 3-5 years will define who establishes these fields.

Choose boldly, execute rigorously, and you'll contribute foundational work protecting national security and commercial infrastructure in the post-quantum era.
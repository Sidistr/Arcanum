<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Arcanum — Whitepaper</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Space+Mono:wght@400;700&family=Lora:ital,wght@0,400;0,600;1,400&display=swap');

  :root {
    --black: #0A0A0F;
    --ink: #13131A;
    --surface: #16161F;
    --border: #252535;
    --muted: #3A3A55;
    --subtle: #6B6B90;
    --body: #B0B0CC;
    --light: #E0E0F0;
    --white: #F4F4FF;
    --accent: #7B61FF;
    --accent-dim: #3D2FA0;
    --accent-glow: rgba(123,97,255,0.15);
    --green: #00E5A0;
    --green-dim: rgba(0,229,160,0.1);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--black);
    color: var(--body);
    font-family: 'Space Grotesk', sans-serif;
    font-size: 17px;
    line-height: 1.75;
    -webkit-font-smoothing: antialiased;
  }

  /* NAVIGATION */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    background: rgba(10,10,15,0.85);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border);
    padding: 0 48px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .nav-logo {
    font-family: 'Space Mono', monospace;
    font-size: 13px;
    color: var(--accent);
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }

  .nav-links {
    display: flex;
    gap: 32px;
    list-style: none;
  }

  .nav-links a {
    font-size: 13px;
    color: var(--subtle);
    text-decoration: none;
    letter-spacing: 0.04em;
    transition: color 0.2s;
  }

  .nav-links a:hover { color: var(--white); }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 120px 48px 80px;
    max-width: 1100px;
    margin: 0 auto;
    position: relative;
  }

  .hero-eyebrow {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 32px;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .hero-eyebrow::before {
    content: '';
    display: block;
    width: 32px;
    height: 1px;
    background: var(--accent);
  }

  .hero h1 {
    font-family: 'Lora', serif;
    font-size: clamp(40px, 6vw, 76px);
    font-weight: 600;
    line-height: 1.1;
    color: var(--white);
    letter-spacing: -0.02em;
    margin-bottom: 12px;
  }

  .hero h1 em {
    font-style: italic;
    color: var(--accent);
  }

  .hero-subtitle {
    font-family: 'Lora', serif;
    font-size: clamp(18px, 2.5vw, 26px);
    font-weight: 400;
    font-style: italic;
    color: var(--subtle);
    margin-bottom: 48px;
    line-height: 1.4;
  }

  .hero-abstract {
    max-width: 680px;
    font-size: 18px;
    line-height: 1.8;
    color: var(--body);
    margin-bottom: 56px;
    border-left: 2px solid var(--accent-dim);
    padding-left: 24px;
  }

  .hero-meta {
    display: flex;
    gap: 40px;
    flex-wrap: wrap;
  }

  .meta-item {
    display: flex;
    flex-direction: column;
    gap: 4px;
  }

  .meta-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .meta-value {
    font-size: 14px;
    color: var(--light);
  }

  /* SECTION */
  .section {
    max-width: 1100px;
    margin: 0 auto;
    padding: 100px 48px;
    border-top: 1px solid var(--border);
  }

  .section-header {
    display: flex;
    align-items: baseline;
    gap: 20px;
    margin-bottom: 56px;
  }

  .section-num {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.1em;
    padding-top: 4px;
  }

  .section h2 {
    font-family: 'Lora', serif;
    font-size: clamp(28px, 4vw, 44px);
    font-weight: 600;
    color: var(--white);
    letter-spacing: -0.01em;
    line-height: 1.2;
  }

  .prose {
    max-width: 720px;
    color: var(--body);
    font-size: 17px;
    line-height: 1.85;
  }

  .prose p { margin-bottom: 24px; }
  .prose p:last-child { margin-bottom: 0; }

  .prose strong {
    color: var(--light);
    font-weight: 600;
  }

  /* HIGHLIGHT BOX */
  .highlight {
    background: var(--accent-glow);
    border: 1px solid var(--accent-dim);
    border-radius: 12px;
    padding: 28px 32px;
    margin: 40px 0;
    max-width: 720px;
  }

  .highlight p {
    font-family: 'Lora', serif;
    font-size: 19px;
    font-style: italic;
    color: var(--light);
    line-height: 1.7;
    margin: 0;
  }

  /* CODE BLOCK */
  .code-block {
    background: var(--ink);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 28px 32px;
    margin: 32px 0;
    max-width: 720px;
    overflow-x: auto;
  }

  .code-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 16px;
  }

  .code-block pre {
    font-family: 'Space Mono', monospace;
    font-size: 13px;
    line-height: 1.7;
    color: var(--body);
    white-space: pre-wrap;
  }

  .code-block .kw { color: var(--accent); }
  .code-block .fn { color: var(--green); }
  .code-block .cm { color: var(--muted); font-style: italic; }
  .code-block .str { color: #FFB347; }

  /* GRID */
  .grid-2 {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 24px;
    margin-top: 40px;
    max-width: 960px;
  }

  .card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 28px;
    transition: border-color 0.2s;
  }

  .card:hover { border-color: var(--accent-dim); }

  .card-icon {
    font-size: 24px;
    margin-bottom: 16px;
  }

  .card h3 {
    font-size: 16px;
    font-weight: 600;
    color: var(--light);
    margin-bottom: 10px;
  }

  .card p {
    font-size: 14px;
    color: var(--subtle);
    line-height: 1.7;
  }

  /* THREAT TABLE */
  .threat-table {
    width: 100%;
    max-width: 720px;
    border-collapse: collapse;
    margin-top: 32px;
    font-size: 14px;
  }

  .threat-table th {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--subtle);
    text-align: left;
    padding: 12px 16px;
    border-bottom: 1px solid var(--border);
  }

  .threat-table td {
    padding: 14px 16px;
    border-bottom: 1px solid var(--border);
    color: var(--body);
    vertical-align: top;
  }

  .threat-table tr:last-child td { border-bottom: none; }

  .badge {
    display: inline-block;
    padding: 3px 10px;
    border-radius: 20px;
    font-size: 11px;
    font-weight: 600;
    font-family: 'Space Mono', monospace;
  }

  .badge-green { background: var(--green-dim); color: var(--green); }
  .badge-red { background: rgba(255,80,80,0.12); color: #FF8080; }
  .badge-yellow { background: rgba(255,180,50,0.12); color: #FFB832; }

  /* ROADMAP */
  .roadmap {
    max-width: 720px;
    margin-top: 40px;
    position: relative;
  }

  .roadmap::before {
    content: '';
    position: absolute;
    left: 20px;
    top: 24px;
    bottom: 24px;
    width: 1px;
    background: var(--border);
  }

  .roadmap-item {
    display: flex;
    gap: 28px;
    margin-bottom: 40px;
    position: relative;
  }

  .roadmap-dot {
    flex-shrink: 0;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: var(--surface);
    border: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    position: relative;
    z-index: 1;
  }

  .roadmap-dot.active {
    background: var(--accent-glow);
    border-color: var(--accent);
  }

  .roadmap-content { padding-top: 8px; }

  .roadmap-phase {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 6px;
  }

  .roadmap-content h3 {
    font-size: 17px;
    font-weight: 600;
    color: var(--light);
    margin-bottom: 8px;
  }

  .roadmap-content p {
    font-size: 14px;
    color: var(--subtle);
    line-height: 1.7;
  }

  /* CONCLUSION */
  .conclusion {
    background: var(--surface);
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    padding: 100px 48px;
    text-align: center;
  }

  .conclusion-inner {
    max-width: 680px;
    margin: 0 auto;
  }

  .conclusion h2 {
    font-family: 'Lora', serif;
    font-size: clamp(28px, 4vw, 48px);
    font-weight: 600;
    color: var(--white);
    line-height: 1.2;
    margin-bottom: 24px;
  }

  .conclusion p {
    font-size: 17px;
    color: var(--body);
    line-height: 1.8;
    margin-bottom: 16px;
  }

  /* FOOTER */
  footer {
    max-width: 1100px;
    margin: 0 auto;
    padding: 48px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 16px;
  }

  footer p {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.08em;
  }

  /* GLOW EFFECT */
  .glow-orb {
    position: fixed;
    width: 600px;
    height: 600px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(123,97,255,0.06) 0%, transparent 70%);
    pointer-events: none;
    top: -200px;
    right: -200px;
    z-index: 0;
  }

  @media (max-width: 700px) {
    nav { padding: 0 20px; }
    .nav-links { display: none; }
    .hero, .section { padding-left: 24px; padding-right: 24px; }
    .conclusion { padding: 64px 24px; }
    footer { padding: 32px 24px; }
  }
</style>
</head>
<body>

<div class="glow-orb"></div>

<nav>
  <div class="nav-logo">Arcanum — Whitepaper v0.2</div>
  <ul class="nav-links">
    <li><a href="#problem">Problem</a></li>
    <li><a href="#solution">Solution</a></li>
    <li><a href="#architecture">Architecture</a></li>
    <li><a href="#threats">Threats</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-eyebrow">Whitepaper · Version 0.2 · Draft</div>
  <h1>Code that <em>cannot</em><br>be seen.</h1>
  <p class="hero-subtitle">A programming language where privacy is not a feature — it is the foundation.</p>
  <p class="hero-abstract">
    Today, every line of source code that runs in the world exists, at some point, as readable plaintext. 
    This is the original sin of software security. <strong>Arcanum</strong> is a compiler layer proposal where source code privacy is treated as a first principle — combining Trusted Execution Environments (TEE) for immediate, practical protection with Zero-Knowledge proofs as the long-term cryptographic foundation. Developers write in the language they already know. Arcanum handles the rest. Plaintext source never exists post-compilation. Not on the server. Not in memory. Not anywhere a hacker, a competitor, or a state actor could find it.
  </p>
  <div class="hero-meta">
    <div class="meta-item">
      <span class="meta-label">Author</span>
      <span class="meta-value">Mert Atakan</span>
    </div>
    <div class="meta-item">
      <span class="meta-label">Status</span>
      <span class="meta-value">Conceptual Draft</span>
    </div>
    <div class="meta-item">
      <span class="meta-label">Version</span>
      <span class="meta-value">0.1 — Pre-MVP</span>
    </div>
    <div class="meta-item">
      <span class="meta-label">Year</span>
      <span class="meta-value">2026</span>
    </div>
    <div class="meta-item">
      <span class="meta-label">Category</span>
      <span class="meta-value">TEE + ZK / Compiler Security</span>
    </div>
  </div>
</section>

<!-- PROBLEM -->
<section class="section" id="problem">
  <div class="section-header">
    <span class="section-num">01</span>
    <h2>The Problem</h2>
  </div>
  <div class="prose">
    <p>
      Software today has a fundamental and largely ignored vulnerability: <strong>source code is readable.</strong> 
      Even when compiled into machine instructions, determined attackers with enough access — whether through a breach, an insider threat, or supply-chain compromise — can eventually reconstruct what a program does and how it works.
    </p>
    <p>
      Existing countermeasures treat this as a problem of access control: firewalls, encryption at rest, obfuscation techniques. But these are all variations of the same idea — hide the key, not the lock. If the key is found, or the right person is bribed, the code is exposed.
    </p>

    <div class="highlight">
      <p>"The most secure secret is one that cannot be read — not one that is merely difficult to find."</p>
    </div>

    <p>
      The consequences are tangible: billions of dollars lost to code theft, competitive advantage eroded by reverse engineering, critical infrastructure made vulnerable by the assumption that compiled binaries are "safe." The world does not need better locks. It needs a different kind of vault.
    </p>
    <p>
      Zero-Knowledge Proofs — mathematical constructs that allow one party to prove knowledge of a secret without revealing the secret itself — suggest a radical alternative. What if the same principle could be applied not just to data, but to <strong>code itself</strong>?
    </p>
  </div>
</section>

<!-- SOLUTION -->
<section class="section" id="solution">
  <div class="section-header">
    <span class="section-num">02</span>
    <h2>The Solution</h2>
  </div>
  <div class="prose">
    <p>
      <strong>Arcanum</strong> is not a new programming language. It is a <strong>privacy-first compiler layer</strong> that sits on top of languages developers already use — C++, Rust, JavaScript, TypeScript, Go, and any other language supported by LLVM or RISC-V toolchains. Developers write code in the language they know. Arcanum transforms it.
    </p>
    <p>
      The single, radical design constraint is this: <strong>source code must never exist as readable plaintext after the compilation step.</strong> Arcanum achieves this through a two-phase approach — practical protection today, with a path to stronger mathematical guarantees tomorrow.
    </p>
    <p>
      <strong>Phase 1 — TEE (Trusted Execution Environment):</strong> In the near term, Arcanum wraps compiled code inside hardware-enforced secure enclaves (Intel SGX, AMD SEV, ARM TrustZone). The code enters the enclave encrypted, executes inside it, and only the output leaves. Not even the server owner, the cloud provider, or an attacker with root access can read the source logic. This is how the world's most security-conscious companies already protect their most sensitive algorithms — Arcanum makes it automatic and developer-transparent.
    </p>
    <p>
      <strong>Phase 2 — ZK (Zero-Knowledge Proofs):</strong> As ZK compiler infrastructure matures, Arcanum will transition to transforming source code into zero-knowledge arithmetic circuits — a mathematical representation that is provably unreadable without the original source, requires no trusted hardware, and adds post-quantum resistance. The long-term vision is a system where source code privacy is guaranteed by mathematics alone, not by trust in any hardware manufacturer.
    </p>

    <div class="code-block">
      <div class="code-label">How Arcanum Works — Conceptual Flow</div>
      <pre><span class="cm">// Step 1: Developer writes in any supported language (e.g. Rust)</span>
<span class="kw">fn</span> <span class="fn">transfer_funds</span>(sender: &amp;Account, receiver: &amp;Account, amount: u64) {
    assert!(sender.balance >= amount);
    sender.balance -= amount;
    receiver.balance += amount;
}

<span class="cm">// Step 2: Arcanum compiler layer — developer runs one command
// $ arcanum compile transfer.rs --output transfer.enc
//
// Phase 1 output: TEE-wrapped encrypted binary
// → Executes inside a hardware secure enclave
// → Source logic unreadable even to server owner
// → No TEE or ZK knowledge required from the developer
//
// Phase 2 output (future): ZK arithmetic circuit
// → Mathematically unreadable without original source
// → No trusted hardware required
// → Post-quantum resistant</span></pre>
    </div>

    <p>
      This is not obfuscation. Obfuscation makes code hard to read; a determined reverse engineer can still decode it. TEE enclaves enforce hardware-level isolation that cannot be bypassed through software. And ZK circuits are mathematically impossible to reverse without the original source — no amount of compute changes that.
    </p>
    <p>
      In both phases, the developer experience is identical: write code as usual, run one command, ship a protected binary. The complexity is entirely Arcanum's responsibility.
    </p>
  </div>
</section>

<!-- ARCHITECTURE -->
<section class="section" id="architecture">
  <div class="section-header">
    <span class="section-num">03</span>
    <h2>Technical Architecture</h2>
  </div>
  <div class="prose">
    <p>
      Arcanum's architecture is designed in two phases — a practical near-term implementation using proven hardware security, and a long-term cryptographic foundation using zero-knowledge proofs. Both phases share the same developer-facing interface: one compile command, complete source code privacy.
    </p>
  </div>

  <div class="grid-2">
    <div class="card">
      <div class="card-icon">⚙️</div>
      <h3>Layer 1 — The Compiler Layer</h3>
      <p>Accepts source code in any supported language (C++, Rust, JavaScript, TypeScript, Go, and others via LLVM or RISC-V toolchains). In Phase 1, produces a TEE-wrapped encrypted binary. In Phase 2, produces a STARK-compatible arithmetic circuit. The compilation step is the only moment source code exists in plaintext.</p>
    </div>
    <div class="card">
      <div class="card-icon">🛡️</div>
      <h3>Layer 2A — TEE Enclave (Phase 1)</h3>
      <p>The compiled binary executes inside a hardware-enforced secure enclave (Intel SGX, AMD SEV, or ARM TrustZone). The source logic is invisible to the operating system, the server owner, and any external attacker. Performance overhead is minimal — near-native execution speed. Trust is placed in the hardware manufacturer, not in any software layer.</p>
    </div>
    <div class="card">
      <div class="card-icon">🔐</div>
      <h3>Layer 2B — ZK Proof System (Phase 2)</h3>
      <p>Generates zero-knowledge proofs (STARK-based) for each execution. No trusted hardware required. Proofs are compact, fast to verify, and reveal nothing about internal program state. Post-quantum resistant by design. This phase eliminates the hardware trust assumption entirely — privacy is guaranteed by mathematics alone.</p>
    </div>
    <div class="card">
      <div class="card-icon">✅</div>
      <h3>Layer 3 — The Verifier</h3>
      <p>A lightweight verification layer that any third party can use to confirm that a program ran correctly — without accessing the source logic. In Phase 1, verification is attestation-based (TEE remote attestation). In Phase 2, verification is cryptographic proof-based. The public-facing result is identical: execution confirmed, logic remains private.</p>
    </div>
  </div>

  <div class="prose" style="margin-top: 48px;">
    <p>
      <strong>Why TEE first?</strong> Trusted Execution Environments are battle-tested, widely deployed (AWS Nitro, Azure Confidential Computing, Google Confidential VMs), and impose near-zero performance penalty. They provide immediate, real-world protection for proprietary source code today — while the ZK compiler infrastructure needed for Phase 2 continues to mature across the research community.
    </p>
    <p>
      <strong>Why ZK eventually?</strong> TEE places trust in hardware manufacturers. If Intel or AMD has a vulnerability — or is compelled by a government — the enclave can theoretically be compromised. ZK circuits have no such dependency: their privacy guarantee is mathematical, not institutional. Phase 2 is not a replacement for Phase 1 — it is an upgrade path that removes the final trust assumption.
    </p>
  </div>
</section>

<!-- THREAT MODEL -->
<section class="section" id="threats">
  <div class="section-header">
    <span class="section-num">04</span>
    <h2>Honest Threat Model</h2>
  </div>
  <div class="prose">
    <p>
      No system is unconditionally secure. The value of Arcanum is not the claim of absolute protection — it is a significant, measurable reduction in the attack surface for source code theft and reverse engineering. The following table reflects an honest assessment of where the system succeeds and where residual risks remain.
    </p>
  </div>

  <table class="threat-table">
    <thead>
      <tr>
        <th>Threat</th>
        <th>Status</th>
        <th>Notes</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Source code theft via network breach</td>
        <td><span class="badge badge-green">MITIGATED</span></td>
        <td>Plaintext source never transmitted or stored post-compile. Both TEE and ZK phases enforce this.</td>
      </tr>
      <tr>
        <td>Reverse engineering of compiled output</td>
        <td><span class="badge badge-green">MITIGATED</span></td>
        <td>Phase 1: TEE enclave prevents access to decrypted logic at runtime. Phase 2: ZK circuits carry no recoverable linguistic information.</td>
      </tr>
      <tr>
        <td>Hardware manufacturer compromise (TEE)</td>
        <td><span class="badge badge-yellow">PHASE 1 ONLY</span></td>
        <td>Phase 1 trusts Intel/AMD/ARM. A hardware-level vulnerability or government compulsion could theoretically expose enclave contents. Phase 2 eliminates this dependency entirely.</td>
      </tr>
      <tr>
        <td>Insider threat (developer leaks source)</td>
        <td><span class="badge badge-red">UNMITIGATED</span></td>
        <td>Social and organizational controls required. Out of scope for the compiler layer in both phases.</td>
      </tr>
      <tr>
        <td>Compiler-level vulnerabilities</td>
        <td><span class="badge badge-yellow">PARTIAL</span></td>
        <td>A bug in the compiler could expose intermediate representations. Formal verification of the compiler is a long-term priority.</td>
      </tr>
      <tr>
        <td>Side-channel attacks</td>
        <td><span class="badge badge-yellow">PARTIAL</span></td>
        <td>Phase 1: TEE hardware provides some side-channel mitigations. Phase 2: ZK circuits do not inherently protect against timing or power analysis at the hardware level.</td>
      </tr>
      <tr>
        <td>Quantum computing attacks</td>
        <td><span class="badge badge-green">MITIGATED (Phase 2)</span></td>
        <td>Phase 1: TEE is not affected by quantum attacks on cryptography. Phase 2: STARK-based systems are post-quantum resistant by design.</td>
      </tr>
    </tbody>
  </table>
</section>

<!-- LANDSCAPE -->
<section class="section" id="landscape">
  <div class="section-header">
    <span class="section-num">05</span>
    <h2>Existing Landscape</h2>
  </div>
  <div class="prose">
    <p>
      Several mature efforts exist at the intersection of zero-knowledge cryptography and compiler design. Arcanum builds on the same infrastructure as these projects — but addresses a fundamentally different problem.
    </p>
    <p>
      <strong>zkLLVM</strong> by NilFoundation is an LLVM-based circuit compiler that supports C++, Rust, JavaScript, and TypeScript. It transforms existing code into ZK circuits efficiently. However, its primary goal is <em>verifiable computation</em> — proving that a program ran correctly — not source code privacy. The developer's source remains readable; the circuit is a proof of execution, not a replacement for the code.
    </p>
    <p>
      <strong>RISC Zero</strong> is a zkVM that generates ZK proofs for Rust and C++ programs compiled to RISC-V. Like zkLLVM, it targets execution verifiability. The source code is never hidden — it is simply executed inside a provable environment.
    </p>
    <p>
      <strong>SP1</strong> by Succinct follows the same pattern: standard Rust code, verifiable execution, no source code privacy guarantee.
    </p>
    <p>
      <strong>Circom</strong> requires developers to write directly in circuit language — it is a tool for ZK experts, not a transparent layer for mainstream developers.
    </p>

    <div class="highlight">
      <p>The distinction is precise: existing tools ask <em>"can we prove this code ran correctly?"</em> Arcanum asks <em>"can we make this code permanently unreadable — while still provably executable?"</em> These are different questions with different architectures, different threat models, and different target users.</p>
    </div>

    <p>
      Arcanum uses the same underlying compiler infrastructure as zkLLVM and RISC Zero — LLVM and RISC-V toolchains — but reorients the design goal entirely around <strong>source code privacy as a first principle</strong>. The developer experience is also different: no ZK background required, no circuit writing, no annotations beyond a standard compile command.
    </p>
    <p>
      No production-ready tool with this specific design constraint currently exists. This is a genuine and addressable gap, at the intersection of growing enterprise demand for intellectual property protection and maturing ZK compiler infrastructure.
    </p>
  </div>
</section>

<!-- ROADMAP -->
<section class="section" id="roadmap">
  <div class="section-header">
    <span class="section-num">06</span>
    <h2>Roadmap</h2>
  </div>

  <div class="roadmap">
    <div class="roadmap-item">
      <div class="roadmap-dot active">01</div>
      <div class="roadmap-content">
        <div class="roadmap-phase">Current — Phase 0</div>
        <h3>Conceptual Foundation</h3>
        <p>Defining the core architecture, threat model, and two-phase roadmap. Publishing this whitepaper to initiate community feedback and identify technical collaborators with TEE and/or ZK compiler experience.</p>
      </div>
    </div>
    <div class="roadmap-item">
      <div class="roadmap-dot">02</div>
      <div class="roadmap-content">
        <div class="roadmap-phase">Phase 1 — TEE MVP</div>
        <h3>TEE-Based Compiler Layer</h3>
        <p>A working Arcanum compiler layer that wraps Rust or C++ programs inside TEE enclaves (targeting Intel SGX / AWS Nitro). Target: one end-to-end working example — developer writes code, runs one command, receives a TEE-protected binary. Source logic unreadable at runtime even with root access.</p>
      </div>
    </div>
    <div class="roadmap-item">
      <div class="roadmap-dot">03</div>
      <div class="roadmap-content">
        <div class="roadmap-phase">Phase 2 — Multi-Language & Tooling</div>
        <h3>Language Expansion & Developer Experience</h3>
        <p>Extend TEE compiler support to the full range of LLVM and RISC-V compatible languages. IDE integrations, debugging tools, and documentation targeting developers with no TEE background. First enterprise pilots.</p>
      </div>
    </div>
    <div class="roadmap-item">
      <div class="roadmap-dot">04</div>
      <div class="roadmap-content">
        <div class="roadmap-phase">Phase 3 — ZK Transition</div>
        <h3>Zero-Knowledge Compiler Layer</h3>
        <p>Introduce the ZK compiler backend alongside the TEE layer. Developers can opt into ZK output for use cases requiring mathematical privacy guarantees without hardware trust. STARK-based, post-quantum resistant. Collaboration with ZK researchers to validate cryptographic security claims.</p>
      </div>
    </div>
    <div class="roadmap-item">
      <div class="roadmap-dot">05</div>
      <div class="roadmap-content">
        <div class="roadmap-phase">Phase 4 — Audited Release</div>
        <h3>Independent Security Audit & Public Beta</h3>
        <p>Independent audit of both the TEE and ZK compiler layers. Public beta targeting financial applications, proprietary algorithms, and critical infrastructure. Full post-quantum migration path documented.</p>
      </div>
    </div>
  </div>
</section>

<!-- CONCLUSION -->
<section class="conclusion">
  <div class="conclusion-inner">
    <h2>Code has always been readable.<br>It doesn't have to be.</h2>
    <p>
      The history of cryptography is the history of humanity learning to communicate secrets across hostile environments. Arcanum applies that same principle to software itself — not as a patch, not as a layer, but as the language layer.
    </p>
    <p>
      This whitepaper is a beginning. The architecture is intentionally open for critique, collaboration, and revision. The goal is not to have all the answers, but to ask the right question clearly: <strong>what would software look like if source code privacy were treated as a first principle?</strong>
    </p>
    <p style="margin-top: 32px; color: var(--subtle); font-size: 15px;">
      Feedback, contributions, and technical collaboration are welcome. This document will be updated as the design matures.
    </p>
  </div>
</section>

<footer style="border-top:1px solid #252535;">
  <div style="max-width:1100px;margin:0 auto;padding:48px;display:flex;flex-direction:column;gap:24px;">
    <div style="display:flex;justify-content:space-between;flex-wrap:wrap;gap:32px;align-items:flex-start;">
      <div>
        <p style="font-family:'Space Mono',monospace;font-size:10px;color:#6B6B90;letter-spacing:0.15em;text-transform:uppercase;margin-bottom:10px;">Authorship</p>
        <p style="font-family:'Space Grotesk',sans-serif;font-size:14px;color:#B0B0CC;margin-bottom:4px;">Idea &amp; Vision: <span style="color:#E0E0F0;font-weight:600;">Mert Atakan</span></p>
        <p style="font-family:'Space Grotesk',sans-serif;font-size:14px;color:#B0B0CC;">Compiled &amp; Written by: <span style="color:#7B61FF;font-weight:600;">Claude</span> <span style="color:#6B6B90;">(Anthropic)</span></p>
      </div>
      <div>
        <p style="font-family:'Space Mono',monospace;font-size:10px;color:#6B6B90;letter-spacing:0.15em;text-transform:uppercase;margin-bottom:10px;">Special Thanks</p>
        <p style="font-family:'Space Grotesk',sans-serif;font-size:14px;color:#B0B0CC;margin-bottom:4px;">Atakan and Erdem Families</p>
        <p style="font-family:'Space Grotesk',sans-serif;font-size:14px;color:#B0B0CC;">Cem Buldanlıoğlu</p>
      </div>
      <div>
        <p style="font-family:'Space Mono',monospace;font-size:10px;color:#6B6B90;letter-spacing:0.15em;text-transform:uppercase;margin-bottom:10px;">Publication</p>
        <p style="font-family:'Space Grotesk',sans-serif;font-size:14px;color:#B0B0CC;">arXiv · GitHub · ethresear.ch</p>
      </div>
    </div>
    <div style="border-top:1px solid #252535;padding-top:20px;">
      <p style="font-family:'Space Mono',monospace;font-size:11px;color:#3A3A55;letter-spacing:0.08em;">Arcanum · Whitepaper v0.2 · 2026 · Draft — All rights reserved</p>
    </div>
  </div>
</footer>

</body>
</html>

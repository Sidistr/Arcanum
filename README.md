# Arcanum

> *What if your source code could never be stolen — not because it's hidden, but because it mathematically cannot be read?*

Arcanum is a zero-knowledge compiler layer for languages developers already use. Write code in **C++, Rust, JavaScript, TypeScript, Go** — or any LLVM / RISC-V compatible language. Arcanum transforms it into a zero-knowledge arithmetic circuit at compile time. Plaintext source never exists post-compilation.

---

## The Problem

Every line of source code that runs in the world exists, at some point, as readable plaintext. Firewalls, obfuscation, and encryption at rest are all variations of the same idea: hide the key, not the lock. If the key is found, the code is exposed.

Arcanum explores a different question: **what would software look like if source code privacy were treated as a first principle?**

---

## How It Works

Arcanum sits between your code and your compiler. You write in the language you already know. Arcanum does the rest.

```bash
# Your existing Rust code — unchanged
fn transfer_funds(sender: &Account, receiver: &Account, amount: u64) {
    assert!(sender.balance >= amount);
    sender.balance -= amount;
    receiver.balance += amount;
}

# Compile with Arcanum
$ arcanum compile transfer.rs --output transfer.zkc

# Output: transfer.zkc (zero-knowledge circuit)
# → Mathematically unreadable without original source
# → Fully executable and verifiable by any third party
# → No ZK knowledge required from the developer
```

- ✅ Code is **verifiable** — anyone can confirm it ran correctly
- ✅ Code is **executable** — it produces real outputs
- ❌ Code is **not readable** — the logic remains permanently private

---

## Architecture

| Layer | Role |
|---|---|
| **Compiler Layer** | Accepts C++, Rust, JS, TS, Go (via LLVM / RISC-V) and transforms source into STARK-compatible arithmetic circuits |
| **Proof System** | Generates zero-knowledge proofs (STARK-based) for each execution — post-quantum resistant, no trusted setup required |
| **Verifier** | Lightweight third-party verification layer — confirms correct execution without accessing internal logic |

---

## How Arcanum Differs from Existing Tools

| | zkLLVM / RISC Zero / SP1 | Arcanum |
|---|---|---|
| Primary goal | Verifiable execution | Source code privacy |
| Source code readable? | ✅ Yes | ❌ Never |
| Target users | Blockchain / ZK developers | Any software team |
| ZK knowledge required | Yes | No |
| Use case | Proving computation | Protecting intellectual property |

Existing tools ask: *"Can we prove this code ran correctly?"*
Arcanum asks: *"Can we make this code permanently unreadable — while still provably executable?"*

---

## Status

This is a **conceptual whitepaper project** at pre-MVP stage. The architecture is open for critique, collaboration, and revision.


---

## Roadmap

| Phase | Goal |
|---|---|
| **0 — Current** | Conceptual foundation, whitepaper, community feedback |
| **1** | Proof of concept compiler layer: Rust/C++ → STARK circuit, end-to-end |
| **2** | Multi-language support, formal specification, ZK researcher collaboration |
| **3** | Developer tooling, IDE integrations, documentation |
| **4** | Independent cryptographic audit, public beta |

---

## Contributing & Feedback

This project is in its earliest stage. Feedback from ZK researchers, compiler engineers, and cryptographers is especially welcome.

📬 mertatakan53@gmail.com

---

## Author

**Idea & Vision:** Mert Atakan
**Whitepaper:** Compiled & written with Claude (Anthropic)

*Special thanks to the Atakan and Erdem families, and Cem Buldanlıoğlu.*

---

## License

MIT License — open for collaboration and adaptation.

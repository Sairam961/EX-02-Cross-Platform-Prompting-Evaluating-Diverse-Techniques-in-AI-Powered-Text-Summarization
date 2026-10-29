# EX-02-Cross-Platform-Prompting-Evaluating-Diverse-Techniques-in-AI-Powered-Text-Summarization

## AIM
To evaluate and compare the effectiveness of prompting techniques (zero-shot, few-shot, chain-of-thought, role-based) across different AI platforms (e.g., ChatGPT, Gemini, Claude, Copilot) in a specific task: text summarization.

## Scenario:
You are part of a content curation team for an educational platform that delivers quick summaries of research papers to undergraduate students. Your task is to summarize a 500-word technical article on "The Basics of Blockchain Technology" using multiple AI platforms and prompting strategies.

Your goal is to determine which combination of prompting technique + platform provides the best summary in terms of:

Accuracy

Coherence

Simplicity

Speed

User experience

## Algorithm
1. **Text Selection:** Obtain a 500-word technical article on "The Basics of Blockchain Technology" to serve as the standard input data.
2. **Goal Definition:** Identify the target audience (undergraduate students) and the specific requirements (simple, accurate, quick summary).
3. **Prompt Design:** Construct a progressive series of prompts, upgrading step-by-step from a "Basic Prompt" up to a highly detailed "Output Format Prompt".
4. **Execution:** Input the identical source text and the progressive prompts into the AI model.
5. **Evaluation:** Analyze how the addition of personas, context, constraints, and formatting rules changes the behavior of the AI and the quality of the summarized text.
6. **Result Formulation:** Document how prompt engineering refines a generic summary into a highly targeted educational resource.

---

## Prompt Designs & Summarization Effects

### 1. Basic Prompt
> **Prompt:** Summarize the following technical article on The Basics of Blockchain Technology: [Insert Blockchain Article Here]
* **What it does:** The AI provides a generic, zero-shot summary. The output is usually a dense paragraph that might still contain too much technical jargon, as the AI doesn't know *who* the summary is for.

### 2. Role Prompt
> **Prompt:** Act as a technical content curator for an educational platform. Summarize the following article on The Basics of Blockchain Technology: [Insert Blockchain Article Here]
* **What it does:** By assigning a role, the AI shifts its tone. The summary becomes slightly more professional and structured, mimicking how an educator or curator might write.

### 3. Context Prompt
> **Prompt:** We are creating content for an educational platform that delivers quick summaries of research papers to undergraduate students. They need to grasp complex technical topics easily. Summarize the following article on The Basics of Blockchain Technology: [Insert Blockchain Article Here]
* **What it does:** The AI now understands the *audience*. It automatically simplifies the vocabulary, uses better analogies, and focuses on the high-level concepts rather than deep cryptographic mathematics.

### 4. Constraint Prompt
> **Prompt:** We are creating content for an educational platform that delivers quick summaries to undergraduate students. Summarize the following article on Blockchain Technology. **Constraints:** Keep the summary strictly under 100 words and do not use overly technical jargon. Text: [Insert Blockchain Article Here]
* **What it does:** This forces the AI to be concise. It strips away all filler words and non-essential background information, ensuring the student can read it quickly without getting overwhelmed.

### 5. Final Upgraded Prompt (Output Format)
> **Prompt:** Act as an expert content curator for an educational platform. We provide quick summaries of technical research papers to undergraduate students. Summarize the article below on 'The Basics of Blockchain Technology'. 
> **Constraints:** Keep the total length under 150 words, ensure high accuracy, and simplify the concepts so a college freshman can understand them. 
> **Format:** Output the summary using exactly 3 bullet points with a bold heading for each point.
* **What it does:** This creates the ultimate, ready-to-publish output. It combines the simplified tone for undergraduates, the strict length constraint for quick reading, and a highly scannable bulleted format.
> **Text:**
```
The Basics of Blockchain Technology

At its core, a blockchain is an append-only, cryptographically secured distributed ledger maintained across a peer-to-peer network of computational nodes without relying on a central authority. Unlike traditional centralized databases managed by a single administrator to validate and record state changes, a blockchain establishes verifiable consensus across untrusted network participants using cryptography, distributed systems theory, and economic incentive models.

Data Architecture and Cryptographic Integrity
Data within a blockchain is organized into chronologically chained structures called blocks. Each block consists of two primary components: a block header and a block body. The body contains a set of validated transactions, while the header contains essential metadata, including a timestamp, an arbitrary counter called a nonce, a target difficulty threshold, and cryptographic hashes.

Transactions within a block are hashed hierarchically into a binary tree structure known as a Merkle Tree. The top of this tree—the Merkle Root—serves as a single, fixed-size cryptographic digest representing all transactions within that block. Altering even a single bit in any underlying transaction produces a cascading change in its hash, immediately invalidating the Merkle Root and signaling data corruption.

Furthermore, each block header explicitly includes the cryptographic hash of the preceding block header. This links individual blocks into an immutable, sequential chain extending back to the initial Genesis Block. Modifying historical data requires an attacker to recalculate the hash of the tampered block and every subsequent block, rendering retroactive data manipulation computationally infeasible.

Distributed Consensus Mechanisms
In a decentralized environment lacking a central administrative operator, distributed nodes must reach dynamic, fault-tolerant agreement on the canonical state of the ledger through a cryptographic consensus mechanism.

Proof of Work (PoW): Nodes (miners) expend computational energy to solve a cryptographic puzzle—finding a nonce that generates a block hash meeting specific difficulty criteria. PoW secures the network through physical thermodynamic energy expenditure, making history rewrites exponentially cost-prohibitive.

Proof of Stake (PoS): Nodes (validators) lock up native tokens as economic collateral (stake) for the privilege of proposing and validating new blocks. Malicious behavior or double-signing results in severe financial penalties via the slashing of staked capital.

Smart Contracts and State Transition
Modern blockchains operate as decentralized, globally distributed deterministic state machines. Beyond simple value transfers, advanced networks execute self-contained programs known as smart contracts. Compiled into bytecode and executed inside isolated environments like the Ethereum Virtual Machine (EVM), smart contracts execute automatically when predefined conditions are met. Every full node on the network independently executes the contract logic against its local copy of the state, ensuring identical, deterministic state transitions across all participants.

Conclusion and Future Outlook
Blockchain technology fundamentally transforms data verification by replacing implicit trust in central intermediaries with explicit cryptographic proof and algorithmic consensus. Through the combined application of cryptographic hashing, Merkle trees, peer-to-peer propagation, and game-theoretic incentives, blockchains establish a tamper-resistant foundation for decentralized systems, transparent supply chains, and digital ownership. As modern scaling technologies like zero-knowledge rollups mature, blockchain architectures continue to redefine distributed computing.```
---

## Result
The experiment demonstrates the critical importance of prompt engineering in text summarization. 

A **Basic Prompt** yields a technically accurate but often dense and unstructured summary. However, by sequentially upgrading the prompt—adding a specific **Role**, providing audience **Context**, enforcing length **Constraints**, and defining a strict **Output Format**—the AI's behavior is completely transformed. The final summarization output is no longer just a condensed version of the text; it is a highly tailored, easy-to-read, and perfectly structured piece of educational content perfectly suited for undergraduate students.


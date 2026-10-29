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
3. **Context Priming (Setup):** Feed the 500-word article into the AI model's context window first and assign it a variable name (e.g., "Blockchain_Article") to optimize token usage and avoid redundant pasting.
4. **Prompt Design:** Construct a progressive series of prompts that reference the variable name, upgrading step-by-step from a "Basic Prompt" up to a highly detailed "Output Format Prompt".
5. **Execution:** Input the progressive prompts sequentially into the AI models (e.g., ChatGPT, Gemini) to generate the summaries.
6. **Evaluation & Result Formulation:** Analyze how the addition of personas, context, constraints, and formatting rules changes the behavior of the AI, and document how prompt engineering refines a generic summary into a targeted educational resource.

## Tools used:

ChatGPT and Gemini
 
## Prompt Designs (Progressive Structure)

To avoid redundancy and optimize token usage, we first use **Context Priming** to feed the source text to the AI, assigning it a variable name to be referenced in subsequent prompts.

### 0. The Setup Prompt (Context Priming)
> **Prompt:** I am going to provide you with a 500-word article. I want you to save this in your context window and remember it as "Blockchain_Article". Do not summarize it or analyze it yet. Just reply with "Ready" if you understand.

The 500-word article is as follows:

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
Blockchain technology fundamentally transforms data verification by replacing implicit trust in central intermediaries with explicit cryptographic proof and algorithmic consensus. Through the combined application of cryptographic hashing, Merkle trees, peer-to-peer propagation, and game-theoretic incentives, blockchains establish a tamper-resistant foundation for decentralized systems, transparent supply chains, and digital ownership. As modern scaling technologies like zero-knowledge rollups mature, blockchain architectures continue to redefine distributed computing.


### 1. Basic Prompt (Zero-Shot)
> **Prompt:** Summarize the "Blockchain_Article".
* **What it does:** The AI provides a generic, zero-shot summary. The output is usually a dense paragraph that might still contain too much technical jargon, as the AI doesn't know *who* the summary is for.

### 2. Role Prompt
> **Prompt:** Act as a technical content curator for an educational platform. Summarize the "Blockchain_Article".
* **What it does:** By assigning a role, the AI shifts its tone. The summary becomes slightly more professional and structured, mimicking how an educator or curator might write.

### 3. Context Prompt
> **Prompt:** We are creating content for an educational platform that delivers quick summaries of research papers to undergraduate students. They need to grasp complex technical topics easily. Summarize the "Blockchain_Article".
* **What it does:** The AI now understands the *audience*. It automatically simplifies the vocabulary, uses better analogies, and focuses on the high-level concepts rather than deep cryptographic mathematics.

### 4. Constraint Prompt
> **Prompt:** We are creating content for an educational platform that delivers quick summaries to undergraduate students. Summarize the "Blockchain_Article". **Constraints:** Keep the summary strictly under 100 words and do not use overly technical jargon. 
* **What it does:** This forces the AI to be concise. It strips away all filler words and non-essential background information, ensuring the student can read it quickly without getting overwhelmed.

### 5. Final Upgraded Prompt (Output Format)
> **Prompt:** Act as an expert content curator for an educational platform. We provide quick summaries of technical research papers to undergraduate students. Summarize the "Blockchain_Article".

> **Constraints:** Keep the total length under 150 words, ensure high accuracy, and simplify the concepts so a college freshman can understand them.

> **Format:** Output the summary using exactly 3 bullet points with a bold heading for each point.

* **What it does:** This creates the ultimate, ready-to-publish output. It combines the simplified tone for undergraduates, the strict length constraint for quick reading, and a highly scannable bulleted format.
  

## Final Comparison & Analysis 

Based on the outputs generated across the five progressive prompts, here is the comparative analysis between ChatGPT and Gemini for the text summarization task:

| Evaluation Criteria | ChatGPT Performance | Gemini Performance |
| :--- | :--- | :--- |
| **Accuracy** | Consistently maintained the core technical truths of the blockchain article across all prompt variations without hallucinating details. | Highly accurate; successfully retained the technical meaning even when forced to simplify the vocabulary. |
| **Coherence** | Summaries flowed smoothly. In the final prompt, the bullet points read like a cohesive, well-structured educational narrative. | Summaries were highly direct and punchy. Slightly more fragmented in the bulleted format, but extremely easy to read. |
| **Simplicity** | Adapted perfectly to the "Context Prompt" (Prompt 3), successfully stripping out heavy cryptographic jargon for the undergraduate audience. | Excelled at simplifying complex terms, providing very clear, layman-friendly explanations suitable for a college freshman. |
| **Speed** | Generated the progressive summaries quickly, though slightly slower when calculating the strict constraints of the final prompt. | Noticeably faster generation time across all 5 prompts, delivering the constrained summaries almost instantaneously. |
| **User Experience** | Followed the strict formatting of Prompt 5 (exactly 3 bullets, bold headings, under 150 words) perfectly on the first try, yielding a publish-ready result. | Followed the constraints well but included slight conversational filler (e.g., "Here is your summary:") which required minor manual editing. |

## Result

The experiment successfully demonstrated how upgrading a prompt from a basic instruction to a heavily constrained format significantly improves the AI's utility. 

A Basic Prompt yielded a technically accurate but dense summary. However, by sequentially upgrading the prompt—adding a specific **Role**, providing audience **Context**, enforcing length **Constraints**, and defining a strict **Output Format**—the outputs from both models were completely transformed into highly tailored educational resources. 

Overall, while Gemini provided faster generation speeds, ChatGPT provided a slightly superior **User Experience** by adhering flawlessly to the strict formatting and length constraints of the Final Upgraded Prompt without adding unnecessary conversational filler.

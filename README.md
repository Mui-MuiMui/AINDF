# AINDF-Spec (AI-Native Document Format Specification)
[Japanese](./README_JP.md)

Stop repeating yourself to AI. A proposal for a new data structure that encapsulates context within the code.

## 1. Introduction

AI-driven code generation has evolved dramatically, yet a deep gap remains between "developer intent" and "AI output."

* **It's exhausting to explain the project background over and over again.**
* **AI guesses libraries or values on its own, breaking existing designs.**
* **Correction prompts often fail to communicate exactly which part of the code needs fixing.**

AINDF (AI-Native Document Format) was created to structurally solve these frustrations. Instead of relying solely on prompt engineering (verbal instructions), it achieves 100% reproducibility by **embedding AI constraints and facts directly into the data structure.**

---

## 2. The Triple-Layer Architecture

AINDF proposes that a single file should consist of the following three logical layers:

### Layer 1: Context Layer (The Rule)
This layer enforces "preconditions" and "external constraints" on the AI.
* **Role**: Explicitly defines technical stacks (e.g., Tailwind v4, shadcn/ui), viewports, and the developer's intent.
* **Effect**: AI can stop guessing which tech stack to use, eradicating errors caused by environment mismatches.

### Layer 2: Implementation Layer (The View)
A layer that is human-readable and executable as a program.
* **Role**: Concrete code representation (TSX, XAML, Kotlin, etc.). The target for AI generation and transformation.
* **Effect**: Maintains high compatibility with existing assets (React, Android, Windows apps, etc.) and allows humans to make final adjustments at the code level.

### Layer 3: State Layer (The Truth / SSOT)
A layer that holds "immutable facts" shared between the AI and the editor.
* **Role**: Structured data (JSON, etc.). Includes GUI states, unique element IDs, and fixed property values.
* **Effect**: Maintains the "truth of the blueprint" even if the code is rewritten. It serves as an "answer key" for the AI, physically preventing fluctuations in modifications.

---

## 3. Core Principles

* **Stop Guessing, Start Defining**: Stop asking AI to "read between the lines" and give it the "facts."
* **Context Encapsulation**: Seal all context into a single file to achieve a portable development experience.
* **Human-AI Symbiosis**: Humans communicate via intuition (GUI/Code), and AI responds with logic (Metadata/State).

---

## 4. Implementation Example: .moc Format

A reference implementation applying AINDF concepts to a UI Builder (VSCode extension "Mocker").

* **[.moc File Format Specification](https://github.com/Mui-MuiMui/moc-spec/blob/main/README.md)**
  * *An example of an integrated data format for Humans, GUIs, and AI agents to develop collaboratively.*

> ※ While this specification is for UIs, the AINDF concept can be applied to any AI-driven development, such as API definitions, database migrations, and business logic descriptions.
> Furthermore, as the data required for communication increases with new versions, additional tags or fields may be added. However, the fundamental concept remains unchanged.

---

## 5. License

MIT License
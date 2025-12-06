# Day 9 and 10: Claude Skills & Sub-Agents

This repository contains the completed tasks for Day 9 and Day 10 of the "30 Days of Agentic Coding" challenge. The focus of these tasks was to extend Claude's capabilities by creating custom **Skills** and specialized **Sub-Agents** to automate complex workflows.

## Project Overview

The goal was to build a modular system for high-quality content creation, specifically tailored for researching, writing, editing, and formatting books or articles.

-   **Task 9:** Create a specialized Skill for robust fact-checking and research.
-   **Task 10:** Create a team of Sub-Agents to handle different stages of the writing process mainly focused on book writing.

---

## Task 9: Custom Skill - Research Fact-Checker

### Location
`.claude/skills/research-fact-checker`

### Description
The **Research Fact-Checker** skill is designed to verify facts, research topics, and ensure accuracy across various subject areas. It acts as a rigorous quality control mechanism for non-fiction, historical fiction, or any content requiring factual precision.

### Key Capabilities
1.  **Historical Verification:** Checks dates, events, timelines, and figures.
2.  **Scientific & Technical Validation:** Validates theories, processes, equipment, and industry standards.
3.  **Geographic & Cultural Accuracy:** Confirms locations, customs, traditions, and regional details.
4.  **Structured Research Process:**
    *   Identifies research needs and key claims.
    *   Provides credible sources (peer-reviewed, authoritative).
    *   Flags uncertain or contested information.

### Usage
This skill is automatically available to the agents to ensure that all generated content is grounded in reality and free from hallucinations.

---

## Task 10: Sub-Agents - The Book Writing Team

### Location
`.claude/agents/`

We have implemented a multi-agent workflow where specialized agents collaborate to produce high-quality written content. Each agent has a specific persona, toolset, and responsibility.

### The Agents

#### 1. Book Researcher (`book-researcher`)
*   **Role:** The Foundation Builder.
*   **Color:** Red
*   **Responsibility:** deep dives into topics to gather accurate facts, statistics, and historical context. It produces structured "Research Briefs" and chapter outlines. It prioritizes accuracy over style.

#### 2. Book Writer (`book-writer`)
*   **Role:** The Storyteller.
*   **Color:** Green
*   **Responsibility:** Transforms the dry Research Briefs into engaging, high-quality prose. It focuses on narrative flow, tone, and storytelling while strictly adhering to the facts provided by the Researcher.

#### 3. Book Editor (`book-editor`)
*   **Role:** The Quality Controller.
*   **Color:** Yellow
*   **Responsibility:** A ruthless critic that polishes drafts. It checks for grammar, spelling, and awkard phrasing. It also critiques logical flow and pacing, creating actionable feedback or direct improvements.

#### 4. Book Formatter (`book-formatter`)
*   **Role:** The Publisher.
*   **Color:** Cyan
*   **Responsibility:** prepares the final manuscript for publication. It ensures consistent headings, proper indentation, correct citation formatting, and produces a clean, production-ready Markdown file.

---

## How it Works Together

1.  **Research:** The `book-researcher` uses the `research-fact-checker` skill to gather data and creates an outline.
2.  **Drafting:** The `book-writer` takes the outline and writes the content.
3.  **Review:** The `book-editor` reviews the content and suggests changes.
4.  **Finalize:** The `book-formatter` structures the final document for export.

## Directory Structure

```
.
├── .claude/
│   ├── agents/
│   │   ├── book-editor.md
│   │   ├── book-formatter.md
│   │   ├── book-researcher.md
│   │   └── book-writer.md
│   ├── skills/
│   │   └── research-fact-checker/
│   │       └── SKILL.md
│   └── settings.local.json
└── README.md
```

# AI SDCI Session Notes

## Idea

The main idea is to clean everything as a scope in the beginning because the idea is to keep the `context flow` stable. If at some point the context is changed, all this automated agent flow can be ruined.

---

## Phase 1: Design and High-Level Planning

This phase is about establishing the foundational documents, designs, and high-level strategy for the project.

### 1. Business Requirements Document/Product Requirement Document (BRD/PRD) → Business Analyst Gem

- Generate a comprehensive BRD. This document should be considered stable and final before moving to the next step to minimize rework.
- **What it contains:**
  - Introduction Summary
  - Business Case & Goals
  - Target Audience
  - Scope
  - Function Requirements
  - Assumptions
  - Constraints & Dependencies
  - Risk & Mitigation Plan
  - User Flows

### 2. Generate User Stories from BRD → Business Analyst Gem

- After the BRD is finalized, use the Gem to derive epics and user stories.
- The creator's role is to review the AI's suggestions, adding details like specific acceptance criteria or negative test cases.

### 3. Create Software Design Document (SDD) → Software Architect Gem

- The full user story backlog is provided as input to the Architect Gem.
- The resulting architecture document may, in turn, lead to the creation of new technical or infrastructure-related stories which are added back to the backlog.
- **What it contains:**
  - Purpose and Scope
  - Definitions
  - Architectural Goals and Constraints
  - System Overview - C4 Level 1: System Context
  - High-level Design C4 Level 2: Container View
  - Detailed Design C4 Level 3: Component View
  - Architectural Diagram of components
  - Web App
  - Smart Contracts
  - Backend API
  - Database Scheme - Data Design
  - Key Workflows

### 4. Create Visual Prototype and Style Guide → Designer

- Based on the BRD and user stories, designer creates a visual prototype and a preliminary style guide.

### 5. High Level Test Plan to SDD → QA Engineer

- Reviews BRD, SDD and the visual prototype to understand the system scope and requirements.
- Contributes a high-level test plan directly to the Software Design Document, outlining:
  - Testing strategy
  - Types of testing required
  - Critical areas of focus

### 6. Contribute High-level Deployment Strategy to SDD → DevOps Engineer

- Reviews the BRD and SDD to formulate a high-level deployment strategy.
- Added to the SDD and includes recommendations for:
  - Target infrastructure
  - CI/CD pipeline
  - Key considerations for production monitoring and scalability

### Note: After Phase 1

After I have all the documents:
- Put them in NotebookLM and share it with my team
- Create a Mind-map on them to visualize what is going to happen in detail to understand what I have to do

---

## Phase 2: Development, Testing and Deployment

After I am done with Phase 1, here is the Team Lead job to create a blueprint.

### On Gemini: Create a Gem for a Role

- For example, use the repo for LLM - Instruction Set to create `Software Implementor` that I can use to generate a Blueprint of my project by loading my PDF files for the scopes, research and so on.

### Create a Blueprint for the Project

1. Create a folder `docs/` and there create a `story-000.md`
2. Paste the blueprint there

### Implementation Process

1. **Use Claude Code to create an Implementation Plan (Plan Mode)** for `docs/story-000.md`
2. **REVIEW the whole plan** - every line - and decide if everything is alright
3. **Before starting to code**, ask Claude to create an issue for the Implementation Plan
4. **When it starts with the Implementation Plan**, it should:
   - Create a PR
   - Link it to the issue
   - So I can add additional agents to review the PR like `almanax` solidity security auditor
5. **When I merge it**, I can ask Claude to give me the discrepancies between the story and what was implemented
6. **Then I use Gemini** to say that using my `story-00` here is what I implemented (paste it)
   - The idea is to keep both models in sync of the process
   - Ask Gemini to continue with the next story (blueprint)

### Important: Rules and Framework

- It is also important to have `rules` set for the model that implements the Implementation Plan, to keep everything under control:
  - Guidelines
  - Good practices
  - Templates
  - PR templates
  - Skills
  - Review
- This provides a framework and avoids chaotic behaviour
- I must have an `IMPLEMENTATION_STATUS.md` document after every feature

### Auto-Approval

- If I agree, I can use `auto-approve` for Claude to start implementing without asking me on every step
- So I can configure to automatically create PR's and so on
- I can add additional agents like `ALMANAX` to audit my code

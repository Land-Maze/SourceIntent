# 1. Introduction and Goals

## 1.1 Requirements Overview

### Purpose

SourceIntent helps solo developers and small development teams—especially “vibe coders” working with LLM-based coding agents—turn rough project ideas into structured documentation that those agents can work from. It provides an easy, low-effort way to clarify intent, record architectural decisions, and prepare specifications and backlogged tasks without requiring users to maintain a heavyweight planning process manually.

SourceIntent uses AI to support brainstorming and backlog preparation. The product's primary value is project context and planning, rather than task tracking alone or autonomous implementation.

Users are not expected to know arc42, ADRs, or architectural terminology. SourceIntent should ask plain-language questions and explain unfamiliar concepts as users encounter them, helping them structure their ideas without requiring prior architecture knowledge.

### Main capabilities

- Organize projects within workspaces, with documentation and planning artifacts belonging to a project.
- Help users explore an initial idea and define project goals, requirements, and constraints through guided conversation.
- Provide contextual **“?” help buttons** throughout the application, with brief explanations of concepts and available actions.
- Briefly explain how the product works on the landing page, so users understand the path from an idea to documentation and implementation planning.
- Draft arc42 architecture documentation and Architecture Decision Records (ADRs), and create implementation tasks.
- Let users review proposed changes, approve them in the current conversation, or reject them for further iteration.
- Produce a `docs/` directory containing project artifacts that the user can download without connecting GitHub.
- Optionally connect a GitHub account and commit approved documentation and ADRs to the project's repository on `main` when the user explicitly selects **Sync with repository**.
- Prepare feature work by creating a new branch and handing off to an OpenSpec workflow, with specifications and backlogged tasks guiding the user's coding agent.

### Conversation modes

The project's chat panel offers three modes that guide the focus of the conversation:

| Mode | Focus |
| --- | --- |
| Architecture | Define and revise the project's high-level idea, goals, and constraints. |
| Brainstorm | Explore and refine both the high-level project idea and its technical architecture. |
| Plan | Create tasks describing what to implement. |

These modes are conversational entry points, not permission boundaries or separate plan/edit phases. Users can approve a proposed change in the mode where it arises, including an architectural change discovered during Brainstorm, without switching to Architecture. Approval of a change does not itself publish it to GitHub; repository synchronization remains a separate, explicit action.

### First-session outcome

A user who arrives with a rough idea should leave with arc42 documentation that captures the project's intent, goals, and constraints and provides structured context for an LLM-based coding agent. The documentation belongs to a project within a workspace and can be downloaded or explicitly synchronized to GitHub.

### Intended workflow

1. Within a project under a workspace, the user describes an idea. An LLM helps clarify its goals and constraints using arc42 as a structure.
2. Using Architecture and Brainstorm as conversational entry points, the user refines the idea and technical direction. SourceIntent drafts architecture documentation and ADRs that capture the resulting understanding and decisions.
3. The user reviews proposed changes in the current conversation. Rejected content returns for further iteration; approved changes become part of the project's documentation.
4. The user can download the project's `docs/` artifacts. Alternatively, after connecting a GitHub account, the user explicitly selects **Sync with repository** to commit approved documentation and ADRs to `main`. Neither connecting GitHub nor approving a change triggers synchronization by itself.
5. Plan mode helps the user create implementation tasks. For repository-connected feature work, SourceIntent creates a new branch and hands off to the OpenSpec workflow: **Propose → Apply → Archive**.
6. The user's coding agent works on the specification and completes the OpenSpec workflow on the user's side, rather than inside the SourceIntent website. PR approval to `main` also takes place on the user's side.

### Scope boundary

SourceIntent supports brainstorming, documentation, repository synchronization, and preparation of feature work. Feature implementation, completion of the OpenSpec workflow, and PR approval remain on the user's side. SourceIntent is not an autonomous implementation or merge platform.

Architecture chapters use `docs/architecture/xx-name.md`, where `xx` is the two-digit arc42 chapter number. ADRs are stored under `docs/architecture/adr/`.

## 1.2 Quality Goals

The following qualitative priorities guide the architecture. They are goals, not claims about the current implementation.

| Priority | Quality goal | Motivation |
| --- | --- | --- |
| 1 | Low effort and usability | Users should be able to turn an informal idea into useful project documentation without prior architecture knowledge or manually maintaining an elaborate process. Plain-language guidance, contextual “?” help, and a brief landing-page explanation should make the workflow understandable. Conversation modes should guide discussion without forcing mode switches to approve changes. |
| 2 | Clear, agent-readable context | Architecture documentation, ADRs, specifications, and tasks should communicate intent and constraints clearly enough for a coding agent to act on them. |
| 3 | User control | Generated changes must be reviewed and approved, with rejection allowing further iteration. Only the explicit **Sync with repository** action publishes approved documentation to GitHub. Implementation and PR approval remain on the user's side. |
| 4 | Documentation consistency | Architecture documentation, decisions, specifications, and backlogged tasks should describe the same project intent without contradictory guidance. |
| 5 | Traceability | Decisions and planned work should be connectable to the goals, requirements, and constraints that motivated them. |
| 6 | Portability | Users should be able to download the project's documentation as files under `docs/` without requiring a GitHub connection. |

## 1.3 Stakeholders

| Stakeholder | Expectations |
| --- | --- |
| Solo developers and vibe coders (primary users) | Quickly clarify ideas, obtain useful documentation for their coding agents without needing prior architecture knowledge, receive guidance and explanations when needed, and retain control over what reaches their repository. |
| Small development teams (secondary users) | Establish shared project context, record architectural decisions, and prepare clearly specified feature work. |
| Project maintainers and reviewers | Understand the intent behind proposed changes and review documentation and implementation before they enter `main`. These responsibilities may belong to the same person as the primary user. |

The user's LLM-based coding agent is a downstream consumer of the documentation and specifications, rather than a human stakeholder. Its need for clear context is reflected in the quality goals above.

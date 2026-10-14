# SourceIntent Architecture

This directory documents SourceIntent using [arc42](https://arc42.org/): its goals, boundaries, constraints, architecture, and quality requirements. Architectural decisions are recorded separately as ADRs.

SourceIntent helps users turn rough project ideas into structured documentation and implementation plans for LLM-based coding agents. No prior architecture knowledge is required.

## Chapters

Chapter numbers follow arc42. Chapters are created incrementally; only drafted chapters are linked below.

| Chapter | Topic | Status |
| --- | --- | --- |
| 01 | [Introduction and Goals](01-introduction-and-goals.md) | Drafted |
| 02 | Architecture Constraints | Not yet drafted |
| 03 | Context and Scope | Not yet drafted |
| 04 | Solution Strategy | Not yet drafted |
| 05 | Building Block View | Not yet drafted |
| 06 | Runtime View | Not yet drafted |
| 07 | Deployment View | Not yet drafted |
| 08 | Crosscutting Concepts | Not yet drafted |
| 09 | Architecture Decisions | Not yet drafted |
| 10 | Quality Requirements | Not yet drafted |
| 11 | Risks and Technical Debt | Not yet drafted |
| 12 | Glossary | Not yet drafted |

## File conventions

- Chapters: `xx-name.md`, using the two-digit arc42 chapter number and a lowercase, hyphenated name.
- Architecture Decision Records (ADRs): stored in [`adr/`](adr/).
- Chapter 09 will provide an overview of architectural decisions and link to individual ADRs rather than duplicate their contents.
- Update this index when a chapter is added.

These documents describe the intended product and architecture; they do not imply that the capabilities are already implemented.

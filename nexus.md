# Nexus

A command-line OSINT investigation tool for licensed private investigators and authorized researchers. Given one or more seed identifiers (name, email, phone, username, address), Nexus runs a coordinated sweep across dozens of public data sources and produces a structured dossier and formatted report.

---

## Problem

Open-source intelligence gathering is highly manual. A PI working a skip trace or background check must run the same searches across dozens of tools and websites, then manually consolidate and deduplicate the results. This process takes hours and is inconsistent across investigators.

Nexus automates that workflow from a single command.

---

## How It Was Built

I defined the requirements, selected the data sources, and validated the output against real data. The code was developed with AI coding assistants (Claude Code) to my specification; I read, modify, and debug it.

Components:

- **CLI:** Clean command interface accepting any combination of seed inputs; supports targeted investigation depth, court record toggling, and dark web search
- **Orchestration engine:** Manages execution across multiple tool tiers, running tools concurrently within each tier; dynamically selects which tools to run next based on what information is still missing from the dossier
- **Tool integration layer:** Unified wrapper interface over 35+ external OSINT tools and data sources; handles subprocess execution, API calls, output parsing, and error recovery consistently across all tools
- **Dossier data model:** Strongly-typed, deduplicated data model that accumulates findings across all sources; tracks confidence and flags unresolved conflicts
- **Report generator:** Produces both a machine-readable JSON dossier and a formatted DOCX case file

---

## Key Capabilities

- Single command to run a multi-source investigation against any combination of name, email, phone, username, address, or domain
- Concurrent tool execution within each investigation phase
- Automatic gap detection: identifies what information is still missing and selects appropriate tools to fill it
- Social account discovery across thousands of platforms
- Breach and credential exposure checks
- People-search and address resolution
- Court record retrieval
- Optional dark web search via Tor
- Structured JSON dossier + DOCX report output

---

## Stack

Python · asyncio · Click · Pydantic v2 · Rich · python-docx · httpx

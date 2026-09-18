# Agentic AI Archetype Finder

A small, single-file web tool that scores an AI system on twelve dimensions and returns the nearest of six archetypes, from *not agentic* to *cross-organisation agents*. It is meant for people in government who have to decide whether a system is agentic at all, and if so, what kind.

**Early-stage prototype.** The approach, the dimensions and the archetypes were developed by colleagues at the Responsible IT Lab, Hogeschool van Amsterdam. Placements, thresholds and archetypes are still under discussion and will change. The code was vibe-coded with Claude Code and should be read as a sketch of the method, not as a validated instrument.

## Use it

Open `index.html` in a browser. Nothing to install, no server, no data leaves the page.

1. Move the sliders to describe the system. Every position is a named anchor; hover or read the text under each slider.
2. Read the result on the right: the nearest archetype, how far the system is from it, comparable examples, and notes on combinations that deserve attention.
3. Optionally set the three context attributes (reversibility, error tolerance, data sensitivity). They do not change the match; they change which notes appear.
4. Open *How the result is determined* at the bottom to see the rules, with the ones currently firing highlighted.

The buttons at the top load each archetype's profile so you can see what a pure case looks like.

## How it decides

- **Gate.** The five agency dimensions are control flow, tool use, underspecification, goal directedness and long term planning. The agency level is the highest of the five scores. Level 1 means not agentic; 2 or more means agentic.
- **Match.** Within its group (non-agentic or agentic), the system is compared with each archetype by the sum of absolute score differences over the twelve dimensions. The smallest distance wins. Scores are ordinal: shapes can be compared, totals mean nothing.
- **Notes.** Rules fire on combinations of the profile and the context, for instance a fixed flow with an open goal, or unmediated actions that cannot be undone.

## Dimensions and sources

One reference per dimension.

| Group | Dimension | Source |
|---|---|---|
| Control | Control flow | Schonenberg et al. (2008), process flexibility |
| Control | Tool use | Mialon et al. (2023) |
| Agency | Underspecification, directness of impact, goal directedness, long term planning | Chan et al. (2023), FAccT |
| State | Memory | Sumers et al. (2023), CoALA |
| State | Learning | Russell & Norvig (2021), learning agents |
| Multiplicity | Number of agents, orchestration | Wooldridge (2009) |
| Multiplicity | Ownership | Hammond et al. (2025) |
| Human role | Human role | Feng, McDonald & Zhang (2025) |
| Context | Reversibility, error tolerance, data sensitivity | IMDA (2026) |

The form of the input and output (structured or free text) is deliberately not a dimension: it describes the interface, not the agency.

## Files

- `index.html`: the tool, self-contained.
- A Python version with the same model and a JSON API (`POST /api/score`) exists as a separate FastAPI project, and an Excel workbook implements the same scoring in formulas.

## Licence and contact

No licence chosen yet; ask before reuse. Contact: Responsible IT Lab, Hogeschool van Amsterdam.

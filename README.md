# Sport4All

Concept shell prototype — Evolving Technologies CA1, Postgraduate Diploma in
Sports Analytics, Technology and Innovation.

**Challenge:** Inclusive Sports Technology Solutions
**Focus area:** Artificial Intelligence and GenAI
**Live:** https://karlhopkins-creator.github.io/sport4all/
**Repo:** https://github.com/karlhopkins-creator/sport4all

## Problem
Membership cost is a barrier to getting children from lower-income households
into organised sport. Supports exist (Local Sports Partnerships, the S4E ESF+
programme) but families struggle to find or reach them, and clubs have no way
to signal unmet demand to funders.

## Core function
A proposed Sport Ireland scheme, delivered with Local Sports Partnerships, that
covers most of a child's club membership fee for qualifying families.
Eligibility is verified on the parent's own DSP status via MyGovID, so no child
data, income figure or PPSN is ever collected. Qualifying families receive a
fee-support code; the club applies it to the fee and claims the balance through
the scheme.

## User flow demonstrated
Parent: landing → data consent → eligibility check (MyGovID) → result →
fee-support code (eligible) or local options (ineligible) → AI-matched club and
session shortlist near you.
Club: portal sign-in → redeem a family code → balance calculated and claimed.
An LSP dashboard surfaces anonymised cost-barrier flags by area for funding
cases. Use the **Demo** toggle at the foot to switch the eligible and
ineligible paths.

## Where the AI acts
After eligibility is resolved or skipped, the app returns a ranked shortlist of
local clubs and taster sessions matched to the child's age band, location and
sport interest, each with a one-line reason. In production this is a recommender
ranking open places, distance, inclusivity signals and session fit; here the
shortlist and rationales are staged sample outputs.

## Real vs simulated
Real: the full clickable flow, the UI, the fee/subsidy calculation (90% to a
€150 cap), code generation and the club balance maths.
Simulated: the MyGovID/DSP eligibility check, the AI recommendations and their
rationales, the dashboard figures, and the Sport Ireland–DSP data-sharing
arrangement, which is an assumption of the concept and not yet in place.

## Build
Single self-contained HTML/React file, deployed on GitHub Pages. The platform
build prompt used to generate this prototype is in `build-prompt.md`.

## Team
Karl Hopkins — [email] — A00050660
Kevin [surname] — [email] — [student number]

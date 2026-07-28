# Sport4All — build prompt

This is the consolidated build prompt for the Sport4All shell prototype. The
prototype was produced iteratively rather than from a single generation: an
initial build (HTML, Tailwind CSS, vanilla JavaScript, with Google Gemini) was
rebuilt and extended in React (with Claude, Anthropic). This prompt is the
specification that governed both passes, consolidated into one document. The
screen flow, content and interaction design are the team's own.

---

## Prompt

Build a mobile-first, single-file React web app called **Sport4All**: a shell
prototype of a proposed Sport Ireland scheme that covers most of a child's
club membership fee for qualifying families, delivered with Local Sports
Partnerships. All intelligence is staged; nothing calls a real service.

### Design principles (non-negotiable)

1. **Verify the parent, never the child.** Eligibility is a Yes/No check on
   the parent's own DSP status via MyGovID. No child data, income figures,
   PPSN or medical-card numbers are collected or shown anywhere.
2. **No disclosure wall.** The app must deliver value on minimal input. A
   "just show me clubs near me" path bypasses the eligibility check entirely.
3. **Every path returns something useful.** The ineligible result is not a
   dead end: it routes to the same club-matching and local options as the
   eligible path.
4. **Dignity in language.** Plain English, no means-test vocabulary at the
   club gate, no stigmatising framing.

### Parent flow (core user flow, clickable start to finish)

1. **Landing** — what the scheme is, MyGovID as sign-in and trust signal, and
   the skip path ("Just show me clubs near me").
2. **Consent** — plain-English data statement: only the parent's Yes/No
   result, a rough location (county or Eircode) and the child's age band are
   kept.
3. **Checking** — simulated secure check (client-side timeout standing in for
   the MyGovID/DSP handshake).
4. **Eligible result** — issues an anonymous fee-support code (format
   XXXX-XXXX), support of up to 90% of the fee to a €150 cap per child per
   season, a copy-code control, and a short how-it-works.
5. **Ineligible result** — respectful framing, straight into local options.
6. **Options screen (shared)** — collects county and age band, then returns
   an **AI-matched shortlist** of three local clubs/taster sessions, ranked,
   with a "Best match" pill on the top result, chips (open places, no fee,
   free sessions, welcome policy) and a one-line rationale per card next to a
   sparkle icon. Label beneath: "AI-suggested and staged for this demo."
   Kildare returns a bespoke set (Newbridge Town FC, juvenile GAA, Athy
   Community Sport Hub); other counties return plausible county-named
   entries. Each card links out to a maps search. Below the shortlist, four
   signposting cards: Local Sports Partnership coordinator, free taster
   sessions, second-hand kit exchange, Citizens Information.

### Club flow

1. **Club portal sign-in** (staged).
2. **Redeem a code** — enter the family's code and the fee; the app shows the
   covered amount (90% to the €150 cap) and the balance the club claims.
3. **Dashboard** — anonymised staged metrics: codes redeemed, families
   supported this season, cost-barrier flags in the area (the demand signal
   for the LSP's funding case). No child is named or tracked.

### Demo affordances

- A labelled demo toggle at the foot of the app switches the checking step
  between the eligible and ineligible outcomes so a reviewer can walk both
  branches.
- All staged elements are visibly labelled as simulated.

### Technical constraints

- Single self-contained `index.html`. React compiled to plain
  `React.createElement` calls (no in-browser Babel), wrapped in a
  `window.__boot` function. Load React 18 from CDN with a fallback source and
  a 15-second watchdog that shows a readable error instead of hanging.
- Mobile-first layout (~380px), system font stack, restrained palette
  (deep pine green primary, warm neutrals), generous touch targets.
- No external CSS or JS beyond the React CDN. No real network calls, no
  analytics, no storage.

### What is real vs simulated

Real: the full clickable flow, the UI, the fee/subsidy calculation, code
generation and the club balance maths. Simulated: the MyGovID/DSP eligibility
check, the AI recommendations and their rationales, the dashboard figures,
and the Sport Ireland–DSP data-sharing arrangement, which is an assumption of
the concept.

---

*AI assistance: Google Gemini (initial build), Claude by Anthropic (React
rebuild and extension). Cited per the CA1 build guidelines.*

# CLAUDE.md

## Project Overview

Marketing site for **AI Receptionist for Locksmiths** — a UK-wide locksmith vertical from Antek Automation targeting the locksmith AI-receptionist / answering-service search cluster.

**Live domain:** aireceptionistforlocksmiths.co.uk
**Repo:** github.com/Nipstar/locksmiths-ai

**Repo type:** UK-wide locksmith vertical site. NOT a location satellite. Sibling to aiforelectricians.co.uk, aiforplumbers.co.uk and aireceptionistforlawfirms.co.uk — all SPOKES of the national receptionist hub at aivoiceagentreceptionist.co.uk.

## Tech Stack & Build

- Zero build step. Static single-page site.
- `index.html` is the entire site (~2,500 lines) with inline CSS + JS.
- Cloned from plumbers-ai (-> a--voice-law-uk -> voice-ai-receptionist -> aiforelectricians) — keeps the Antek network design system (dark theme, Sora/DM Sans, blue/cyan/green palette) intact.

## Target Keywords (from GSC)

- **Primary:** "ai receptionist for locksmith services" (~pos 23, no dedicated page before this site) — H1 / title / meta / FAQ
- "ai voice agent for locksmith" — already #3 organically off the hub; protect and strengthen, do not dilute (service-card H3)
- "ai voice agents for locksmiths", "ai answering service for locksmiths / locksmith", "answering service(s) for locksmiths" — H2/H3, FAQ, schema serviceType
- "ai locksmith" — ambiguous; sparingly (meta keywords + the FAQ guardrail answer only). Never in headings.

## Anti-Cannibalisation Rules (CRITICAL)

1. **National only.** No geographic targeting. Locality sites own places.
2. **Hub-and-spoke:** this is the LOCKSMITH SPOKE. The hub (aivoiceagentreceptionist.co.uk) links here from its "who we help" locksmith card. Do NOT re-fight the generic "ai receptionist" head term.
3. **Locksmith vertical only.** No plumber / electrician / legal / etc. terms — those belong to their own spokes.
4. Antek also runs `aivoiceagentsforhomeservices.co.uk` — check it does not target locksmith terms in H1/headings/title before traffic ramps.

## Locksmith Accuracy Guardrails (CRITICAL)

1. The AI answers calls, qualifies and books — it does NOT attend jobs, cut keys or perform locksmith work.
2. Do NOT claim Antek/the AI is MLA-approved, DBS-checked or insurance-backed. Those are the locksmith customer's credentials — reference as AUDIENCE credentials only (copy/FAQ/schema).
3. No invented locksmith client, case study, testimonial or results figure. Demo strip is generic with TODO flags (HTML comments) for Andy to add a real locksmith reference + demo phone number. The Bolt chat-iframe demo (boltelectrical.uk — a generic UK trade site) is inherited from the template; the plumbing Retell orb + phone demo were deliberately NOT carried over.
4. British English. "30+ years" is always attributed to **Andy Norman**, never the company. Pricing stays vague — "book a call for a quote".

## Architecture

`index.html`:
1. `<head>` — meta, OG/Twitter, single `@graph` JSON-LD (Organization+ProfessionalService + Person), separate FAQPage JSON-LD, all CSS, Retell widget v2
2. Body sections: `hero`, `pain-points`, `services`, `demo`, `how-it-works`, `who-we-help` (8 locksmith-type cards), `why-us`, `founder`, `faq`, `contact`
3. About-micro (SEO-dense paragraph)
4. Footer (Antek parent + hub + electricians + plumbers + law-firms)
5. Bolt chat demo modal + scripts at end of body

## Schema

ONE @graph in head — Organization+ProfessionalService node (@id `https://aireceptionistforlocksmiths.co.uk/#organization`) + Person node (shared @id `https://www.antekautomation.com/#andynorman`, identical to plumbers-ai except `worksFor` pointing at this site's Organization @id). FAQPage is a separate `<script type="application/ld+json">` block. Never create a second competing Organization/Person.

## FAQ Parity

Every FAQ must appear identically in BOTH the visible accordion AND the FAQPage JSON-LD. Exactly 10 entries (what is it, emergency triage, job-type qualification, 24/7 + answering service, calendar/CMS, sounds natural, sole-trader fit, keep your number, no-attend/no-cut-keys/MLA guardrail, live demo).

## Contact Form / Cal.com / Retell

- n8n iframe: `https://auto.juxtarank.com/form/17d8ddcd-4860-4dde-bd4a-2de0adb518e2`, min-height 1200px.
- Cal.com: antek-automation/30min.
- Retell widget v2, shared public key + agent ID; `data-dynamic` = `{"site": "locksmiths", "domain": "aireceptionistforlocksmiths.co.uk"}`.

## .htaccess

Verbatim from plumbers-ai: HTTPS, /index.html -> /, HSTS + security headers, Permissions-Policy microphone for `self` + `https://boltelectrical.uk` (Bolt demo iframe).

## Internal Linking

Footer: Antek parent + hub + aiforelectricians.co.uk + aiforplumbers.co.uk + aireceptionistforlawfirms.co.uk. This site is linked reciprocally from the hub's who-we-help card and from the footers of the electricians, plumbers, law-firm and hub sites.

## Open TODOs (Andy)

- Real locksmith demo phone number + named locksmith reference (demo strip + FAQ 10).
- Locksmith-specific Bolt chat demo to replace boltelectrical.uk.
- Confirm hello@aireceptionistforlocksmiths.co.uk mailbox exists (inherited pattern from plumbers-ai).
- `logo.svg` referenced by schema (same as plumbers-ai) — check it exists on the domain.

## Deployment

Static — push to any host. GitHub: `github.com/Nipstar/locksmiths-ai`, branch `main`.

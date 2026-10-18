# One-Pager: Apply Kit — cvdrops.com

**Author:** Ahmet Berk Conker (Founder & PM) · **Product:** cvdrops.com, AI-powered CV builder (TR / EN / DE) · **Status:** Shipped

## 1. Problem

Turkish-speaking candidates applying for jobs in Germany and internationally usually send one generic CV to every posting. Tailoring a CV and cover letter to each job is slow, so most candidates skip it. The result is weak keyword match in ATS screening and low response rates.

**Evidence that shaped the problem**
- Candidates already had a CV but didn't know how to adapt it to a specific posting.
- Tailoring is repeated for every application, so the cost adds up across dozens of applications.
- Language is an extra barrier: the CV may be in Turkish while the posting is in German or English.

## 2. Target user

- **Primary:** Turkish-speaking job seekers applying to roles in Germany or internationally.
- **Secondary:** New graduates reached through university career offices.

## 3. Goal

Turn "tailor my application to this job" from an hour of manual work into a guided flow of a few minutes, and make it the main paid action in cvdrops.

## 4. Solution: Apply Kit

The user pastes a job posting, and Apply Kit generates a **tailored CV and cover letter** based on the user's existing cvdrops CV.

**User flow**
1. The user finishes their base CV in the 13-step guided wizard.
2. The user opens Apply Kit and pastes the job posting text.
3. The Claude API analyses the posting (requirements, keywords, seniority) against the CV.
4. Output: a tailored CV version and a matching cover letter in the selected language (TR / EN / DE).
5. The user reviews and edits, then exports.

**Funnel around it**
- **Free ATS score (no sign-up)** is the acquisition hook. It shows the gap between the CV and ATS expectations and leads naturally into Apply Kit.
- Apply Kit is the core paid action.

## 5. Requirements

| # | Requirement | Priority |
|---|---|---|
| R1 | User can paste a free-text job posting (any of TR / EN / DE) | Must |
| R2 | Output keeps the user's real experience; AI may rephrase and reorder but must not invent jobs, dates or achievements | Must |
| R3 | Tailored CV and cover letter are generated in the selected output language | Must |
| R4 | User can edit the output before export | Must |
| R5 | Each Apply Kit run consumes credits; the user sees the cost before running | Must |
| R6 | Output stays ATS-friendly (simple structure, no tables or graphics in the CV body) | Must |
| R7 | Generated versions are saved per job so the user can return to them | Should |

**Acceptance criteria (examples)**
- If the posting is empty or too short, the user gets a clear error and no credits are consumed.
- If generation fails, no credits are consumed and the user can retry.
- The output contains no employer, title or date that isn't in the base CV.

## 6. Pricing decision

**One-time credit packs instead of a subscription.** Job searching is episodic: users are intensive for a few weeks, then stop. A subscription would create churn and refund friction. Pay-per-action matches value to usage, and the free ATS score keeps the entry barrier at zero.

## 7. Success metrics

- **Activation:** % of ATS-score users who create an account and complete a base CV.
- **Conversion:** % of base-CV users who buy a credit pack.
- **Core usage:** Apply Kit runs per paying user.
- **Quality guardrail:** edit rate on generated output and user-reported "invented content" issues (target: zero hallucinated experience).
- **Acquisition:** traffic and sign-ups from SEO and university career-office channels.

## 8. Risks & mitigations

| Risk | Mitigation |
|---|---|
| AI invents experience | Strict prompt rules + R2 acceptance check + mandatory user review before export |
| API cost per run is too high | Credit pricing set above per-run model cost; failed runs don't consume credits |
| Low trust in an unknown brand | Free ATS score with no sign-up to prove value first |

## 9. Tech & launch

- **Stack:** Next.js, Supabase, Claude API, Vercel.
- **Measurement:** GA4, Microsoft Clarity, Search Console.
- **Go-to-market:** SEO + university career-office outreach.
- Built and launched end to end with AI-assisted development (Claude Code).

# TLVA – 2-Week Validation Plan (Preschool)

## Goal
Validate desirability (kids), viability (parents), and feasibility (production cadence) before a full build.

## Hypotheses
- H1: Preschoolers (ages 4–6) will complete a short interactive episode and request another.
- H2: Parents perceive learning value and would commit weekly.
- H3: A template-driven episode can be produced in < 6 hours using reusable assets.

## Success Criteria (Pass/Fail Gates)
- 70%+ session completion
- 50%+ kids ask for another session within 48 hours
- 50%+ parents say they would pay or commit weekly
- Episode production time < 6 hours

## Prototype Scope (Lean)
- One region: Word Forest
- One 8–10 minute episode
- Two interaction moments (Find & Point, Match & Sort)
- One “secret moment” (visual overlay + VO line)
- Manual difficulty adjustment (Wizard-of-Oz)

## Content Approach (AI-Assisted)
- Use AI for word lists, prompt variants, and VO draft lines
- Human review for age-appropriateness and clarity
- Reuse a single background pack; vary props and words only

## Roles and QA
- AI: generate word lists, prompt variants, and VO drafts
- You: QA for age-appropriateness, clarity, and pedagogy
- Final pass: remove ambiguous wording and ensure instructions are 1-step for Band A

## Preschool QA Checklist (Band A)
- One-step instructions only
- No negations or “except” phrasing
- 2–3 options max per interaction
- Concrete nouns first (cat, dog, apple)
- High contrast visuals and clear audio
- Consistent verbs (“tap,” “find,” “match”)
- Immediate positive feedback on success
- Avoid time pressure in early tiers

## Tools (Minimal)
- Web prototype (Svelte or plain HTML) + screen recording
- Controller: simple phone web page with 3 buttons
- Session pairing via a printed code or shared link

## Test Design
- Sample: 5–8 families with preschoolers
- Two sessions per child (same episode with small variations)
- Observe: completion, engagement, confusion points, help usage

## Metrics to Capture
- Completion rate
- Time to first interaction
- Help usage
- Prompt clarity issues
- Parent survey responses (5 questions)

## Parent Survey (5 Questions)
1. Did your child seem engaged?
2. Would you want this weekly?
3. Did it feel educational?
4. Was the interaction easy to use?
5. What would you pay per month? (range)

## 2-Week Timeline

### Week 1
- Day 1: Define targets and word list (Band A) (AI draft, your QA)
- Day 2: Draft VO lines + visual storyboard (AI draft, your QA)
- Day 3: Build prototype (episode + 2 interactions)
- Day 4: Internal test + fix confusing prompts
- Day 5: Recruit families + schedule sessions

### Week 2
- Day 6–8: Run tests (Session 1)
- Day 9: Analyze feedback + micro-iterate
- Day 10–11: Run tests (Session 2)
- Day 12: Analyze results
- Day 13: Decision checkpoint (go / pivot / pause)
- Day 14: Write summary report

## Decision Outputs
- Go: Build 3-episode mini-season
- Pivot: Adjust target age or interaction model
- Pause: If engagement or parent interest is weak

# AI Classroom Listener - Professor Dashboard Prototype v1

## What You're Building

Build a single-file HTML dashboard (`index.html`) that demonstrates what an AI-powered classroom participation assessment tool would look like from a **professor's perspective**. This is a product demo for the INSEAD Venture Competition - it needs to look like a real product, not a toy.

The concept: A microphone sits in a lecture hall. AI processes the audio after each class: identifies speakers, transcribes contributions, assesses quality, and builds longitudinal profiles of every student across the term. This dashboard is what the professor sees.

## Design Language

- **Dark theme**: background #0a0a0a, card backgrounds #111, borders #222
- **Gold accent**: #d4a843 for highlights, rankings, data emphasis
- **Fonts**: JetBrains Mono (monospace, for data/labels) + DM Sans (UI/body text)
- **Aesthetic**: Premium, minimal, data-dense. Think Bloomberg terminal meets Spotify Wrapped.
- **No build tools**: Single HTML file, inline CSS and JS. Hosted on GitHub Pages.

## Architecture

Single HTML file with **tab navigation** at the top:
1. **Sessions** (default view) - Select a session, see the deep dive
2. **Section** - All 70 students ranked and sortable
3. **Trends** - Participation over time

Plus a **student profile card** as a modal overlay, triggered by clicking any student name from any view.

A **section selector** in the header should show "Section D" as active, with greyed-out A/B/C/E options (implying the tool works across sections, but we're demoing D).

## The Course: Organisational Behaviour (OB)

7 double sessions (each covers 2 class periods):

| Sessions | Title | Case/Framework | Date |
|----------|-------|---------------|------|
| 1 & 2 | Negotiation | Red Banana simulation, BATNA, emotional tactics | 12 Jan 2026 |
| 3 & 4 | Group Decision-Making | 12 Angry Men, hidden profiles, minority influence | 15 Jan 2026 |
| 5 & 6 | Leading Diverse Teams | Apollo 13, superordinate goals, remote teams | 22 Jan 2026 |
| 7 & 8 | Power & Politics | Axelrod, tit-for-tat, coalition building | 29 Jan 2026 |
| 9 & 10 | Motivation | Semler/Jobs, Four Drives model, intrinsic vs extrinsic | 5 Feb 2026 |
| 11 & 12 | Feedback | Set-Up-to-Fail, self-fulfilling prophecy, growth mindset | 12 Feb 2026 |
| 13 & 14 | Leadership | Hogan & Kaiser, dark side of personality, 50% manager failure | 14 Feb 2026 |

## Tab 1: Session View (Hero View)

When the user selects a session (horizontal pills/tabs for all 7), show:

### Session Header
- Title: "Sessions 5 & 6 - Leading Diverse Teams"
- Date, total contributions, active/silent student counts
- Quick stat pills: "34 contributions - 12 students active - 58 silent"

### Session Summary
3-4 sentence AI-generated summary of what happened. Example for Session 5&6:
> "Apollo 13 crisis case examined through the lens of superordinate goals and team cohesion under pressure. Marwan Sinaceur challenged Section D to identify when Kranz's leadership shifts from directive to empowering. Nick Colbourne argued Kranz was 'giving them work to distract them' - professor built the next segment around this. Voice transmission research (70% of emotional cues via voice alone) connected to remote team dynamics."

### Seating Plan Heatmap
A visual representation of the amphitheatre classroom:
- Row 1 (front): 22 seats
- Row 2: 18 seats
- Row 3: 16 seats
- Row 4 (back): 14 seats

Each seat is a small cell (~40x32px) showing student initials. Colour-coded by this session's participation:
- **Gold** (#d4a843): High-quality contribution (professor built on it)
- **Warm amber** (rgba(212,168,67,0.4)): Contributed, moderate quality
- **Dim** (rgba(212,168,67,0.15)): Contributed once, low quality
- **Dark grey** (#1a1a1a): Silent

Hover shows full name + contribution count. Click opens profile card.

### Session Leaderboard
Horizontal bar chart showing this session's contributors only (typically 10-15 students per session). Each row:
- Rank number (gold for top 3)
- Student name
- Dual bars: outer grey bar (total contributions) + inner coloured bar (quality/validated contributions)
- Predicted GPA on the right
- Clickable to open profile card

### Key Moments
2-3 highlighted contributions from this session. Each shows:
- Student name and photo
- Direct quote
- Professor's response
- Tag: "Framework challenge" / "Professor built on this" / "Reframed the discussion"

## Tab 2: Section Overview

All 70 students in a sortable leaderboard:
- Columns: rank, name, row, predicted GPA, total contributions, quality score, trend arrow (up/down/flat)
- Top 15 as horizontal bars (like the session view), rest as compact table rows
- Sort options: GPA, frequency, quality, improvement rate
- Alert banner: "12 students haven't contributed in 3+ sessions" (clickable to see who)

## Tab 3: Trends

Simple line/area charts (can use canvas or SVG, no external libraries):
- Total contributions per session (bar chart)
- Unique speakers per session (line)
- Top 5 students' cumulative contribution trajectories (multi-line)

## Student Profile Card (Modal)

Triggered by clicking any student name. Shows:

**Header**: Circular photo + Rank #X of 70 + Name + Background (company, nationality)

**Headline**: Archetype label in gold italic (e.g., "The Reframer", "The Framework Challenger")

**Quote**: Direct quote from transcripts, left-bordered, italicised

**Assessment**: 2-3 sentence qualitative assessment

**6 Assessment Dimensions** (scored 1-5, shown as filled/unfilled dots):
1. Curiosity - genuine questions, exploration beyond the obvious
2. Depth - analytical elevation, mechanisms-level thinking
3. Frequency - how often they contribute
4. Precision - hit rate, well-targeted contributions
5. Courage - challenging frameworks, intellectual risk-taking
6. Elevation - lifting discussion, professors building on their points

**Traits**: 3-4 tag pills (e.g., "Structured", "Mechanisms-level", "Framework builder")

**Stats**: Predicted GPA | Actual GPA | Accuracy %

**Session Sparkline**: Mini bar chart showing their contributions across all 7 sessions

Close on: click outside, X button, Escape key.

## The 70 Students (Section D)

### Seating Plan
Row 1 (front, 22 seats):
1. Wagner De Oliveira Filho, 2. Isabella Isotta, 3. Emmanuel Franco, 4. Gabi Klein, 5. Raphael Barata Pasqualetto, 6. Javier Del Rio Torres, 7. Katie Anderson, 8. Joon Kim, 9. Vivek Singh, 10. Xenia Postnikova, 11. Francesco Danovi, 12. Mehdi El Ayachi, 13. Eva Sinha, 14. Guillermo Krauch, 15. Saurabh Bhatia, 16. Nichamon Damrongkitkarn, 17. Raphaell Henry, 18. Alba Wang, 19. Callum Bartlett, 20. Karim Hafez, 21. Lais Victoria Ometto, 22. Andrew Bauer

Row 2 (18 seats):
23. Gim Chuan Ong, 24. Madeleine Kelly, 25. Armand Goze, 26. Michelle Baaklini, 27. Chetanand Ramakrishnan, 28. Sandeep Lakshmipathy, 29. Julien Trehet, 30. Raja Makhlouf, 31. Sander Goudriaan, 32. Justin Uffelman, 33. Zoe Barbier-Mueller, 34. Alejandro Michel Marron, 35. Jessica Dill, 36. Jozef Tanzer, 37. Nick Colbourne, 38. Arushi Tewari, 39. Navya Pathak, 40. Freddie Chambers

Row 3 (16 seats):
41. Omar Chemaly, 42. Lilian Guan, 43. Nassib Abou Nader, 44. Tanya Saharya, 45. Lars Ballhausen, 46. Jeff Neukomm, 47. Mya Ojogwu, 48. Alan Schilis, 49. Habib Baladi, 50. Emma Teisen, 51. Gonzalo Salazar, 52. Jasmine Tsai, 53. Chris Johnson, 54. Felix Fotso Kuate, 55. Estefania Esbalie, 56. Andrew Rogozinski

Row 4 (back, 14 seats):
57. Nadir Omar, 58. Marta Villagran Prieto, 59. Eliel Rosenkranz, 60. Claire Maybank, 61. Baron Sudharta, 62. Fatima Dashe, 63. Oussama Obeid, 64. Bhaskar Venkatraman, 65. Sabine Rihan, 66. Thomas Mulwa, 67. Lina Brandao Morao Lima, 68. Vernes Rasidkadic, 69. Yara Bou Maachar, 70. Felix Schinkovits

### Students with Real Contribution Data (from transcript analysis)

These students have actual contributions recorded across 25+ lecture transcripts. Use this data to build their profiles, GPA predictions, and dimension scores.

**Tier 1 - The Sharpest:**

1. **Chris Johnson** (Bain, British) - Total: 24, Validated: 17, Predicted GPA: 3.8, Actual: 3.7
   - "The Reframer" - Consistently reframes questions at mechanism level. Professors use his contributions as launching pads.
   - Quote: "I think the point is to signal that they're an innovative company... and that cascades down, so I perceive Nike as being this great brand."
   - Negotiation: argued rule-following is Kantian ethics. Professor: "Very good."
   - Strategy: Distinguished tacit vs institutionalised knowledge at Bain.
   - Scores: Curiosity 5, Depth 5, Frequency 4, Precision 5, Courage 4, Elevation 5

2. **Vernes Rasidkadic** (UniCredit, Bosnian) - Total: 2, Validated: 2, Predicted GPA: 3.5, Actual: 3.4
   - "The Industry Expert" - Single most commercially deep answer in any transcript.
   - Quote: "There's friction to change... inertia by the customers... a degree of trust... in COVID, there was a lot of flight to safety."
   - Turned banking experience into generalised principle about ecosystem lock-in. Professor built 3 follow-up questions from his answer.
   - Scores: Curiosity 4, Depth 5, Frequency 1, Precision 5, Courage 3, Elevation 5

3. **Nick Colbourne** (EY, Belgian/British/Canadian) - Total: 16, Validated: 12, Predicted GPA: 3.6, Actual: 3.5
   - "The Framework Challenger" - Questions the model itself, not just applies it.
   - Quote: "That assumes people aren't gonna want to pay in the middle... Surely there's people competing in the middle."
   - Called BS on McKinsey's $8 trillion AI estimate. Identified boundary between uncertainty types.
   - Scores: Curiosity 5, Depth 4, Frequency 3, Precision 4, Courage 5, Elevation 4

**Tier 2 - Strong:**

4. **Raphael Barata Pasqualetto** (AI Alliance, Brazilian/Portuguese) - Total: 6, Validated: 5, Predicted GPA: 3.3, Actual: 3.4
   - Only student to give mathematically correct birthday probability calculation.
   - Electoral College insight: "Small differences can add up to large differences."

5. **Guillermo Krauch** (Bain Brasil, German-Paraguayan) - Total: 8, Validated: 7, Predicted GPA: 3.5, Actual: 3.6
   - "The Economist" - Micro-economic reasoning when others pattern-match.
   - Quote: "If there was perfect competition, you would be basically at cost level."
   - Scores: Curiosity 4, Depth 5, Frequency 2, Precision 5, Courage 3, Elevation 4

6. **Sander Goudriaan** (BCG, Belgian/Dutch) - Total: 3, Validated: 3, Predicted GPA: 3.6, Actual: 3.5
   - "The Analyst" - Most analytically complete single answer across all transcripts.
   - Connected Amazon's scale to data advantages enabling customer intimacy.
   - Scores: Curiosity 4, Depth 5, Frequency 1, Precision 5, Courage 3, Elevation 5

7. **Freddie Chambers** (WPP, Barbadian/British) - Total: 8, Validated: 5, Predicted GPA: 3.2, Actual: 3.3
   - Active, commercially grounded. Professor: "What you said, Freddie, makes full sense."
   - Tactical/applied perspective rather than framework-building.

8. **Andrew Rogozinski** (Five Rings Capital, American) - Total: 4, Validated: 3, Predicted GPA: 3.2, Actual: 3.1
   - Quick on the draw, correct instincts. Immediately nailed the birth month maturity effect.

**Tier 3 - Solid Participants (use these for moderate profiles):**
- Katie Anderson: Total 8, Validated 5, GPA 3.0/3.1 - Frequent, cross-domain
- Eva Sinha: Total 11, Validated 7, GPA 3.3/3.2 - "even more poetic than what professor was looking for"
- Justin Uffelman: Total 6, Validated 5, GPA 3.3/3.2 - 83% hit rate, remarkably efficient
- Jessica Dill: Total 12, Validated 7, GPA 3.0/3.1 - Process-oriented, textbook correct
- Andrew Bauer: Total 30, Validated 12, GPA 2.8/2.9 - Highest volume, low hit rate
- Felix Fotso Kuate: Total 17, Validated 10, GPA 3.1/3.0 - Versatile, steady
- Francesco Danovi: Total 4, Validated 2, GPA 2.9/3.0 - Competent presentations
- Raja Makhlouf: Total 3, Validated 1, GPA 2.8/2.7 - Surface-level culture answers
- Jasmine Tsai: Total 3, Validated 2, GPA 2.9/2.8 - Solid recall
- Tanya Saharya: Total 2, Validated 1, GPA 2.8/2.9 - Process design instinct
- Eliel Rosenkranz: Total 2, Validated 1, GPA 2.8/2.9 - "The market is not ready to pay for it"
- Lina Brandao Morao Lima: Total 2, Validated 1, GPA 2.7/2.8

**Tier 4 - Surface Level:**
- Vivek Singh: Total 3, Validated 0, GPA 2.5/2.4 - Notably vague about Amazon despite working there
- Karim Hafez: Total 4, Validated 0, GPA 2.5/2.6 - Bet 50 euros on birthday problem. Lost.
- Lilian Guan: Total 2, Validated 0, GPA 2.5/2.6 - Garbled, no analytical depth

**Other students with some data:**
- Michelle Baaklini: Total 4, Validated 2, GPA 2.7/2.8
- Thomas Mulwa: Total 6, Validated 3, GPA 2.9/2.8 - Late bloomer
- Gonzalo Salazar: Total 5, Validated 4, GPA 3.2/3.3 - Late bloomer, 80% hit rate
- Lars Ballhausen: Total 3, Validated 2, GPA 2.9/3.0
- Fatima Dashe: Total 4, Validated 3, GPA 3.1/3.0
- Xenia Postnikova: Total 2, Validated 2, GPA 3.0/3.1
- Claire Maybank: Total 1, Validated 1, GPA 3.2/3.1 - One contribution, professor referenced 3 times
- Wagner De Oliveira Filho: Total 2, Validated 1, GPA 2.7/2.6
- Alan Schilis: Total 2, Validated 1, GPA 2.6/2.7

### Students Without Data (~38 students)

Generate plausible low-to-moderate participation data for the remaining students. Guidelines:
- Front row students slightly more active than back row (realistic pattern)
- ~10 get 2-4 total contributions across all 7 sessions (moderate)
- ~12 get 1 contribution (minimal)
- ~16 get 0 contributions (silent - show them in heatmap as grey)
- Predicted GPAs should cluster around the 2.5-3.1 range (mean 3.0 on INSEAD's scale)
- Give them generic but plausible profiles: "No recorded contributions in this period" or brief assessments based on their participation level

## GPA System

INSEAD uses a 0-5 scale with forced Z-curve distribution, mean 3.0:
- 3.5+ = Dean's List territory (top 10%), highlight in gold
- 3.0 = exactly average
- 2.1 = minimum to graduate
- Predicted GPAs should be within 0.1-0.2 of actual GPAs (shows the system works)

## Key Patterns to Surface

1. **Consulting alumni dominate** (Bain, BCG, EY) - structured thinking training shows
2. **Industry experience only valuable when elevated** - Vernes turned banking into strategy; Vivek gave vague Amazon answers
3. **Best contributions challenge the framework**, not just apply it
4. **Frequency doesn't equal quality** - Andrew Bauer has 30 contributions but 40% hit rate; Sander has 3 but 100%
5. **Front row is more active** than back row (spatial pattern visible in heatmap)

## Session-Specific Key Moments

**Sessions 1 & 2 - Negotiation:**
- Chris Johnson: "If you're asking others to follow rules, you should demonstrate the same behaviour." Professor: "Very good." Tag: "Kantian ethics connection"
- Freddie Chambers: Contribution on negotiation strategy. Professor: "What you said, Freddie, makes full sense." Tag: "Professor validated"

**Sessions 3 & 4 - Group Decision-Making:**
- Nick Colbourne: "Isn't it kind of like every time something is so new, we have to collect data over time?" Professor: "A good way to think about it." Tag: "Philosophical insight"
- Francesco Danovi: Suggested voting before discussion. Professor: noted ethical implications. Tag: "Tactically interesting"

**Sessions 5 & 6 - Leading Diverse Teams:**
- Nick Colbourne: Argued Kranz was "giving them work to distract them." Professor built the next segment around it. Tag: "Professor built on this"
- Chris Johnson: Connected team contract principles to crisis leadership. Tag: "Framework application"

**Sessions 7 & 8 - Power & Politics:**
- Guillermo Krauch: Applied game theory to coalition dynamics. Tag: "Economics-grounded"

**Sessions 9 & 10 - Motivation:**
- Eva Sinha: "IKEA's enemy is individualism." Professor: "Even more poetic than what I was looking for." Tag: "Creative reframe"
- Chris Johnson: Connected Four Drives model to Bain's talent retention. Tag: "Professional insight"

**Sessions 11 & 12 - Feedback:**
- Nick Colbourne: Role-play became teaching moment on "illusion of transparency." Tag: "Became the case study"
- Jessica Dill: "Focus on the data, have a process." Tag: "Process-oriented"

**Sessions 13 & 14 - Leadership:**
- Chris Johnson: Final contribution that cemented #1 position. Tag: "Consistent excellence"
- Eliel Rosenkranz: "The market is not ready to pay for it." Honest, grounded. Tag: "Market reality check"

## What Makes This a Good Demo

1. **The seating heatmap** is the visual wow - instantly shows who's speaking and where they sit
2. **Real quotes and professor reactions** make it feel authentic, not generated
3. **The predicted vs actual GPA** proves the system works (97%+ accuracy)
4. **The longitudinal story** (7 sessions) shows development over time
5. **70 students including silent ones** shows the scale of the assessment challenge
6. **The section selector** (A/B/C/D/E) implies this scales across the whole school

## Technical Notes

- Use Google Fonts CDN for JetBrains Mono and DM Sans
- No external JS libraries - vanilla JS only
- Seating heatmap can use CSS grid or flexbox
- Charts can use canvas or SVG (no Chart.js etc.)
- All data embedded in the JS - no API calls
- File should be self-contained and work when opened directly in a browser
- Target: looks great at 1440x900 resolution (laptop screen for demo)

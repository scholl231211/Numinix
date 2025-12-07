# Numinix — Project Description

## One-line Summary
Numinix is an intelligent, adaptive mathematics learning platform that combines short adaptive diagnostics, prioritized personalized learning roadmaps, gamified practice, and visual progress intelligence to help students (Class 1–12) efficiently discover and close gaps in their mathematical knowledge.

## Executive Summary
Numinix is a web-first education platform designed to rapidly diagnose a learner's strengths and weaknesses in mathematics, identify topic-level misconceptions, and recommend targeted practice. It pairs an adaptive diagnostic engine with a prerequisite-aware recommendation engine, engaging practice modules (timed drills, games, puzzles), and a progress intelligence dashboard. Intended for classroom use, pilots, and public demonstrations, Numinix supports anonymous demo sessions and offline-first operation to work reliably in low-connectivity settings.

## Problem Statement
- Mathematics learning is cumulative; gaps in foundational concepts result in persistent struggles.
- Traditional assessments can be time-consuming, non-adaptive, and do not provide the granular diagnostic detail needed for individualized remediation.
- Teachers have limited capacity to diagnose and personalize learning for each student in large classes.

## Project Objectives
- Rapidly diagnose topic-level mastery and misconceptions in short adaptive assessments (typically 5–8 minutes).
- Generate prioritized and actionable learning roadmaps that respect prerequisite relationships.
- Deliver engaging and adaptive practice experiences that scaffold learning and build fluency.
- Provide clear, interpretable progress reports for students and teachers.
- Maintain privacy for demo participants and support offline operation during exhibitions.

## Core Systems
### Diagnostic Engine
An adaptive item-selection engine that uses student responses and error-pattern analysis to infer misconceptions and estimate mastery. The engine focuses on high-information items to minimize test length while maximizing diagnostic value.

### Recommendation Engine
A module that maps diagnostic output to ordered learning steps. It uses a dependency graph of topics and prioritizes interventions that unblock downstream learning, considering student readiness (zone of proximal development).

### Practice & Activity Modules
A set of learning activities including:
- Timed fluency drills
- Untimed conceptual practice
- Gamified puzzles (e.g., Sudoku-style number puzzles, target-number challenges)
- Scaffolded hints and worked examples
These modules adapt difficulty and content based on mastery estimates.

### Progress Intelligence
Continuous tracking and aggregation of performance signals to produce:
- Topic-level mastery estimates
- Accuracy and response-time trends
- Engagement metrics (time on task, sessions)
- Learning velocity and confidence scores
Dashboards present this information for students, teachers, and administrators.

## How the Adaptive Diagnostic Works (Lay Explanation)
1. The test begins with medium-difficulty questions across a chapter.
2. Each response is evaluated for correctness and error type.
3. The engine selects subsequent questions to probe uncertain topics or confirm suspected misconceptions.
4. The test converges quickly on topic-level mastery estimates and provides confidence scores.

## Data Model (Summary)
- Primary records captured per response: questionId, topicId, timestamp, response, correctness, responseTime, inferredErrorType, sessionId, userId (optional).
- Derived metrics: topicMastery, accuracy, learningVelocity, confidence.
- Storage strategy: demo mode uses local session store; production deployments can optionally use encrypted server-side storage (e.g., Supabase-compatible).

## Privacy and Security
- Demo mode: anonymous session IDs, no collection of personally identifying information by default.
- Minimal data collection for demos (responses, timestamps, topic IDs).
- Offline-first behavior: data can stay local during an exhibition and sync to a secure backend only when explicitly enabled.
- For deployments: use HTTPS/TLS for transport, encryption at rest, and export/delete workflows for classroom governance.

## User Flow for Demonstrations (10–20 minutes)
1. Setup: Device(s) with a modern browser (Chrome/Edge/Firefox). Optionally project to a screen.
2. Intro (1–2 minutes): Explain demo purpose and anonymous session ID process.
3. Diagnostic (5–8 minutes): Participant completes the adaptive assessment (15–25 items typical).
4. Results (1 minute): Show mastery profile, confidence, and identified misconceptions.
5. Roadmap & Practice (5–10 minutes): Demonstrate a recommended practice activity or game.
6. Wrap-up (1–2 minutes): Show dashboard trends and suggest next steps.

## Key Features
- Adaptive, error-pattern-aware diagnostics
- Prioritized learning roadmaps with prerequisite handling
- Multiple practice modes and scaffolded supports
- Gamification to increase engagement
- Offline-first and anonymous demo modes for exhibitions
- Exportable reports and teacher-friendly dashboards

## Technical Stack (High Level)
- Frontend: React + TypeScript, built with Vite
- Styling: Tailwind CSS
- Math rendering: KaTeX / react-markdown
- Local/offline services: client-side cache and sync layer
- Optional backend: lightweight REST API or Supabase-compatible services for persistence, auth, and analytics
- Packaging: Electron or Capacitor options for desktop/mobile distribution

## Important Repo Files to Reference (for technical visitors)
- `package.json` — scripts and dependencies
- `src/App.tsx` — app shell, routing, and global providers
- `src/components/DiagnosticTest/` — diagnostic user interface
- `src/components/MathMap/` — chapter map and roadmap modal
- `src/services/diagnosticService.ts` — diagnostic generation and selection logic
- `src/services/progressTrackingService.ts` — persistence and analytics calls

## Evaluation Metrics and Research Questions
- Diagnostic completion rate during events
- Learning gain: pre/post comparisons or immediate post-practice improvement
- Engagement measures: time on task, session counts, game completions
- Teacher utility: time saved on screening, targeted interventions started

## Booth Setup Recommendations
- Devices: minimum 1 laptop; recommended 2–3 devices for throughput
- Optional: projector or large monitor for group demonstrations
- Power: access to mains power
- Assistants: 1 volunteer per 6 devices recommended
- Pre-create anonymous session IDs to expedite onboarding

## Typical Visitor Questions (and short answers)
- Q: How is the diagnostic adaptive?
  - A: It chooses subsequent items based on correctness and error patterns to focus on uncertain topics and misconceptions.
- Q: How long does the diagnostic take?
  - A: Typically 5–8 minutes (15–25 items), depending on the difficulty of items and responses.
- Q: Can it work without the internet?
  - A: Yes — demo and practice modules work offline and sync later.
- Q: What about student privacy?
  - A: Demos use anonymous session IDs; production deployments can enable encryption and consent workflows.
- Q: Can teachers use it for a whole class?
  - A: Yes — class dashboards, aggregated reports, and exports are available for teacher workflows.

## Future Work and Extensions
- Teacher dashboard with class planning and assignment workflows
- Offline-first packaged app with richer local analytics and sync
- Multimedia worked solutions and narrated explanations
- Multi-language support and expanded curriculum coverage
- LMS integrations and single sign-on for institutional deployments

## One-page Abstract (150–200 words)
Numinix is a browser-first adaptive mathematics learning platform that identifies students' topic-level strengths and misconceptions in short, efficient assessments and generates prioritized learning roadmaps. By combining an adaptive diagnostic engine, prerequisite-aware recommendation algorithms, and a suite of scaffolded practice activities and games, Numinix aims to make diagnosis and remediation fast, actionable, and engaging. The platform presents clear visual dashboards for students and teachers, tracking mastery, accuracy trends, engagement, and learning velocity. Designed with exhibitions and classroom pilots in mind, Numinix supports anonymous demo sessions and offline operation so the core experience works reliably even without continuous internet access. Diagnostics adapt in real time using correctness and error-pattern analysis to select high-information items, enabling accurate recommendations within 5–8 minutes. Practice modules include timed drills and game-like puzzles that build fluency and conceptual understanding. For privacy, demo sessions avoid collecting personal identifiers by default; production deployments can enable encrypted storage and consented data retention for classroom use. Numinix is built using modern web technologies (React + TypeScript) and can be packaged for desktop or mobile when needed.

## How to Use This File
- Use this markdown as a source for handouts, the exhibition website, or as input to an AI agent that generates a PPTX. If you want, I can also generate a `.docx` file from this content or produce a 1-page printable handout in PDF.

---

*File created: Numix_Project_Description.md*

## Technology Details (Dependencies, Scripts, Build & Deployment)

This section lists the concrete technologies and commands used in the project and provides practical notes for local development, packaging, and deployment.

### Key Dependencies (from `package.json`)
- Frontend core: `react` (v18.x), `react-dom` — main UI library.
- Build & Dev: `vite` (v7.x) and `@vitejs/plugin-react` — fast dev server and bundler.
- Types: `typescript` and `@types/*` packages for static typing in React.
- Styling: `tailwindcss`, `postcss`, `autoprefixer`.
- UI/animation: `framer-motion`, `lucide-react` (icons).
- Math rendering: `katex`, `react-markdown`, `rehype-katex`, `remark-math`.
- Backend & integrations: `express`, `cors`, `dotenv`, `node-fetch` (for proxy/API tasks).
- Storage & auth: `@supabase/supabase-js` and `supabase` packages for optional backend services.
- AI/Content: `groq-sdk` and a local `groqProxy.js` to mediate calls to external AI/content services.
- Packaging: `electron` and `@capacitor/*` packages for desktop and mobile packaging.
- Deployment helpers: `gh-pages` for GitHub Pages deploys and `concurrently` for running parallel dev workflows.

### Dev Scripts (from `package.json`)
- `npm run dev` — starts the Vite dev server.
- `npm run build` — builds the production bundle into `dist/`.
- `npm run preview` — runs a local preview of the production build.
- `npm run groq-proxy` — runs `groqProxy.js`, a node proxy used during local development to access GROQ/OpenAI/Gemini APIs.
- `npm run dev:full` — runs both the groq-proxy and the dev server concurrently (useful for full local development).
- `npm run deploy` — builds and deploys `dist/` to GitHub Pages using `gh-pages`.
- `npm run electron` — launch the Electron app (if configured) for desktop packaging/testing.

### Environment Variables and Configuration
Typical environment variables used (stored in `.env` for local dev, not committed):
- `VITE_SUPABASE_URL` — Supabase project URL (optional)
- `VITE_SUPABASE_ANON_KEY` — Supabase anon/public key (optional)
- `GROQ_API_KEY` — API key used by `groqProxy.js` to access external AI/content services
- `NODE_ENV` — development or production

Keep secrets out of the repo. Use `.env` for local development and a secrets manager (or GitHub Actions secrets) for CI/CD.

### Packaging & Distribution
- Desktop: Electron builds are supported — the `build` block in `package.json` configures `appId` and Windows NSIS target. Use `electron-builder` or the `electron` script for testing locally.
- Mobile: Capacitor is included for Android packaging — run Capacitor CLI to generate native projects and build with Android tooling.
- Web: Deploy static `dist/` to GitHub Pages, Netlify, Vercel, or a simple static host.

### Backend & API Notes
- `groqProxy.js` is present to proxy and safeguard API keys for AI integrations (OpenAI/Gemini/GROQ). During local dev, run the proxy to avoid exposing keys to the browser.
- Optional use of Supabase: authentication, Postgres, and storage can be used for production deployments. The app currently imports `@supabase/supabase-js` and includes a `lib/supabase.ts` client.

### Recommended Local Dev Workflow
1. Copy `.env.example` to `.env` and fill required keys (FILL only non-sensitive testing keys if needed).
2. Install dependencies: `npm install`.
3. Start full dev environment (proxy + vite): `npm run dev:full`.
4. Open `http://localhost:5173` (or the port Vite reports) and test UI flows.
5. Run lint: `npm run lint` and fix warnings as needed.

### CI/CD and Deployment Suggestions
- Build pipeline should run `npm ci` (or `npm install`), `npm run build`, then publish `dist/` to the desired host.
- Use GitHub Actions to run tests, linters, and build steps; use encrypted secrets to provide `GROQ_API_KEY` or Supabase credentials during build/time-of-deploy.

### Notes on Third-party Integrations and Limitations
- AI content generation: treat generated content as assistance. Always provide human review for correctness, especially for math solutions.
- Supabase usage: anonymous keys in client are for public access to per-project resources; production systems should enforce row-level security and server-side protections.

---

*Technology details appended.*

## Vast Detailed Explanation (Technical + Pedagogical)

This section provides a deep, structured explanation suitable for developers, educators, and reviewers who want to understand the internal design, algorithms, data schemas, and deployment plans for Numinix. Use these details as a reference for implementation, evaluation, or to inform an AI agent that will transform this content into slides, code examples, or documentation.

### Pedagogical Basis and Learning Theory
- Spaced practice and interleaving: Practice activities are scheduled and mixed across topics to improve retention.
- Diagnostic-prescribed practice: The diagnostic identifies specific misconceptions; practice tasks directly target those misconceptions (worked examples followed by practice to encourage transfer).
- Zone of Proximal Development (ZPD): Recommendations preferentially choose tasks that are slightly above current mastery to promote growth without excessive frustration.
- Retrieval practice: Timed fluency drills emphasize retrieval and speed to build automaticity.

### Algorithmic Overview

1. Mastery Estimation
- Each topic t for a student s has a mastery score M_{s,t} in [0,1]. Initialize M_{s,t} to a prior based on grade level or population statistics if available.
- After each response r to question q (tagged with topic t), update using an exponential smoothing rule:

  mastery_new = alpha * performance_recent + (1 - alpha) * mastery_old

  - performance_recent is 1 for correct, 0 for incorrect, optionally scaled by response time or rubric score.
  - alpha is a smoothing parameter (typical 0.2–0.4).

2. Item Selection (Adaptive Diagnostic)
- Maintain a set of candidate items per topic with difficulty d_q and discrimination parameters.
- Use an information-gain heuristic: estimate expected reduction in entropy over topic mastery if item q is presented, and greedily select the item with maximal expected utility.

Pseudocode (simplified):

```
function select_next_item(student, candidate_pool):
  best = null
  best_score = -inf
  for q in candidate_pool:
    expected_gain = compute_expected_information_gain(student, q)
    if expected_gain > best_score:
      best = q
      best_score = expected_gain
  return best
```

3. Recommendation / Roadmap Generation
- Build a directed acyclic graph of topic prerequisites.
- Score topics by impact = (prerequisite_weight * downstream_unblocked) * (1 - M_{s,t})
- Select top-K topics and produce a sequence that respects dependencies and mixes fluency/transfer activities.

4. Confidence and Stopping Criteria
- Track posterior variance or entropy of mastery estimates; stop when variance falls below threshold or when maximum question count is reached.

### Data Schemas

Simplified JSON shapes used by the app (for developer reference):

Question record:

```
{
  "id": "q_123",
  "text": "What is 7 + 8?",
  "topicId": "t_add",
  "difficulty": 0.3,
  "choices": [ ... ],
  "solution": "15",
  "metadata": {"skillTags": ["addition","numberSense"]}
}
```

Response record:

```
{
  "id": "r_456",
  "userId": "u_789",            // optional for demo
  "sessionId": "s_1011",
  "questionId": "q_123",
  "topicId": "t_add",
  "timestamp": "2025-10-15T12:34:56Z",
  "response": "15",
  "correct": true,
  "responseTimeMs": 4200,
  "inferredErrorType": null
}
```

Mastery record:

```
{
  "userId": "u_789",
  "topicId": "t_add",
  "mastery": 0.78,
  "updatedAt": "2025-10-15T12:34:56Z"
}
```

### Pseudocode for Diagnostic Flow

```
function run_diagnostic(student, chapterId):
  session = start_session(student, chapterId)
  candidates = load_candidate_items(chapterId)
  while not stopping_criteria(session):
    q = select_next_item(student, candidates)
    show_question(q)
    r = collect_response()
    record_response(r)
    update_mastery(student, r)
    remove_item_from_candidates(q)
  end
  return summarize_results(student, session)
```

### Pilot Plan (for a school or exhibition study)

- Goals: Validate diagnostic accuracy, measure immediate learning gains, estimate engagement and throughput in an exhibition setting.
- Participants: 30–100 students segmented by grade bands.
- Procedure:
  1. Pre-screen: optionally capture basic grade-level and consent.
  2. Run Numinix diagnostic (10–12 minutes max per student).
  3. Assign 10–15 minutes of targeted practice based on roadmap.
  4. Run a short post-practice assessment (5–8 items) to measure immediate gain.
  5. Collect short feedback survey (3–5 questions).
- Metrics: pre/post accuracy delta, engagement time, user satisfaction, throughput per hour.

### Consent and Short Participant Notice (Template)

Title: Numinix Demonstration — Participant Notice

We invite you to try Numinix, an adaptive mathematics learning application. Participation is voluntary. During this demonstration we will collect responses to math questions and timestamps to produce immediate personalized recommendations. No names or contact information will be collected unless you choose to provide them. If you do provide identifying information, it will be stored only with your explicit consent.

By participating you acknowledge that data collected during the session will be used in anonymized form to improve the application and for aggregate reporting. You may request deletion of your session data before leaving.

If you (or your guardian) do not consent, you may still observe the demo but not participate.

### Suggested Short Feedback Survey (3–5 questions)
- How enjoyable did you find the activity? (1–5)
- How clear were the explanations and hints? (1–5)
- Do you feel more confident on the topics after practice? (1–5)
- Would you use this tool again? (Yes/No)
- Optional: Short comment box

### Metrics Collection Plan

- Collect the following per session (anonymous by default):
  - sessionId, startTime, endTime
  - diagnostic responses (questionId, correct, responseTime)
  - roadmap topics recommended
  - practice activities completed and success rates
  - post-practice assessment responses
  - survey responses

- Analysis scripts should compute:
  - pre/post accuracy and effect sizes
  - average improvement by topic and grade
  - engagement statistics and throughput

### Deployment Checklist (Exhibition / School Pilot)

- Devices prepared and tested (browsers, power, screen mirroring if needed)
- Pre-created anonymous session ID list or QR generator
- Volunteer instructions and schedule
- Local offline cache prepared (if Wi-Fi unreliable)
- Data export plan (how to extract anonymized logs)
- Emergency data deletion procedure and privacy contact

### Risk Mitigation and Ethical Considerations

- Misclassification risk: diagnostics are screening tools — present results as guidance, not final judgments.
- Accessibility: ensure color contrast, readable fonts, and keyboard navigation.
- Data privacy: default to anonymous demos; require explicit consent for persistent storage.
- Bias: monitor item difficulty and population performance; ensure question bank covers diverse contexts and avoids cultural bias.

### Developer Handoff Notes

- Entry points: `src/App.tsx` for app shell and routing; `src/services/diagnosticService.ts` for core selection logic; `src/services/progressTrackingService.ts` for persistence.
- Testing: add unit tests for mastery updates, item-selection heuristics, and roadmap generation.
- Configuration: make thresholds (alpha, entropy_stop, max_items) configurable via environment variables.

### Example Analysis Queries (SQL-like pseudocode)

1. Average pre/post improvement by grade:

```
SELECT grade, AVG(post_accuracy - pre_accuracy) as avg_improvement
FROM session_summaries
GROUP BY grade;
```

2. Topic-level difficulty map:

```
SELECT topicId, AVG(1 - correctness) as avg_error_rate
FROM responses
GROUP BY topicId
ORDER BY avg_error_rate DESC;
```


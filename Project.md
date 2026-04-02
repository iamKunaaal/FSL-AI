# Neorise FSL — Complete Project Specification
## AI-Powered Curriculum Generator

---

# PART 1: WHAT ARE WE BUILDING?

## One Line Summary
A web app where admin enters a project topic and AI generates a complete 6-week school curriculum with 18 session plans + teaching materials (lesson plans, PPTs, worksheets).

## The Core Idea
There is a FIXED FRAMEWORK (skeleton) that never changes — it defines 6 weeks, 18 sessions, competencies, skills. When admin gives a TOPIC (like "Ethical Marketing"), AI fills this skeleton with topic-specific content. Same skeleton, different topic = different curriculum.

## Who Uses It

**Admin (Neorise curriculum team):**
- Creates new projects by entering a topic
- Triggers AI generation
- Reviews AI-generated content
- Edits/approves each session
- Generates teaching materials (Phase 2)
- Publishes final curriculum for teachers

**Teacher (School staff):**
- Views published projects only
- Browses week-by-week, session-by-session
- Reads session descriptions and activity plans
- Downloads teaching materials (Lesson Plan PDF, PPT, Worksheet)
- Read-only access — no editing

---

# PART 2: THE FRAMEWORK (Fixed Data)

This is the backbone. It comes from a CSV sheet. It gets stored in the database ONCE and never changes. Every project uses this same framework.

## 2.1 Structure

- 1 Framework contains 6 Weeks
- Each Week has a Phase name and 3 Sessions
- Each Session has a Generic Description, Period Type, and mapped Competencies
- Each Competency belongs to a Sub-Pillar and has 3 difficulty levels (LL/MM/HS)

## 2.2 The 6 Weeks

| Week | Phase | What Happens |
|------|-------|-------------|
| Week 1 | Explore | Students discover the topic, spark curiosity, discuss why it matters |
| Week 2 | Learn | Students learn core concepts, tools, systems needed for the project |
| Week 3 | Find | Students research problems, interview users, gather data, frame problem statement |
| Week 4 | Create | Students brainstorm solutions, evaluate ideas, build prototypes |
| Week 5 | Improve | Students test prototypes, gather feedback, iterate, reflect on ethics |
| Week 6 | Reflect | Students prepare presentations, pitch to audience, reflect on journey |

## 2.3 Sessions Per Week

Every week has exactly 3 sessions:

| Session Type | Duration | Purpose |
|-------------|----------|---------|
| Block Period 1 (Challenge) | ~80 minutes | Main activity, hands-on work |
| Block Period 2 (Challenge) | ~80 minutes | Deeper dive, practice, application |
| Single Period (Reflection) | ~40 minutes | Think, write, set goals, consolidate |

Total across 6 weeks: 18 sessions (12 Block Periods + 6 Reflection Periods)

## 2.4 The 18 Generic Session Descriptions

These are FIXED templates that tell AI what TYPE of activity each session should have. They are topic-agnostic — same for every project:

| Session | Week | Period | Generic Description |
|---------|------|--------|-------------------|
| 1 | Week 1 | Block 1 | Project Launch & Context Exploration — Introduce the project theme through a real-world problem, story, or scenario |
| 2 | Week 1 | Block 2 | Understanding the Challenge — Students unpack the project question, identify key ideas, explore examples |
| 3 | Week 1 | Single | Prior Knowledge & Curiosity Mapping — Students document what they already know, generate questions |
| 4 | Week 2 | Block 1 | Concept Exploration — Introduce core concepts, tools, or systems through demonstrations and guided activities |
| 5 | Week 2 | Block 2 | Case Study & Skill Practice — Students explore real-world examples and complete guided tasks |
| 6 | Week 2 | Single | Knowledge Consolidation — Students summarize key learnings through notes, diagrams, set goals |
| 7 | Week 3 | Block 1 | Problem Exploration — Students investigate problems and analyze who is affected and why it matters |
| 8 | Week 3 | Block 2 | User Research & Data Gathering — Students conduct interviews, surveys, observations |
| 9 | Week 3 | Single | Insights & Problem Framing — Students organize findings and define a clear problem statement (HMW) |
| 10 | Week 4 | Block 1 | Idea Generation Workshop — Brainstorm solutions using structured ideation, evaluate on feasibility and impact |
| 11 | Week 4 | Block 2 | Prototype Development — Teams build or design a prototype using available tools and materials |
| 12 | Week 4 | Single | Design Documentation — Students record design ideas, explain approach, plan next steps |
| 13 | Week 5 | Block 1 | Prototype Testing — Students test solutions and observe effectiveness, identify potential risks |
| 14 | Week 5 | Block 2 | Iteration & Improvement — Teams analyze feedback, identify limitations, refine prototype |
| 15 | Week 5 | Single | Impact & Responsibility Reflection — Reflect on ethical considerations, sustainability, consequences |
| 16 | Week 6 | Block 1 | Preparing the Showcase — Prepare presentations, demonstrations, visual explanations |
| 17 | Week 6 | Block 2 | Project Presentation / Pitch — Present to peers, teachers, or invited audiences |
| 18 | Week 6 | Single | Reflection & Future Connections — Reflect on learning, connect to real-world problems and future opportunities |

Plus there is a "Plug-In" entry at the end for Financial Literacy (SP6) which is an add-on module.

## 2.5 Kaushal Bodh Questions (Per Week)

Each week has guiding questions that teachers use and AI should weave into sessions:

**Week 1:** What will I be able to do? What will I need? Connecting with the world of jobs and careers. Why is this relevant?

**Week 2:** What will I need to know before I start? (Core knowledge pieces). Meet an Expert. What do I have to do? Share what we know with others. How do I keep myself and others safe?

**Week 3:** What problem around me do I want to/Can I solve? Identify User/Idea/Problem/Business. Understanding the context better and user. Identify USP, idea elements and user.

**Week 4:** What are the criteria for a good solution? Further details of your idea. Making your idea. Upgrading your idea with tech/other applications.

**Week 5:** Feedback from peers and users. Researching on how to improve idea. Applying contemporary knowledge to upgrade. Consequences and ethics.

**Week 6:** What did I learn from others, and how did I use it? What did I do, and how long did it take? Connecting with the world of jobs and careers. Reflecting on your interests and tasks. What else can I do? Presenting to others. Think and Answer — Assessment Sheet.

## 2.6 Sub-Pillars (11 NEP Skill Areas)

These are the skill categories from India's National Education Policy:

| Code | Name |
|------|------|
| SP1 | Knowing Self |
| SP2 | Building Self |
| SP4 | Data, Digital & Media Literacy |
| SP5 | Environmental & Sustainability Literacy |
| SP6 | Financial Literacy |
| SP11 | Design Thinking |
| SP12 | Entrepreneurial Mindset |
| SP13 | Global Citizenship & Cross-Culture Awareness |
| SP14 | Readiness for Future of Work & Career |
| SP15/SP16 | Smart Systems, IoT & Robotics |
| SP17 | Design & Emerging Tech (AR/VR, Drones) |

## 2.7 Competency Codes and Levels

There are 38 unique competency codes across all sessions (like MSP13.C1, MSP4.C3, MSP11.C1).

Each competency has descriptions at 3 levels:

- **LL (Lower Level)** — Foundational. Present for all 18 sessions. Example: "Recognises and appreciates similarities and differences across cultures"
- **MM (Middle Level)** — Applied/Technical. Present for ~6 sessions (mainly IoT/Robotics weeks). Example: "Identifies and connects microcontrollers to sensors to create functional circuits"
- **HS (Higher Level)** — Advanced/Analytical. Present for ~2 sessions (Digital Literacy). Example: "Select and apply appropriate digital tools to create multi-modal digital content"

## 2.8 Session-to-Competency Mapping

Each session maps to one or more sub-pillars and competency codes. For example:

- Session 1 → SP13 (Global Citizenship) → MSP13.C1
- Session 4 → SP5 (Sustainability) [LL] + SP15/SP16 (IoT/Robotics) [MM] + SP4 (Digital Literacy) [HS]
- Session 7 → SP11 (Design Thinking) → MSP11.C1
- Session 10 → SP5 [LL] + SP15/SP16 [MM] + SP4 [HS]
- Session 17 → SP12 (Entrepreneurial Mindset) → MSP12.C4

The full mapping is in the CSV file. Every session has at least one LL competency mapped.

---

# PART 3: WHAT AI GENERATES (Dynamic Data)

This is the RIGHT SIDE of the CSV — content that changes with every new project topic.

## 3.1 Phase 1 Outputs (Session Content)

For each of the 18 sessions, AI generates:

**Weekly Objective (one per week, so 6 total):**
Topic-specific learning goals for that week. Example for Week 1 of "Ethical Marketing":
- Understand how marketing influences people
- Design ethical marketing ideas for real-world products
- Awareness of digital platforms, ethics, consumer behavior, teamwork
- Roles: digital marketers, brand strategists, content creators

**Session Description (one per session, so 18 total):**
Detailed, step-by-step activity plan customized to the topic. Example for Session 1:
1. Prompt discussion: "What made you trust or distrust the ad?"
2. Group analysis: Who is affected? (consumers, parents, companies). What could go wrong? Should there be rules?
3. Student reflection: Ads they saw recently — were they Influenced, Misled, or Informed?
4. Discussion: What is ethical vs unethical? Do all communities view ads the same?
5. Written reflection: Why are marketing ethics needed? Who does it affect?

## 3.2 Phase 2 Outputs (Teaching Materials)

For each session, AI generates 3 types of materials:

| Material | Format | Purpose |
|----------|--------|---------|
| Lesson Plan | PDF | Teacher's guide — objectives, materials needed, step-by-step instructions, assessment notes |
| Session PPT | PPTX | Slides to show in classroom — visual aids, discussion prompts, key concepts |
| Worksheet | PDF | Handout for students — activities, questions, reflection spaces |

Total materials per project: 18 sessions × 3 materials = 54 files

---

# PART 4: DATABASE STRUCTURE

## Tables Needed

### Fixed Framework Tables (Seeded once from CSV):

**Framework** — Master template record
- Fields: name, description, total_weeks, sessions_per_week, is_active

**Week** — 6 rows per framework
- Fields: framework (FK), week_number (1-6), phase_name (Explore/Learn/Find/Create/Improve/Reflect), kaushal_bodh_questions (text)

**SubPillar** — 11 rows
- Fields: code (SP1, SP13, etc.), name, description

**SessionTemplate** — 18 rows per framework
- Fields: week (FK), session_number (1-18), period_type (block_1/block_2/single), challenge_number (1-12 or null), generic_description (the fixed description text), duration_minutes (80 or 40)

**CompetencyMap** — Links sessions to sub-pillars with competency details
- Fields: session_template (FK), sub_pillar (FK), competency_code (MSP13.C1), ll_description, mm_description, hs_description

### Dynamic Project Tables (Created per project):

**Project** — One row per curriculum project
- Fields: framework (FK), topic_name, grade, subject_area, additional_context, status (draft/generating_phase1/review/generating_phase2/published), ai_model, created_by (FK to User), total_tokens_used, total_cost_usd, timestamps

**ProjectSession** — 18 rows per project (one per session)
- Fields: project (FK), session_template (FK), weekly_objective (AI generated), session_description (AI generated), ai_status (pending/generating/completed/failed), is_approved, tokens_used, cost_usd, original_description (backup for "reset to original")

**GeneratedOutput** — Up to 54 rows per project (3 per session)
- Fields: project_session (FK), output_type (lesson_plan/ppt/worksheet), file (uploaded file), raw_content (AI text before file conversion), ai_status (pending/generating/completed/failed)

### User Table:

**User** — Extended Django user
- Fields: standard auth fields + role (admin/teacher), school_name, phone

---

# PART 5: APPLICATION SCREENS

## 5.1 Admin Dashboard (Home)

**URL:** /dashboard/
**Access:** Admin only
**Purpose:** Overview of all projects with stats and quick actions

**What it shows:**
- 4 stat cards: Total Projects, Published count, In Review count, Generating count
- Project table with columns: Project Name (clickable), Grade (badge), Subject Area, Status (color-coded badge), Sessions progress (X/18 with progress bar), Created Date, Actions menu
- Filters: by status, by grade, search by name
- "+ Create New Project" button (top-right, prominent)
- Pagination at bottom

**Status badge colors:**
- Draft = gray
- Generating = amber with pulse animation
- Review = blue
- Published = green
- Failed = red

## 5.2 Create New Project

**URL:** /projects/create/
**Access:** Admin only
**Purpose:** Form to create a new curriculum project

**Form fields:**
1. Project Topic (text input, required) — "e.g., Smart Ethical Marketing in Future Digital Economy"
2. Subject Area (dropdown, optional) — Human Services, Environmental Science, Digital Literacy, Commerce & Finance, Arts & Culture, STEM, Health & Wellness
3. Grade Level (radio buttons) — Grade 6, 7, 8, 9, 10
4. Framework (dropdown) — "FSL 6-Week PBL Framework (Default)" — currently only one option
5. AI Model (dropdown) — "Claude Sonnet 4 (Recommended)", "GPT-4o", "Gemini 1.5 Pro", "Llama 3.1 70B"
6. Additional Context (textarea, optional) — extra instructions for AI, max 500 chars

**Framework Preview section (expandable):**
Shows 6 weeks with phase badges and "3 sessions" each. Summary: "Total: 18 sessions | 12 Block Periods + 6 Reflection Periods"

**Action buttons:**
- Cancel → back to dashboard
- Save as Draft → saves project with status "draft", no AI generation
- Create & Generate → saves project + triggers Phase 1 AI generation → redirects to Generation Progress page

## 5.3 AI Generation Progress

**URL:** /projects/{id}/generate/
**Access:** Admin only
**Purpose:** Real-time progress view while AI generates 18 sessions

**What it shows:**
- Phase stepper: Phase 1 (Session Descriptions) = active, Phase 2 (Teaching Materials) = grayed out
- Overall progress bar: "X of 18 sessions completed — X%"
- Estimated time remaining
- Week-wise progress grid (6 columns, 3 sessions each):
  - Green check = completed
  - Amber spinner = currently generating
  - Gray = queued/pending
  - Red X = failed (with retry button)
- System log (terminal-style): timestamps, completion messages, token counts
- Cost tracker: tokens used, estimated USD cost, model name

**Action buttons:**
- Cancel Generation → stops all pending tasks, keeps completed ones
- Pause → temporarily stops
- Continue in Background → redirects to dashboard, generation continues via Celery

**When 18/18 complete:** Shows success message + "Review Sessions →" button → redirects to Project Detail

## 5.4 Project Detail (Week-wise View)

**URL:** /projects/{id}/
**Access:** Admin (full) + Teacher (read-only)
**Purpose:** Browse the complete 6-week curriculum

**What it shows:**
- Project header: title, grade badge, subject badge, status badge, created date
- Action buttons (admin only): Edit Project, Generate Materials, Publish/Unpublish
- Progress summary: "18/18 sessions generated | 18/18 approved | 54 materials generated"
- Segmented progress bar (6 segments, one per week, color-coded by status)

**Week accordion (6 sections):**
Each week expands to show 3 session cards:

Each session card shows:
- Session number + Period type badge + Status badge (Approved/Pending/Draft)
- LEFT part: AI-generated session description (truncated, expandable with "Show More")
- RIGHT part: Framework reference — Sub-pillar tag, Competency code badge, competency description
- Bottom buttons (admin only): Edit, Regenerate, Approve/Approved, View Materials

**Side panel (right):**
Weekly Objectives for the currently expanded week — sticky, stays visible while scrolling

**Left sidebar:**
Project Overview, Weekly Schedule, Frameworks, AI Insights — navigation links

## 5.5 Session Review & Edit

**URL:** /projects/{id}/sessions/{session_number}/
**Access:** Admin only
**Purpose:** Detailed view to review, edit, approve a single session

**Split-screen layout:**

**LEFT PANEL — "Framework Input" (read-only):**
What was given to AI as input:
- Generic Session Template (gray box with the fixed description text)
- Kaushal Bodh Questions (bulleted list for that week)
- Competency Mapping: Sub-pillar tag + code badge + LL/MM/HS tabs showing competency descriptions
- Period Duration: Session type + minutes

**RIGHT PANEL — "AI Generated Output" (editable by admin):**
What AI produced:
- Weekly Objective (editable text area) — with "Regenerate" button
- Session Description & Flow (editable rich text) — the main content with numbered activities, timings, discussion prompts — with "Regenerate" button + "Reset to Original" link
- Generated Materials section: 3 cards (Lesson Plan, PPT, Worksheet) — each with status, Preview, Download, Regenerate buttons. If not yet generated, shows "Generate Materials" button

**Top-right info:**
AI Model used, generation timestamp, token count

**Bottom action bar (sticky):**
- Left: ← Previous Session | "Session X of 18" | Next Session →
- Right: Save Draft, Approve Session, Approve & Next →

## 5.6 Teacher Dashboard

**URL:** /teacher/
**Access:** Teacher only
**Purpose:** Warm, simple landing page for teachers

**What it shows:**
- Welcome message with teacher name
- Published project count
- Project cards grid (2 columns): Each card shows project title, grade, subject, phase dots (6 colored dots showing weeks), resource count, last accessed, "Open Project →" button
- "This Week's Sessions" section: timeline of upcoming sessions based on schedule

## 5.7 Teacher Project View

**URL:** /teacher/projects/{id}/
**Access:** Teacher only (published projects only)
**Purpose:** Browse a curriculum week-by-week, download materials

**What it shows:**
- Week navigation tabs (6 tabs with phase colors)
- Week header: phase name, weekly objective, Kaushal Bodh questions
- 3 session cards per week:
  - Session number, period type, duration
  - Session activities (numbered steps, expandable)
  - Competency tags and levels (expandable)
  - Material download cards: Lesson Plan (PDF), Session PPT (PPTX), Worksheet (PDF) — each with download button
- "Download All Week Materials" button (ZIP)
- Week navigation: ← Previous Week | "Week X of 6" | Next Week →

---

# PART 6: AI GENERATION PIPELINE

## 6.1 How AI Generation Works

When admin clicks "Create & Generate":

1. A new Project record is created in the database with status "generating_phase1"
2. 18 ProjectSession records are created with status "pending"
3. A Celery background task is triggered
4. The task processes sessions one by one (or in batches of 3):
   - For each session, it builds a prompt using framework data + topic
   - Sends the prompt to OpenRouter API
   - Parses the response
   - Saves the generated content to the ProjectSession record
   - Updates status to "completed"
5. Frontend polls every 3-5 seconds to update the progress page
6. When all 18 complete, project status changes to "review"

## 6.2 What Goes Into Each AI Prompt

For EACH of the 18 sessions, a separate API call is made. Each call includes:

**System Prompt (same for all sessions):**
You are an expert NEP 2020-aligned curriculum designer. Design project-based learning sessions that are engaging, age-appropriate, activity-based (not lecture-based), and competency-focused. Follow Bloom's taxonomy. Include discussion prompts, student activities, and reflection points. Output in structured format.

**User Prompt (unique per session, built dynamically from database):**
- Project topic: [from Project.topic_name]
- Grade: [from Project.grade]
- Subject area: [from Project.subject_area]
- Week number and phase: [from Week.week_number, Week.phase_name]
- Period type and duration: [from SessionTemplate.period_type, duration_minutes]
- Generic session template: [from SessionTemplate.generic_description]
- Kaushal Bodh questions for this week: [from Week.kaushal_bodh_questions]
- Sub-pillar: [from CompetencyMap → SubPillar.name]
- Competency code: [from CompetencyMap.competency_code]
- LL competency description: [from CompetencyMap.ll_description]
- MM competency description: [from CompetencyMap.mm_description] (if available)
- HS competency description: [from CompetencyMap.hs_description] (if available)
- Additional context: [from Project.additional_context]
- Output format instructions: Return structured JSON with weekly_objective and session_description fields

**Example prompt for Session 1:**
"Generate a detailed session plan for:
- Topic: Smart Ethical Marketing in Future Digital Economy
- Grade: 8
- Week 1 (Explore phase)
- Period: Block Period 1 — Challenge 1 (~80 minutes)
- Generic template: Project Launch & Context Exploration — Introduce the project theme through a real-world problem, story, or scenario...
- Kaushal Bodh Questions: What will I be able to do? What will I need? Why is this relevant?
- Sub-pillar: SP13 Global Citizenship & Cross-Culture Awareness
- Competency: MSP13.C1 — Recognises and appreciates similarities and differences across cultures, identities, and communities
- Include activities suitable for LL, MM, and HS level students
- Return as JSON: {weekly_objective: '...', session_description: '...'}"

## 6.3 Phase 2 — Material Generation

After admin approves sessions and triggers Phase 2:

For each session, 3 more API calls are made:

1. **Lesson Plan prompt**: "Based on this session description [paste session_description], create a detailed teacher's lesson plan with: learning objectives, materials needed, step-by-step facilitation guide, timing breakdown, assessment notes, differentiation tips for LL/MM/HS students."

2. **PPT content prompt**: "Based on this session description, create content for a classroom presentation with: slide titles, bullet points, discussion prompts, visual suggestions, activity instructions. Format as slide-by-slide breakdown."

3. **Worksheet prompt**: "Based on this session description, create a student worksheet with: warm-up questions, main activity instructions, reflection questions, self-assessment section."

The AI text responses are then converted to actual files:
- Lesson Plan → PDF (using WeasyPrint or ReportLab)
- PPT → PPTX (using python-pptx)
- Worksheet → PDF

## 6.4 OpenRouter API Details

All AI calls go through OpenRouter which provides a unified API for multiple models:

- **Endpoint**: https://openrouter.ai/api/v1/chat/completions
- **Authentication**: Bearer token (OPENROUTER_API_KEY)
- **Model options**: anthropic/claude-sonnet-4 (recommended), openai/gpt-4o, google/gemini-1.5-pro, meta-llama/llama-3.1-70b
- **Temperature**: 0.7 (creative but consistent)
- **Max tokens**: ~4000 per session description, ~3000 per material

Admin can choose the model when creating a project. The model choice is stored in the Project record.

## 6.5 Why Celery + Redis

AI generation takes 15-30 seconds per session. For 18 sessions, that's 5-9 minutes. For Phase 2 (54 materials), that's 15-25 minutes. This CANNOT be done synchronously — the browser would time out.

**Redis** acts as a message queue — Django puts tasks in the queue.
**Celery** workers pick tasks from the queue and process them in the background.

The frontend polls the server every few seconds to get updated progress, which it displays on the Generation Progress page.

---

# PART 7: USER FLOWS

## 7.1 Admin — Create and Publish a Project

```
1. Login → Admin Dashboard
2. Click "+ Create New Project"
3. Fill form: Topic, Grade, Subject, AI Model
4. Click "Create & Generate"
5. Watch Generation Progress page (18 sessions generating)
6. All 18 complete → Click "Review Sessions"
7. Project Detail page — browse all 18 sessions
8. Click "Edit" on any session to review in detail (Session Review page)
9. Read left panel (what AI got as input) vs right panel (what AI produced)
10. Edit if needed, or click "Approve & Next"
11. Repeat for all 18 sessions
12. Back to Project Detail → Click "Generate Materials" (triggers Phase 2)
13. Watch Generation Progress again (54 materials generating)
14. Review materials — Preview, Download, Regenerate if needed
15. Click "Publish"
16. Project is now visible to teachers
```

## 7.2 Teacher — Access and Use Curriculum

```
1. Login → Teacher Dashboard
2. See published projects as cards
3. Click "Open Project" on a project card
4. Teacher Project View — see Week 1 tab by default
5. Read weekly objective
6. Browse 3 session cards with activity details
7. Download Lesson Plan PDF, Session PPT, Worksheet for each session
8. Or click "Download All Week Materials" for ZIP
9. Navigate to Week 2, 3... using tabs
10. Use materials in classroom
```

## 7.3 Admin — Edit and Regenerate

```
1. Open any project → Project Detail page
2. Click "Edit" on a session
3. Session Review page opens (split view)
4. Option A: Edit text directly in right panel → Save Draft → Approve
5. Option B: Click "Regenerate" → AI generates new content → Review → Approve
6. Option C: Click "Reset to Original" → reverts to first AI generation
7. For materials: Click "Regenerate" on individual Lesson Plan/PPT/Worksheet
```

---

# PART 8: STATUS LIFECYCLE

## Project Status Flow

```
Draft → Generating Phase 1 → Review → Generating Phase 2 → Published
```

- **Draft**: Project created but no AI generation triggered yet
- **Generating Phase 1**: AI is generating 18 session descriptions (Celery working)
- **Review**: All 18 sessions generated, admin is reviewing/editing/approving
- **Generating Phase 2**: AI is generating teaching materials — lesson plans, PPTs, worksheets (Celery working)
- **Published**: Everything approved and ready, visible to teachers

## Session Status Flow

```
Pending → Generating → Completed → Approved
                    ↘ Failed (can retry)
```

## Material Status Flow

```
Pending → Generating → Completed
                    ↘ Failed (can retry)
```

---

# PART 9: ASSESSMENT (No Exams)

The FSL framework uses continuous, competency-based assessment — NOT traditional exams.

**How teachers assess students:**

- **Week 1-2 (Explore + Learn)**: Teacher observes — who is participating in discussions? Who is thinking critically? Evidence: discussion responses, curiosity questions, mind maps, charts
- **Week 3 (Find)**: Quality of research — interview questions, data collection, HMW problem statement quality
- **Week 4 (Create)**: Quality of prototype — idea evaluation, design process, portfolio documentation
- **Week 5 (Improve)**: Ability to receive and act on feedback — testing checklist, revised prototype, ethical reflection
- **Week 6 (Reflect)**: Final presentation quality, peer feedback, "Think and Answer" assessment sheet, journey reflection

**Final output**: Teacher determines each student's level (LL/MM/HS) for each competency. This becomes the competency report card.

---

# PART 10: TECH STACK

| Component | Technology | Purpose |
|-----------|-----------|---------|
| Backend | Django 5.x | Web framework, views, auth, ORM |
| Database | PostgreSQL | Store all framework + project data |
| Task Queue | Celery | Background AI generation tasks |
| Message Broker | Redis | Queue for Celery tasks |
| AI API | OpenRouter | Unified access to Claude/GPT/Gemini/Llama |
| Frontend | Django Templates | Server-rendered HTML pages |
| Styling | Tailwind CSS | Utility-first CSS framework |
| Interactivity | Alpine.js | Accordions, modals, dropdowns, toggles |
| Partial Updates | HTMX | Update parts of page without full reload (progress polling) |
| PPT Generation | python-pptx | Create PowerPoint files from AI content |
| PDF Generation | WeasyPrint or ReportLab | Create PDF lesson plans and worksheets |
| File Storage | Django Media / S3 | Store generated files |

---

# PART 11: IMPORTANT NOTES

1. **Subject Area is NOT in the CSV** — it is entered by admin in the project creation form. The CSV only mentions "Human Services (Grade 8)" in a column header as a label for that specific example.

2. **Grade is NOT in the CSV** — same as subject, it's admin input.

3. **The CSV is a COMPLETE EXAMPLE** — both left side (framework) and right side (generated content for "Ethical Marketing") are filled in. We use the left side as seed data and the right side as reference for what AI should produce.

4. **LL column is fully filled, MM and HS are sparse** — MM competencies exist only for IoT/Robotics sessions, HS only for Digital Literacy. This may be intentional (different tracks) or incomplete (to be filled later by Neorise).

5. **One framework currently** — "FSL 6-Week PBL Framework". The system should be designed to support multiple frameworks in future (e.g., "FSL 4-Week Mini Project").

6. **Phase 1 and Phase 2 are sequential** — Admin must review and approve Phase 1 (session descriptions) before triggering Phase 2 (materials). This is by design — materials are generated BASED ON the approved session descriptions.

7. **Each AI call is independent** — Session 5's generation does not depend on Session 4's output. They can technically be parallelized (batches of 3), but the weekly objective should be generated once per week and shared across 3 sessions.

8. **Regeneration replaces content** — When admin clicks "Regenerate" on a session, the old content is overwritten. The "original_description" field stores the first generation for "Reset to Original" functionality.

---

# PART 12: CSV COLUMN MAPPING TO DATABASE

For reference, here's exactly how the CSV columns map to database tables:

| CSV Column | Column Name | Stored In | Field Name |
|-----------|-------------|-----------|------------|
| Col 0 | Week | Week table | week_number, phase_name |
| Col 1 | Kaushal Bodh Questions Integrated | Week table | kaushal_bodh_questions |
| Col 2 | Sub-Pillar Anchoring | SubPillar table | code, name |
| Col 3 | Competencies | CompetencyMap table | competency_code |
| Col 4 | LL: Competencies | CompetencyMap table | ll_description |
| Col 5 | MM Competencies | CompetencyMap table | mm_description |
| Col 6 | HS Competencies | CompetencyMap table | hs_description |
| Col 7 | Session Description | SessionTemplate table | generic_description |
| Col 8 | Period | SessionTemplate table | period_type, challenge_number |
| Col 9 | Weekly Objective → Weekly Challenge | ProjectSession table | weekly_objective (AI generated) |
| Col 10 | Session Description [Project Topic] | ProjectSession table | session_description (AI generated) |
| Col 11 | (Empty/overflow) | Not stored | — |
| Col 12 | Learning Material | GeneratedOutput table | output_type, file, raw_content (AI generated) |

**Col 0-8 = Seed data (stored once, never changes)**
**Col 9-12 = AI generated data (new for every project)**
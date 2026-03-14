<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Agency Builder Roadmap — Hitika</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=DM+Mono:wght@300;400;500&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --ink: #0f0f0f;
    --paper: #f5f0e8;
    --cream: #ede7d9;
    --accent: #c84b2f;
    --accent2: #2f5fc8;
    --muted: #7a7060;
    --done: #2a7a4b;
    --border: #d4cdc0;
  }

/* FIX 1: was `-` which is invalid — changed to `*` */

- { box-sizing: border-box; margin: 0; padding: 0; }

body {
background: var(–paper);
color: var(–ink);
font-family: ‘DM Sans’, sans-serif;
min-height: 100vh;
padding: 0;
}

.header {
background: var(–ink);
color: var(–paper);
padding: 48px 60px 36px;
position: relative;
overflow: hidden;
}

.header::before {
content: ‘AGENCY’;
font-family: ‘Playfair Display’, serif;
font-weight: 900;
font-size: 180px;
color: rgba(255,255,255,0.04);
position: absolute;
right: -20px;
top: -30px;
letter-spacing: -8px;
pointer-events: none;
}

.header-label {
font-family: ‘DM Mono’, monospace;
font-size: 11px;
letter-spacing: 3px;
text-transform: uppercase;
color: var(–accent);
margin-bottom: 12px;
}

.header h1 {
font-family: ‘Playfair Display’, serif;
font-size: 48px;
font-weight: 900;
line-height: 1.05;
margin-bottom: 10px;
}

.header p {
font-size: 14px;
color: rgba(245,240,232,0.55);
max-width: 480px;
line-height: 1.6;
font-family: ‘DM Mono’, monospace;
}

.progress-bar-wrap {
margin-top: 28px;
display: flex;
align-items: center;
gap: 16px;
}

.progress-bar {
flex: 1;
height: 4px;
background: rgba(255,255,255,0.12);
border-radius: 2px;
max-width: 320px;
}

.progress-fill {
height: 100%;
background: var(–accent);
border-radius: 2px;
transition: width 0.5s ease;
width: 0%;
}

.progress-label {
font-family: ‘DM Mono’, monospace;
font-size: 12px;
color: rgba(245,240,232,0.5);
}

.nav {
display: flex;
gap: 0;
padding: 0 60px;
background: var(–cream);
border-bottom: 1px solid var(–border);
overflow-x: auto;
}

.nav-tab {
font-family: ‘DM Mono’, monospace;
font-size: 11px;
letter-spacing: 2px;
text-transform: uppercase;
padding: 16px 24px;
cursor: pointer;
border: none;
background: transparent;
color: var(–muted);
border-bottom: 2px solid transparent;
margin-bottom: -1px;
white-space: nowrap;
transition: all 0.2s;
}

.nav-tab:hover { color: var(–ink); }

.nav-tab.active {
color: var(–ink);
border-bottom-color: var(–accent);
}

.main {
padding: 40px 60px;
max-width: 1100px;
}

.phase-view { display: none; }
.phase-view.active { display: block; }

.phase-meta {
display: flex;
align-items: flex-start;
justify-content: space-between;
margin-bottom: 32px;
padding-bottom: 24px;
border-bottom: 1px solid var(–border);
flex-wrap: wrap;
gap: 16px;
}

.phase-title {
font-family: ‘Playfair Display’, serif;
font-size: 32px;
font-weight: 700;
margin-bottom: 6px;
}

.phase-subtitle {
font-size: 13px;
color: var(–muted);
font-family: ‘DM Mono’, monospace;
max-width: 480px;
line-height: 1.6;
}

.phase-tag {
font-family: ‘DM Mono’, monospace;
font-size: 10px;
letter-spacing: 2px;
text-transform: uppercase;
padding: 6px 12px;
border: 1px solid var(–border);
color: var(–muted);
border-radius: 2px;
white-space: nowrap;
}

.sprint {
margin-bottom: 36px;
}

.sprint-header {
display: flex;
align-items: center;
gap: 12px;
margin-bottom: 16px;
}

.sprint-num {
font-family: ‘DM Mono’, monospace;
font-size: 10px;
letter-spacing: 2px;
text-transform: uppercase;
background: var(–ink);
color: var(–paper);
padding: 4px 10px;
border-radius: 2px;
}

.sprint-title {
font-family: ‘Playfair Display’, serif;
font-size: 18px;
font-weight: 700;
}

.sprint-focus {
font-size: 12px;
color: var(–muted);
font-family: ‘DM Mono’, monospace;
margin-left: auto;
}

.tasks {
display: grid;
gap: 8px;
}

.task {
display: flex;
align-items: flex-start;
gap: 12px;
padding: 14px 16px;
background: white;
border: 1px solid var(–border);
border-radius: 4px;
cursor: pointer;
transition: all 0.15s;
position: relative;
}

.task:hover { border-color: var(–ink); }

.task.done {
background: #f0f7f3;
border-color: #b8ddc9;
}

.task.done .task-text { text-decoration: line-through; color: var(–muted); }

.task-check {
width: 18px;
height: 18px;
border: 1.5px solid var(–border);
border-radius: 2px;
flex-shrink: 0;
margin-top: 1px;
display: flex;
align-items: center;
justify-content: center;
transition: all 0.15s;
}

.task.done .task-check {
background: var(–done);
border-color: var(–done);
color: white;
}

.task-check::after {
content: ‘✓’;
font-size: 11px;
display: none;
}

.task.done .task-check::after { display: block; }

.task-body { flex: 1; }

.task-text {
font-size: 14px;
line-height: 1.5;
margin-bottom: 4px;
}

.task-note {
font-size: 11px;
color: var(–muted);
font-family: ‘DM Mono’, monospace;
line-height: 1.5;
}

.task-tag {
font-family: ‘DM Mono’, monospace;
font-size: 9px;
letter-spacing: 1.5px;
text-transform: uppercase;
padding: 2px 7px;
border-radius: 2px;
white-space: nowrap;
flex-shrink: 0;
}

.tag-doc      { background: #e8f0fe; color: #2f5fc8; }
.tag-research { background: #fef3e2; color: #b45309; }
.tag-build    { background: #f0f7f3; color: #2a7a4b; }
.tag-learn    { background: #fce8e6; color: #c84b2f; }
.tag-strategy { background: #f3e8ff; color: #6b21a8; }

.section-rule {
border: none;
border-top: 1px solid var(–border);
margin: 32px 0;
}

.deliverable-box {
background: var(–ink);
color: var(–paper);
padding: 20px 24px;
border-radius: 4px;
margin-top: 28px;
}

.deliverable-box h4 {
font-family: ‘DM Mono’, monospace;
font-size: 10px;
letter-spacing: 3px;
text-transform: uppercase;
color: var(–accent);
margin-bottom: 12px;
}

.deliverable-list {
display: flex;
flex-wrap: wrap;
gap: 8px;
}

.deliverable-item {
font-size: 12px;
padding: 5px 12px;
border: 1px solid rgba(245,240,232,0.2);
border-radius: 2px;
font-family: ‘DM Mono’, monospace;
color: rgba(245,240,232,0.8);
}

@media (max-width: 700px) {
.header { padding: 32px 24px 28px; }
.header h1 { font-size: 32px; }
.nav { padding: 0 24px; }
.main { padding: 28px 24px; }
.phase-meta { flex-direction: column; }
.sprint-focus { display: none; }
}
</style>

</head>
<body>

<div class="header">
  <div class="header-label">Solo Founder Blueprint · 2025–2026</div>
  <h1>Build While<br>You're Employed</h1>
  <p>12-week agency infrastructure sprint. One year to go from solo contributor to owner-operator. Track it here.</p>
  <div class="progress-bar-wrap">
    <div class="progress-bar"><div class="progress-fill" id="globalFill"></div></div>
    <div class="progress-label" id="globalLabel">0 / 0 tasks complete</div>
  </div>
</div>

<div class="nav">
  <button class="nav-tab active" data-tab="m1">Month 1 — Foundation</button>
  <button class="nav-tab" data-tab="m2">Month 2 — Services &amp; Offers</button>
  <button class="nav-tab" data-tab="m3">Month 3 — Systems &amp; Udaipur R&amp;D</button>
  <button class="nav-tab" data-tab="ongoing">Ongoing Rituals</button>
</div>

<div class="main">

  <!-- MONTH 1 -->

  <div class="phase-view active" id="m1">
    <div class="phase-meta">
      <div>
        <div class="phase-title">Month 1: Foundation</div>
        <div class="phase-subtitle">Before you can sell anything, you need to know exactly what you're building, who it's for, and what documents underpin the whole operation. No client work yet. Pure infrastructure.</div>
      </div>
      <div class="phase-tag">Weeks 1–4 · ~5 hrs/week</div>
    </div>

```
<div class="sprint">
  <div class="sprint-header">
    <span class="sprint-num">Sprint 1</span>
    <span class="sprint-title">Clarity &amp; Positioning</span>
    <span class="sprint-focus">Week 1–2</span>
  </div>
  <div class="tasks">
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Write your agency's founding document — a 1-page internal brief</div>
        <div class="task-note">Answer: What does the agency do, who is it for, what problem does it solve, what's the brand POV. Not for clients — for you. This becomes your north star.</div>
      </div>
      <span class="task-tag tag-doc">Document</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Define your 3 core service pillars</div>
        <div class="task-note">E.g. Podcast Production, Social Media Strategy, Brand Content. Don't list 10 things. Pick 3 you can do well and charge for. Everything else is an add-on.</div>
      </div>
      <span class="task-tag tag-strategy">Strategy</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Map your target client — write a 1-page ICP (Ideal Client Profile)</div>
        <div class="task-note">Who are they? (Founder, executive coach, D2C brand, MSME?) What's their budget bracket? What pain are they bringing to you? What do they look like on Instagram?</div>
      </div>
      <span class="task-tag tag-strategy">Strategy</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Audit your existing case studies — write 2–3 mini case study docs</div>
        <div class="task-note">Love Lingo (3K to 8.3K organic), DotStory podcast production, Anshu Patni brand strategy. One page each: problem → what you did → result. These become your pitch ammo.</div>
      </div>
      <span class="task-tag tag-doc">Document</span>
    </div>
  </div>
</div>

<div class="sprint">
  <div class="sprint-header">
    <span class="sprint-num">Sprint 2</span>
    <span class="sprint-title">The Master Questionnaire</span>
    <span class="sprint-focus">Week 3–4</span>
  </div>
  <div class="tasks">
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Research: collect 5–8 existing agency intake questionnaires</div>
        <div class="task-note">Search LinkedIn, Twitter/X, Reddit (r/agency, r/freelance). Screenshot or save them. Note what's missing in each. This is your raw material.</div>
      </div>
      <span class="task-tag tag-research">Research</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Draft Section 1: Business Context (15–20 questions)</div>
        <div class="task-note">Brand story, founding year, team size, revenue stage, who makes decisions, what's worked before, what hasn't. Goal: AI can build a business snapshot from this alone.</div>
      </div>
      <span class="task-tag tag-doc">Document</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Draft Section 2: Audience &amp; Positioning (10–12 questions)</div>
        <div class="task-note">Who is their customer, what does their customer fear/want, how does client describe themselves vs how customers describe them. Include a brand personality matrix prompt.</div>
      </div>
      <span class="task-tag tag-doc">Document</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Draft Section 3: Content &amp; Social (12–15 questions)</div>
        <div class="task-note">Current platforms, posting frequency, what content performs, what they hate making, do they want to be on camera, are they a thought leader or a brand account.</div>
      </div>
      <span class="task-tag tag-doc">Document</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Draft Section 4: Goals, Budget, Constraints (8–10 questions)</div>
        <div class="task-note">What does success look like in 6 months, what have they spent before, who else is involved, any brand guidelines, any "never do this" rules.</div>
      </div>
      <span class="task-tag tag-doc">Document</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Write the master AI prompt that takes questionnaire answers → full audit output</div>
        <div class="task-note">This is the crown jewel. Test it with Claude. Iterate until the output is genuinely useful: brand audit, content gaps, 3 strategic recommendations, proposed scope of work.</div>
      </div>
      <span class="task-tag tag-build">Build</span>
    </div>
  </div>
</div>

<div class="deliverable-box">
  <h4>Month 1 Deliverables</h4>
  <div class="deliverable-list">
    <span class="deliverable-item">Agency founding brief</span>
    <span class="deliverable-item">ICP document</span>
    <span class="deliverable-item">3 mini case studies</span>
    <span class="deliverable-item">Master intake questionnaire (v1)</span>
    <span class="deliverable-item">AI audit prompt (tested)</span>
  </div>
</div>
```

  </div>

  <!-- MONTH 2 -->

  <div class="phase-view" id="m2">
    <div class="phase-meta">
      <div>
        <div class="phase-title">Month 2: Services &amp; Offers</div>
        <div class="phase-subtitle">Now you build what you're actually selling — packages, pricing logic, onboarding flow, contracts. By end of this month you could technically take on a client tomorrow.</div>
      </div>
      <div class="phase-tag">Weeks 5–8 · ~6 hrs/week</div>
    </div>

```
<div class="sprint">
  <div class="sprint-header">
    <span class="sprint-num">Sprint 3</span>
    <span class="sprint-title">Service Packages</span>
    <span class="sprint-focus">Week 5–6</span>
  </div>
  <div class="tasks">
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Build your service menu document — each service, what's included, what's not</div>
        <div class="task-note">For each service: deliverables per month, turnaround time, your time commitment, tools needed. Be brutally specific. Vague services = scope creep = burnout.</div>
      </div>
      <span class="task-tag tag-doc">Document</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Create 3-tier package structure for Social Media Management</div>
        <div class="task-note">Starter / Growth / Full Stack. Define post count, platform count, strategy calls, reporting cadence. Leave pricing as a range for now — you'll finalize after market research next month.</div>
      </div>
      <span class="task-tag tag-build">Build</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Create 3-tier package structure for Podcast Production</div>
        <div class="task-note">Pre-production only / Full production / Full production + social. What does each include — scripting, editing, show notes, audiograms, scheduling? Map it out.</div>
      </div>
      <span class="task-tag tag-build">Build</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Create a Brand Strategy one-time project scope</div>
        <div class="task-note">Based on your Anshu Patni experience. What does a brand strategy engagement include? Deliverables, timeline, number of revisions, handoff format. This is a premium project, not a retainer.</div>
      </div>
      <span class="task-tag tag-build">Build</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Research competitor pricing — 15 agencies/freelancers in your category</div>
        <div class="task-note">Look at Indian solo agencies and small studios on LinkedIn, Instagram, and Karat (if you can access). Note what they charge or imply they charge. Build a pricing benchmark sheet.</div>
      </div>
      <span class="task-tag tag-research">Research</span>
    </div>
  </div>
</div>

<div class="sprint">
  <div class="sprint-header">
    <span class="sprint-num">Sprint 4</span>
    <span class="sprint-title">Legal &amp; Financial Infrastructure</span>
    <span class="sprint-focus">Week 7–8</span>
  </div>
  <div class="tasks">
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Draft a client contract template (freelance services agreement)</div>
        <div class="task-note">Cover: scope of work, payment terms, revision limits, IP ownership, kill fee clause, confidentiality, termination notice period. Use an Indian freelance contract as base. Do NOT skip the kill fee.</div>
      </div>
      <span class="task-tag tag-doc">Document</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Build an invoice template in Canva or Notion</div>
        <div class="task-note">Include: your name/brand, GST number (or placeholder), client details, line items, payment due date, bank account/UPI details. Professional invoices = faster payment.</div>
      </div>
      <span class="task-tag tag-build">Build</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Create a project proposal / scope of work template</div>
        <div class="task-note">Covers: what you heard from them, what you're proposing, exact deliverables, timeline, what you need from them, investment. This is what you send before the contract.</div>
      </div>
      <span class="task-tag tag-doc">Document</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Research GST registration requirements for freelance agencies in India</div>
        <div class="task-note">At what threshold is registration mandatory? What's the process? Do you need it before taking your first client? Keep notes — you'll need this when you go live.</div>
      </div>
      <span class="task-tag tag-research">Research</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Build a client tracker spreadsheet (pipeline + active clients)</div>
        <div class="task-note">Columns: Lead name, service interested in, status, proposal sent date, contract signed, retainer amount, invoice date, paid/unpaid. Even if you have 0 clients, the habit matters.</div>
      </div>
      <span class="task-tag tag-build">Build</span>
    </div>
  </div>
</div>

<div class="deliverable-box">
  <h4>Month 2 Deliverables</h4>
  <div class="deliverable-list">
    <span class="deliverable-item">Service menu document</span>
    <span class="deliverable-item">3 packaged offer structures</span>
    <span class="deliverable-item">Pricing benchmark sheet</span>
    <span class="deliverable-item">Client contract template</span>
    <span class="deliverable-item">Invoice template</span>
    <span class="deliverable-item">Proposal/SOW template</span>
    <span class="deliverable-item">Client pipeline tracker</span>
  </div>
</div>
```

  </div>

  <!-- MONTH 3 -->

  <div class="phase-view" id="m3">
    <div class="phase-meta">
      <div>
        <div class="phase-title">Month 3: Systems + Udaipur R&amp;D</div>
        <div class="phase-subtitle">Operational systems that let you run the agency without burning out. Plus: serious research into the Udaipur market opportunity — the outsourcing gap you mentioned is real and worth sizing properly.</div>
      </div>
      <div class="phase-tag">Weeks 9–12 · ~6 hrs/week</div>
    </div>

```
<div class="sprint">
  <div class="sprint-header">
    <span class="sprint-num">Sprint 5</span>
    <span class="sprint-title">Onboarding &amp; Delivery Systems</span>
    <span class="sprint-focus">Week 9–10</span>
  </div>
  <div class="tasks">
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Design your full client onboarding flow — step by step</div>
        <div class="task-note">From "I want to work with you" to "we're live." Every step: discovery call → proposal → contract → invoice → kickoff call → access collection → content calendar → first post. Document every handoff.</div>
      </div>
      <span class="task-tag tag-build">Build</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Build a client onboarding kit (the Notion or Google Doc they get on day 1)</div>
        <div class="task-note">Includes: welcome note, what to expect, communication norms (response time, channels), brand asset checklist, what you need from them in week 1, timeline. This sets the tone entirely.</div>
      </div>
      <span class="task-tag tag-doc">Document</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Build a content delivery SOP for social media clients</div>
        <div class="task-note">How do you deliver content for approval? What's the revision round process? How many rounds? What's the turnaround for feedback? What happens if they miss the approval window?</div>
      </div>
      <span class="task-tag tag-doc">Document</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Build a podcast production SOP — from recording to publish</div>
        <div class="task-note">Pre-production checklist, recording brief template, editing brief, review process, show notes format, publish checklist, social assets checklist. Build this once, use forever.</div>
      </div>
      <span class="task-tag tag-doc">Document</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Build a monthly reporting template for social media clients</div>
        <div class="task-note">What metrics matter (reach, saves, DMs, profile visits, follower growth). What you comment on. What you recommend next month. Keep it visual. This is a retention tool, not just a report.</div>
      </div>
      <span class="task-tag tag-build">Build</span>
    </div>
  </div>
</div>

<!-- FIX 2: Sprint 6A label was "Jaipur Market Research" — corrected to Udaipur -->
<div class="sprint">
  <div class="sprint-header">
    <span class="sprint-num">Sprint 6A</span>
    <span class="sprint-title">Udaipur Market Research</span>
    <span class="sprint-focus">Week 11</span>
  </div>
  <div class="tasks">
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Map which Udaipur agencies are currently outsourcing to Jaipur — and why</div>
        <div class="task-note">Talk to 3–5 Udaipur business owners informally. Ask: who does your social media, where are they based, what's the frustration, would you prefer someone local who also understands your market. This is your insight doc.</div>
      </div>
      <span class="task-tag tag-research">Research</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Map Udaipur's key business verticals worth targeting</div>
        <div class="task-note">Hospitality &amp; heritage hotels, handicraft exporters, D2C lifestyle brands, real estate, wedding industry, education institutes. For each: do they have Instagram presence? Is it good? Who runs it?</div>
      </div>
      <span class="task-tag tag-research">Research</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Write a 2-page Udaipur Market Opportunity brief</div>
        <div class="task-note">The gap: local businesses, money going to Jaipur, no premium local option. Your play: remote-first agency that understands Udaipur context AND can serve nationally/internationally. Include 3 target segments to prioritize first.</div>
      </div>
      <span class="task-tag tag-strategy">Strategy</span>
    </div>
  </div>
</div>

<div class="sprint">
  <div class="sprint-header">
    <span class="sprint-num">Sprint 6B</span>
    <span class="sprint-title">Remote Operations + International Clients</span>
    <span class="sprint-focus">Week 12</span>
  </div>
  <div class="tasks">
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Design your remote client stack — tools for async, zero-friction delivery</div>
        <div class="task-note">Notion (client portals + SOPs), Loom (async video updates instead of calls), Slack or WhatsApp Business, Google Drive (shared brand folders), Calendly (booking), Stripe or Wise (international payments). Document which tool does what job.</div>
      </div>
      <span class="task-tag tag-build">Build</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Research international payment infrastructure for Indian freelancers</div>
        <div class="task-note">Wise vs Payoneer vs Stripe (India) vs Razorpay for international. What are the limits, fees, FEMA compliance requirements? For clients in UK, US, UAE — what's the cleanest way to invoice and receive? Build a 1-page summary.</div>
      </div>
      <span class="task-tag tag-research">Research</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Map the international client acquisition funnel for content agencies</div>
        <div class="task-note">How do small remote agencies actually get international clients? Research: LinkedIn outbound, Clutch.co listings, Contra, Toptal (content), cold email, referrals, niche communities. Identify 2–3 channels that are realistic in Year 1 and document the approach for each.</div>
      </div>
      <span class="task-tag tag-research">Research</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Build a geo-based pricing framework: India vs Gulf vs UK/US rates</div>
        <div class="task-note">Research what Indian agencies charge Indian clients, what they charge Gulf clients (UAE, Saudi — huge market), and what UK/US clients expect to pay. The same social media package can be priced 3–5x higher for an international client. Build a rate card with three geo tiers.</div>
      </div>
      <span class="task-tag tag-research">Research</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Identify 3 international niches where Indian content agencies have natural edge</div>
        <div class="task-note">Think: South Asian diaspora brands in UK/US/Canada, Indian heritage hospitality (international tourism market), yoga/wellness brands targeting Western audiences, Indian D2C going global. Pick niches where your cultural fluency is a feature, not a liability.</div>
      </div>
      <span class="task-tag tag-strategy">Strategy</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Skill gap audit: what do you need to learn to charge premium (India + international)?</div>
        <div class="task-note">Meta Ads (already in progress), SEO basics, email marketing fundamentals, video strategy, pitch deck design, cross-cultural content strategy. Rank by: revenue impact × your current gap. This becomes your Year 1 learning roadmap.</div>
      </div>
      <span class="task-tag tag-learn">Learn</span>
    </div>
  </div>
</div>

<div class="deliverable-box">
  <h4>Month 3 Deliverables</h4>
  <div class="deliverable-list">
    <span class="deliverable-item">Client onboarding flow map</span>
    <span class="deliverable-item">Client onboarding kit</span>
    <span class="deliverable-item">Social media delivery SOP</span>
    <span class="deliverable-item">Podcast production SOP</span>
    <span class="deliverable-item">Monthly reporting template</span>
    <span class="deliverable-item">Udaipur market opportunity brief</span>
    <span class="deliverable-item">Remote client tool stack doc</span>
    <span class="deliverable-item">International payments guide</span>
    <span class="deliverable-item">Geo-based pricing framework</span>
    <span class="deliverable-item">Skill gap audit + learning list</span>
  </div>
</div>
```

  </div>

  <!-- ONGOING -->

  <div class="phase-view" id="ongoing">
    <div class="phase-meta">
      <div>
        <div class="phase-title">Ongoing Rituals</div>
        <div class="phase-subtitle">Non-negotiable habits that compound over 12 months. These aren't sprint tasks — they're how you build the long game while working full-time.</div>
      </div>
      <div class="phase-tag">Every week · ~2 hrs</div>
    </div>

```
<div class="sprint">
  <div class="sprint-header">
    <span class="sprint-num">Weekly</span>
    <span class="sprint-title">Weekly Habits</span>
  </div>
  <div class="tasks">
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">30 min: Document one thing you learned at the NBFC job</div>
        <div class="task-note">Financial services marketing, B2B content, regulated industry brand strategy — this is gold for your future agency positioning. Write it down. It compounds.</div>
      </div>
      <span class="task-tag tag-learn">Learn</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">30 min: Read one agency owner's newsletter or case study</div>
        <div class="task-note">Recommendations: Varun Mayya, Social Media Examiner, Agency Hackers (UK), Nathan Barry (ConvertKit). Save good frameworks to a swipe folder.</div>
      </div>
      <span class="task-tag tag-research">Research</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">15 min: Update your master document folder — version control your work</div>
        <div class="task-note">Every document needs a version date. Create a Google Drive folder structure now: /Agency Infrastructure / Questionnaires / Contracts / Packages / Research / SOPs</div>
      </div>
      <span class="task-tag tag-build">Build</span>
    </div>
  </div>
</div>

<div class="sprint">
  <div class="sprint-header">
    <span class="sprint-num">Monthly</span>
    <span class="sprint-title">Monthly Review</span>
  </div>
  <div class="tasks">
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">End-of-month retrospective: what did you build, what did you skip, why</div>
        <div class="task-note">Honest 1-page note to yourself. What's blocking you — time, energy, clarity, confidence? Name it. You can only fix what you've named.</div>
      </div>
      <span class="task-tag tag-strategy">Strategy</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Talk to one person who runs their own agency or freelance business</div>
        <div class="task-note">Doesn't have to be formal. DM someone on LinkedIn. Podcast community. Instagram. Ask one real question. The answer will be more useful than 10 articles.</div>
      </div>
      <span class="task-tag tag-research">Research</span>
    </div>
    <div class="task" onclick="toggleTask(this)">
      <div class="task-check"></div>
      <div class="task-body">
        <div class="task-text">Update the questionnaire or one process doc based on what you've learned</div>
        <div class="task-note">These are living documents. Every month you know more than last month. Schedule time to improve one thing, not everything.</div>
      </div>
      <span class="task-tag tag-doc">Document</span>
    </div>
  </div>
</div>

<div class="deliverable-box">
  <h4>By Month 12 — If You Hold The Rituals</h4>
  <div class="deliverable-list">
    <span class="deliverable-item">Battle-tested client questionnaire</span>
    <span class="deliverable-item">Packaged offers ready to sell</span>
    <span class="deliverable-item">Complete ops infrastructure</span>
    <span class="deliverable-item">Udaipur + remote market strategy</span>
    <span class="deliverable-item">International client playbook</span>
    <span class="deliverable-item">Geo-tiered pricing framework</span>
    <span class="deliverable-item">Meta Ads + paid media fluency</span>
    <span class="deliverable-item">12 months of NBFC brand experience</span>
    <span class="deliverable-item">Agency launch-ready on day 1</span>
  </div>
</div>
```

  </div>

</div>

<script>
  function toggleTask(el) {
    el.classList.toggle('done');
    updateProgress();
  }

  // FIX 3: removed reliance on global `event` object — pass button reference directly
  document.querySelectorAll('.nav-tab').forEach(function(btn) {
    btn.addEventListener('click', function() {
      var tabId = this.getAttribute('data-tab');
      document.querySelectorAll('.phase-view').forEach(function(v) {
        v.classList.remove('active');
      });
      document.querySelectorAll('.nav-tab').forEach(function(t) {
        t.classList.remove('active');
      });
      document.getElementById(tabId).classList.add('active');
      this.classList.add('active');
    });
  });

  function updateProgress() {
    var all  = document.querySelectorAll('.task');
    var done = document.querySelectorAll('.task.done');
    var pct  = all.length ? Math.round((done.length / all.length) * 100) : 0;
    document.getElementById('globalFill').style.width = pct + '%';
    document.getElementById('globalLabel').textContent = done.length + ' / ' + all.length + ' tasks complete';
  }

  updateProgress();
</script>

</body>
</html>

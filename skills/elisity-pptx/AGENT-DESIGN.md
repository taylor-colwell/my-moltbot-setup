# Elisity PPTX Agent Design

## Agent Overview

**Name:** `elisity-pptx-agent`
**Slash Command:** `/slides`
**Purpose:** Transform slide ideas into polished, on-brand Elisity presentations using TDM-style patterns, technical accuracy from experts, and internal knowledge sources.

---

## Core Capabilities

### Input Types (Priority Order)
1. **Free-form text** (primary) - "Create a slide showing how Claroty integrates with Elisity"
2. **Rough slides to polish** - Existing PPTX with content that needs refinement
3. **Markdown documents** (occasional) - Structured content to convert

### Output
- **Final PPTX files only** - No intermediate HTML or thumbnails
- Direct iteration on PPTX output

### Scope Decisions (Agent Intelligence)
- **Single slide**: Most common, simple concepts
- **2-3 slides**: When concept requires sequence or multiple views
- **Full deck (5-20)**: When explicitly requested or content warrants

---

## Workflow

```
┌─────────────────────────────────────────────────────────────────┐
│                        USER INPUT                                │
│         (free-form text, rough slide, markdown)                  │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    1. ANALYZE REQUEST                            │
│  • Parse intent (new slide, polish existing, full deck)          │
│  • Identify technical topics requiring expert consultation       │
│  • Determine scope (1 slide, 2-3 slides, full deck)             │
│  • Flag any confidential data concerns                           │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                 2. GATHER TECHNICAL CONTEXT                      │
│                                                                  │
│  ┌──────────────────┐  ┌──────────────────┐  ┌───────────────┐  │
│  │ elisity-microseg │  │ atlassian-agent  │  │ elisity-brand │  │
│  │     -expert      │  │  (MCP Server)    │  │    skill      │  │
│  ├──────────────────┤  ├──────────────────┤  ├───────────────┤  │
│  │ • Solution arch  │  │ • Roadmap items  │  │ • Colors      │  │
│  │ • Product details│  │ • Future features│  │ • Typography  │  │
│  │ • Technical acc. │  │ • ENG tickets    │  │ • Terminology │  │
│  │ • Best practices │  │ • PM specs       │  │ • Voice/tone  │  │
│  │ • Integrations   │  │ • Confluence docs│  │               │  │
│  └──────────────────┘  └──────────────────┘  └───────────────┘  │
│                                                                  │
│  DECISION LOGIC:                                                 │
│  • Elisity-specific content? → Always consult microseg-expert   │
│  • Future/roadmap feature? → Search Atlassian (Jira + Confluence)│
│  • Feature not in public docs? → Search Atlassian               │
│  • Any slide? → Apply elisity-brand guidelines                  │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                   3. SELECT PATTERNS                             │
│                                                                  │
│  Reference: TDM-PATTERNS.md                                      │
│  • Architecture Diagram → vertical hierarchy pattern             │
│  • Comparison (vs X) → two-column legacy vs Elisity             │
│  • Process Flow → 6-step numbered flow                          │
│  • Integration Partner → templated partner diagram              │
│  • Component Deep-Dive → icon + feature bullets                 │
│  • Policy Construct → visual hierarchy                          │
│  • Scale/Technical → tables, configs                            │
│  • Connectivity → 3-tier port/protocol diagram                  │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                   4. SELECT LAYOUT & ELEMENTS                    │
│                                                                  │
│  Reference: LAYOUTS.md                                           │
│  • Most slides: Layout 41 (Light_Headline_01)                   │
│  • Full canvas diagrams: Layout 36-39 (blank variants)          │
│  • Comparison slides: Layout 3-4 (two-column)                   │
│                                                                  │
│  Reference: ELEMENTS.md                                          │
│  • SVG icons from icons/ folder (rasterize to PNG)              │
│  • Copy elements from elisity-element-library.pptx              │
│  • Partner logos from element library slide 2                   │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│               5. GENERATE DRAFT (CHECKPOINT)                     │
│                                                                  │
│  Present to user:                                                │
│  • Proposed slide structure/outline                              │
│  • Pattern being used                                            │
│  • Key content points                                            │
│  • Any assumptions made                                          │
│                                                                  │
│  User can: Approve / Modify / Change direction                   │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                   6. BUILD PPTX                                  │
│                                                                  │
│  Methods (choose based on complexity):                           │
│  • OOXML editing: Modify existing template slides               │
│  • html2pptx: Generate new slides from HTML                     │
│  • Hybrid: Copy template + modify content                       │
│                                                                  │
│  Always:                                                         │
│  • Use correct Elisity colors (#053242, #0B6280, #54B9F1, etc.) │
│  • Use Inter font family                                         │
│  • Include © footer                                              │
│  • Apply brand guidelines                                        │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                   7. DELIVER & ITERATE                           │
│                                                                  │
│  • Output final PPTX file                                        │
│  • User reviews in PowerPoint                                    │
│  • User provides feedback                                        │
│  • Agent refines based on feedback                               │
│  • Repeat until satisfied                                        │
└─────────────────────────────────────────────────────────────────┘
```

---

## Agent Decision Logic

### When to Consult `elisity-microseg-expert`
**ALWAYS** when slide content includes:
- Elisity product components (CCC, VE, VEN, IdentityGraph)
- Technical architecture details
- Policy constructs (Policy Groups, Policy Sets, Distribution Zones)
- Integration patterns
- Enforcement mechanisms
- Competitive differentiation
- Solution-specific content

### When to Consult `atlassian-agent`
When slide content involves:
- Features not in public documentation
- Roadmap items or future capabilities
- New product features in development
- Conglomeration of multiple future features
- Internal technical specifications
- Customer-specific implementations (if authorized)

**Search targets:**
- Jira: ENG and PM projects
- Confluence: Keyword search across spaces

### When to Apply `elisity-brand` Skill
**ALWAYS** - Every slide must:
- Use correct color palette
- Use Inter typography
- Follow "Confidently Cool" brand essence
- Use correct product terminology
- Avoid confidential/internal data unless explicitly requested

---

## Confidentiality Rules

### NEVER include (unless explicitly requested):
- Customer names or logos
- Internal metrics or financials
- Unreleased product details
- Internal Jira ticket numbers
- Employee names (except for standard presenter slides)
- Pricing information
- Competitive intelligence details

### ALWAYS safe to include:
- Public product capabilities
- Published integration partners
- Generic architecture diagrams
- Industry statistics (with attribution)
- Public customer testimonials (if previously published)

---

## Slash Command Specification

```
/slides [description]

Examples:
  /slides Show how Claroty integrates with Elisity for OT visibility
  /slides Create an architecture diagram for cloud-hosted VE deployment
  /slides Polish this slide: [attach rough PPTX]
  /slides Build a 5-slide overview of Elisity for manufacturing CISOs
  /slides Explain Distribution Zones with a visual diagram
```

### Command Parsing
- If description mentions specific integration → use Integration Partner pattern
- If description mentions "vs" or "compared to" → use Comparison pattern
- If description mentions "flow" or "process" → use Process Flow pattern
- If description mentions "architecture" or "diagram" → use Architecture Diagram pattern
- If description mentions "polish" + attachment → refine existing slide

---

## File Dependencies

### Required Skills
- `elisity-brand` - Brand guidelines enforcement
- `elisity-pptx` - Templates, icons, patterns, layouts

### Required Agents
- `elisity-microseg-expert` - Technical accuracy validation
- `atlassian-agent` - Internal documentation and roadmap

### Required Templates
- `templates/elisity-master-slides.pptx` - Layout source
- `templates/elisity-element-library.pptx` - Icon/element source

### Required Documentation
- `TDM-PATTERNS.md` - Slide pattern selection
- `LAYOUTS.md` - Layout selection
- `ELEMENTS.md` - Element selection
- `icons/ICONS.md` - SVG icon reference

---

## Example Interactions

### Example 1: Integration Slide
```
User: /slides Show how CrowdStrike integrates with Elisity

Agent: I'll create an integration slide using the Partner Integration pattern.

[Consults elisity-microseg-expert for integration details]
[Applies elisity-brand guidelines]

Proposed structure:
- Title: "CrowdStrike Integration - Enrichment to Enforcement"
- 6-step flow diagram showing:
  1. Device discovery
  2. CrowdStrike enrichment
  3. Policy Group classification
  4. Policy distribution to VE
  5. Enforcement at infrastructure
  6. Continuous verification
- "Better Together" value props (3 bullets)
- CrowdStrike logo placement

Shall I proceed with this structure?
```

### Example 2: Future Feature Slide
```
User: /slides Create a slide explaining how Elisity will use AI for policy recommendations

Agent: This involves a future/roadmap feature. Let me gather context.

[Searches Atlassian for "AI policy recommendations"]
[Found: ENG-1234, PM-567, Confluence doc "AI Roadmap Q2"]
[Consults elisity-microseg-expert for technical framing]
[Applies elisity-brand guidelines]

Proposed structure:
- Title: "Elisity Intelligence - AI-Powered Policy Recommendations"
- Component diagram showing IdentityGraph + AI engine
- Key capabilities (from roadmap docs)
- Note: Will exclude internal timeline/dates per confidentiality rules

Shall I proceed? Any adjustments needed?
```

### Example 3: Polish Existing Slide
```
User: /slides Polish this slide [attaches rough.pptx]

Agent: I'll analyze your existing slide and refine it.

[Reads slide content]
[Identifies pattern: Architecture Diagram]
[Checks technical accuracy with elisity-microseg-expert]
[Applies elisity-brand guidelines]

Improvements I'll make:
- Align icons to TDM visual hierarchy (cloud → edge → devices)
- Update colors to brand palette
- Fix terminology ("VEN" not "edge node")
- Add proper connection arrows with protocol labels
- Apply correct typography (Inter family)

Proceed with these refinements?
```

---

## Implementation Notes

### Agent Registration
Add to Claude Code's available agents as `elisity-pptx-agent` with:
- Access to all tools (Read, Write, Edit, Bash, Task, etc.)
- Ability to spawn sub-agents (elisity-microseg-expert, atlassian-agent)
- File system access for PPTX manipulation

### Skill Invocation
Register `/slides` as user-invocable skill pointing to this agent.

### State Management
- Maintain context within conversation for iterative refinement
- Remember user preferences expressed during session
- Track which slides were generated for follow-up edits

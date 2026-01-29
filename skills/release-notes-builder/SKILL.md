---
name: release-notes-builder
description: "Build Elisity release notes from Jira tickets and roadmap PowerPoints. Use when: (1) generating release notes for a new version, (2) validating which features shipped, (3) running the releasebot CLI. Triggers on requests like 'build release notes', 'generate release notes for version X', 'run releasebot', or 'validate roadmap tickets'."
---

# Release Notes Builder

Generate customer-facing release notes for Elisity product releases using the releasebot CLI tool.

## Project Location

The releasebot project is at: `/Users/taylorcolwell/Cursor-Projects/releasebot`

## Quick Reference

```bash
# Activate environment
cd /Users/taylorcolwell/Cursor-Projects/releasebot
source .venv/bin/activate

# Validate (dry-run - see what ships without generating notes)
releasebot validate <VERSION> --include "inputs/roadmaps/<ROADMAP>.pptx"

# Build release notes
releasebot build <VERSION> -p ENG --include "inputs/roadmaps/<ROADMAP>.pptx"

# With manual additions
releasebot validate <VERSION> --include "inputs/roadmaps/<ROADMAP>.pptx" --manual inputs/manual/manual_additions.csv
releasebot build <VERSION> -p ENG --include "inputs/roadmaps/<ROADMAP>.pptx" --manual inputs/manual/manual_additions.csv
```

## Workflow

### Step 1: Verify Inputs

Before running, confirm:
1. **Roadmap PPTX** exists in `inputs/roadmaps/` - contains Jira ticket links by product area
2. **Manual additions CSV** (optional) at `inputs/manual/manual_additions.csv` - for tickets not in roadmap
3. **Environment** - `.env` file has JIRA_* and ANTHROPIC_API_KEY credentials

### Step 2: Validate (Recommended First)

Run validation to see which features will be included without generating notes:

```bash
releasebot validate <VERSION> --include "inputs/roadmaps/<ROADMAP>.pptx"
```

**Output**: `outputs/reports/<VERSION>_validation_report.md` showing:
- Shipped features (included in release notes)
- Pushed features (moved to future release)
- Not ready features (excluded)

Review the report before building.

### Step 3: Build Release Notes

```bash
releasebot build <VERSION> -p ENG --include "inputs/roadmaps/<ROADMAP>.pptx"
```

**Outputs**:
- `release_notes/<VERSION>.html` - Final customer-facing release notes
- `data/jira-<VERSION>.json` - Raw Jira data cache

## Input File Locations

| Input Type | Location | Format |
|------------|----------|--------|
| Roadmap | `inputs/roadmaps/*.pptx` | PowerPoint with Jira links |
| Manual tickets | `inputs/manual/manual_additions.csv` | CSV: `ticket_key,product_area,category,description` |
| Knowledge base | `inputs/knowledge-base/*.json` | Optional historical context |

## Output File Locations

| Output Type | Location |
|-------------|----------|
| Release notes | `release_notes/<VERSION>.html` |
| Validation report | `outputs/reports/<VERSION>_validation_report.md` |
| Jira data cache | `data/jira-<VERSION>.json` |

## Version Format

Use semantic versioning: `X.Y.Z` (e.g., `16.15.0`, `26.1.0`)

The version must match Jira's `fixVersion` field for ticket validation.

## Validation Rules

The tool uses 5 smart rules to determine if features shipped:

1. **Standard**: Status=Closed/Done/Resolved AND fixVersion matches
2. **Virtual Edge**: Status=Closed AND fixVersion starts with "VE-"
3. **Ready for QA**: Status="Ready for QA" AND fixVersion matches
4. **Closed without fixVersion**: Status=Closed AND no fixVersion (assumed shipped)
5. **PM/FR via Links**: PM/FR tickets validated through linked ENG tickets

## Troubleshooting

**CLI not found**: Reinstall with `.venv/bin/pip install -e .`

**Broken venv**: Recreate with `rm -rf .venv && python3 -m venv .venv && .venv/bin/pip install -e .`

**Jira auth errors**: Verify `.env` has valid `JIRA_API_TOKEN` from https://id.atlassian.com/manage-profile/security/api-tokens

**No AI summaries**: Verify `ANTHROPIC_API_KEY` in `.env`

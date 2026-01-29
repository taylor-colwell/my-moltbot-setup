# TDM Sales Deck Analysis: Slide Patterns & Storytelling

This document analyzes how the TDM Sales Deck (200+ slides) tells the Elisity technical story, documenting patterns for AI-assisted slide creation.

---

## Narrative Arc (Story Structure)

The deck follows a deliberate progression from problem → solution → proof:

### Act 1: Problem & Positioning (Slides 1-15)
1. **Cover + Social Proof** - Customer quote, growth metrics, logos
2. **The Legacy Problem** - Why traditional approaches fail (802.1X, VLANs, NAC, overlays)
3. **What's Changing** - Modern enterprise realities
4. **Why Elisity** - Core value proposition

### Act 2: Architecture Deep-Dive (Slides 3-35)
5. **High-Level Architecture** - "No Agents, No Hardware, Cloud Delivered"
6. **Component Breakdown** - VE, VEN, CCC explained individually
7. **Deployment Options** - VM, Cloud, Switch-hosted
8. **Competitive Differentiation** - Elisity vs 802.1X, VXLAN, TrustSec/SDA
9. **Process Flows** - Discovery → Classification → Enforcement
10. **Policy Constructs** - Policy Groups, Policy Sets, Distribution Zones
11. **Scale & Operations** - Learning/Simulation/Activation workflow

### Act 3: Integration Ecosystem (Slides 38-66)
12. **Partner Slides** - Templated integration flows (Claroty, Armis, ServiceNow, CrowdStrike, etc.)
13. **IdentityGraph Enrichment** - How each connector adds value
14. **Trust & Risk Context** - EDR, MDM, CMDB integration patterns

### Act 4: Technical Implementation (Slides 67-84)
15. **Vendor-Specific Details** - Cisco, Arista, Juniper configurations
16. **Discovery & Policy Flows** - Per-vendor technical diagrams
17. **Connectivity Requirements** - Port/protocol diagrams per vendor
18. **Wireless Designs** - WLC integration patterns

### Act 5: Use Cases & Industry (Slides 85+)
19. **Workflow Slides** - Classification remediation, adoption acceleration
20. **Industry-Specific** - Healthcare mixed environment, manufacturing

---

## Slide Type Patterns

### Pattern 1: Architecture Diagram
**Layout:** Blank canvas (Layout 41 or 36-39)
**Structure:**
- Eyebrow: Category (e.g., "Elisity Architecture")
- Headline: Specific topic
- Central diagram with icons arranged spatially
- Labels on/near icons
- Arrows showing data/policy flow
- Numbered steps for process flows

**Example Elements:**
```
Cloud Control Center (top center)
    ↓ HTTPS
Virtual Edge (middle)
    ↓ Policy/Telemetry
Virtual Edge Nodes / Switches (bottom layer)
    ↓
Devices (various icons at bottom)
```

### Pattern 2: Comparison Slide (Elisity vs X)
**Layout:** Two-column or split layout
**Structure:**
- Left side: Legacy approach (with ❌ or issues highlighted)
- Right side: Elisity approach (with ✓ or benefits)
- "Why It Doesn't Scale" section
- "Elisity IdentityGraph™" solution callout

**Consistent Elements:**
- "The Legacy Model" box
- "Why It Doesn't Scale" bullet points
- "Elisity IdentityGraph™" solution summary

### Pattern 3: Process Flow (Numbered Steps)
**Layout:** Horizontal or circular flow
**Structure:**
- Steps numbered 1-6 (typical)
- Each step has icon + brief description
- Arrows connecting steps
- Cycle icon (↻) for continuous processes

**Standard 6-Step Flow:**
1. Device attaches to network
2. Assets are discovered/enriched
3. Assets are classified into Policy Groups
4. Policy is sent to Virtual Edge
5. Policy is distributed to enforcement points
6. Continuous verification (cycle back)

### Pattern 4: Integration Partner Slide
**Layout:** Templated diagram (reused across partners)
**Structure:**
- Partner logo (top left or prominent)
- Same 6-step flow diagram
- Partner-specific text in steps 2-3
- "Better Together" value propositions (3 bullets)

**Templated Text Pattern:**
- "Assets are enriched by [PARTNER] within IdentityGraph™"
- "Assets are classified into Policy Groups using data from [PARTNER]"
- "[PARTNER] enrichment initiated"

### Pattern 5: Component Deep-Dive
**Layout:** Headline + diagram
**Structure:**
- Component icon (large, centered or left)
- Feature bullets around/beside the icon
- Technical details in organized lists
- Deployment options or capabilities

### Pattern 6: Policy Construct Explanation
**Layout:** Visual hierarchy showing relationships
**Structure:**
- Policy Groups → Policy Group Labels → Policy Sets → Site Labels
- Visual groupings with boxes/containers
- Match criteria examples in callout boxes
- Color coding for different policy types

### Pattern 7: Scale/Technical Specs
**Layout:** Data tables or spec lists
**Structure:**
- Hardware limits in tables
- Distribution Zone diagrams
- Latency/scale numbers
- Configuration snippets (code blocks)

### Pattern 8: Connectivity Requirements
**Layout:** Simple network diagram
**Structure:**
- Three-tier: Cloud → VE → Infrastructure
- Port/protocol labels on connections
- Directional arrows (inbound/outbound)
- Vendor-specific notes

---

## Visual Design Patterns

### Icon Usage
- **Elisity Products:** CCC, VE, VEN icons consistently used
- **Infrastructure:** Switches (Cisco, Arista, Juniper logos), WLCs, firewalls
- **Devices:** Generic device groups, PLCs, cameras, phones, computers
- **Cloud:** AWS, Azure, GCP logos for cloud deployments
- **Security:** Shield icons for security profiles, policy icons
- **Locations:** Building icons for sites/campuses

### Color Coding
- **Elisity Blue/Green gradient:** Headers, emphasis boxes
- **Deep Blue (#053242):** Text, headers
- **True Blue (#54B9F1):** Accents, connections
- **Red/Orange:** Warning, legacy issues, "doesn't scale"
- **Green:** Success, checkmarks, "Elisity approach"

### Spatial Arrangement
- **Vertical hierarchy:** Cloud → Edge → Devices (top to bottom)
- **Horizontal flow:** Left to right for processes
- **Grouped clusters:** Devices grouped by type or location
- **Connection lines:** Arrows with protocol labels

### Text Patterns
- **Eyebrow:** ALL CAPS, short category label
- **Headlines:** Bold, action-oriented
- **Body text:** Concise bullets, 3-5 per section
- **Callout boxes:** Highlighted key concepts
- **Footer:** © 2025 Elisity. Confidential for internal distribution only.

---

## Content Patterns

### Consistent Terminology
- "Elisity IdentityGraph™" (always with ™)
- "Cloud Control Center" or "CCC"
- "Virtual Edge" and "Virtual Edge Node"
- "Policy Groups" (not "device groups" or "segments")
- "Match Criteria" (for classification rules)
- "Distribution Zones" (for scale architecture)

### Value Proposition Phrases
- "No agents, no hardware, cloud-delivered"
- "Identity-based microsegmentation"
- "Enforce at the network edge"
- "Without touching underlying network architecture"
- "Real-time policy distribution"
- "Works across any vendor"

### Problem Statements
- "Traditional approaches... were built for static, managed environments"
- "Fragile, require intensive coordination"
- "Break down in hybrid, heterogeneous, or IoT-heavy networks"
- "Can't rely on enforcement at a single chokepoint"

### Differentiation Points
- vs 802.1X: No supplicants, works with unmanaged devices
- vs VXLAN: No overlays, no underlay dependency
- vs TrustSec/SDA: Works across vendors, no fabric required
- vs NAC: Continuous verification, not point-in-time

---

## Slide Building Workflow

### For Architecture Diagrams:
1. Start with Layout 41 (Light_Headline_01)
2. Add eyebrow + headline
3. Place CCC icon at top
4. Add VE layer in middle
5. Add infrastructure icons (switches, WLCs)
6. Add device icons at bottom
7. Draw connection arrows
8. Add step numbers and labels
9. Include protocol/port labels on connections

### For Comparison Slides:
1. Use two-column structure
2. Left: "Legacy Model" with issues
3. Right: "Elisity" with solutions
4. Add "Why It Doesn't Scale" section
5. Include IdentityGraph callout

### For Integration Partner Slides:
1. Copy existing integration template
2. Replace partner logo
3. Update partner name in text
4. Adjust specific enrichment attributes
5. Update "Better Together" bullets

### For Technical Flow Slides:
1. Use 6-step numbered flow
2. Start with device attachment
3. Show enrichment/classification
4. Policy distribution to VE
5. Enforcement at infrastructure
6. Continuous verification loop

---

## Key Takeaways for AI Slide Generation

1. **Reuse Patterns** - Integration slides follow identical templates
2. **Consistent Iconography** - Same icons represent same concepts throughout
3. **Hierarchical Layout** - Cloud → Edge → Devices is standard
4. **Numbered Flows** - 6 steps is the standard for process explanations
5. **Comparison Format** - Legacy (left/bad) vs Elisity (right/good)
6. **Value Props Repeated** - Core messages reinforced across slides
7. **Vendor-Neutral Core** - Same concepts apply across Cisco, Arista, Juniper
8. **Visual Consistency** - Colors, fonts, layouts maintain brand

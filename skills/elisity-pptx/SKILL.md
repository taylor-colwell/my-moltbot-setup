---
name: elisity-pptx
description: "Elisity-branded PowerPoint presentation creation, editing, and analysis. Creates on-brand presentations using Elisity's official colors, typography, master slide templates, and network security icon library. Use for: (1) Creating new Elisity-branded presentations, (2) Transforming documents/diagrams into presentations, (3) Working with Elisity master slide layouts, (4) Using Elisity's network security icon library."
license: Proprietary - Elisity, Inc.
---

# Elisity PPTX Creation, Editing, and Analysis

## Overview

This skill creates professional, on-brand Elisity presentations. It includes:
- **Elisity Master Slides Template** (45 layouts)
- **Elisity Icon Library** (48 network security SVG icons)
- **Elisity Brand Guidelines** (colors, typography, style)

A user may ask you to create, edit, or analyze presentations. A .pptx file is a ZIP archive containing XML files and resources that you can read or edit.

## Reference Documentation

| Document | Description |
|----------|-------------|
| [`TDM-PATTERNS.md`](TDM-PATTERNS.md) | **Slide patterns & storytelling from TDM Sales Deck** |
| [`LAYOUTS.md`](LAYOUTS.md) | Complete guide to all 45 slide layouts with recommendations |
| [`ELEMENTS.md`](ELEMENTS.md) | Element library index: icons, diagrams, partner logos |
| [`icons/ICONS.md`](icons/ICONS.md) | SVG icon library reference |
| [`html2pptx.md`](html2pptx.md) | HTML to PPTX conversion workflow |
| [`ooxml.md`](ooxml.md) | OOXML editing for existing presentations |

**For manual diagram building**: Use blank canvas layouts (41, 36-39, 43) and import elements from the element library. See LAYOUTS.md for layout selection and ELEMENTS.md for available icons.

## Elisity Brand Quick Reference

### Colors

| Name | HEX | RGB | Use |
|------|-----|-----|-----|
| Deep Blue | `#053242` | 5, 50, 66 | Dark backgrounds, headers |
| Elisity Green | `#0B6280` | 11, 98, 128 | Primary brand color |
| True Blue | `#54B9F1` | 84, 185, 241 | Accent, highlights |
| New Blue | `#65F1FC` | 101, 241, 252 | Bright accent |
| Easy Green | `#B5FC7B` | 181, 252, 123 | Bright accent |
| White | `#FFFFFF` | 255, 255, 255 | Light backgrounds |

### Typography

- **Primary Font:** Inter (Google Font)
- **Headlines:** Inter Extra Bold (800)
- **Subheadings:** Inter Medium (500)
- **Body Text:** Inter Regular (400)
- **Eyebrow:** Inter Medium, ALL CAPS
- **Fallback:** Arial, Helvetica

### Brand Essence

"Confidently Cool" — purposeful, precise, bold, intentional, clean design

## Elisity Master Slide Layouts

The template at `templates/elisity-master-slides.pptx` includes 45 professional layouts. For detailed layout selection guidance, see [`LAYOUTS.md`](LAYOUTS.md).

Key layouts for manual diagram building:
| Layout | Name | Best For |
|--------|------|----------|
| 41 | Light_Headline_01 | Standard slides with eyebrow + headline |
| 42 | Light_Headline_02 | Alternate headline style |
| 36-39 | Light_No-Headline variants | Full canvas, no header |
| 43 | Light_Blank_01 | Blank with brand elements |

### Cover & Section Slides
| Index | Name | Use |
|-------|------|-----|
| 19 | Light_Cover Slide | Main presentation cover |
| 20 | Light_Cover Slide+Presenter | Cover with presenter info |
| 21 | Light_Cover Slide + Subheader | Cover with subtitle |
| 24 | Light_Cover Logo | Logo-focused cover |
| 25 | Light_Section Slide | Section dividers |
| 34 | Light_ClosingSlide | Final slide |

### Content Layouts
| Index | Name | Use |
|-------|------|-----|
| 0-1 | Light_Headline+Text | Standard content |
| 2 | Light_Title+Two_Column_Text | Two columns |
| 3 | Light_Half Page+TwoColumn w/Headline | Half-page with columns |
| 4 | Light_Two ColumnText + Highlight Text Box | Featured content |
| 5-6 | Light_2Column/3Column w/ Image | Content with images |
| 7-8 | Light_Title+Blank | Flexible layouts |
| 14-15 | Light_Text-3_Column | Three-column text |
| 28-29 | Light_FourColumn+Outline/Color | Four columns |
| 30-33 | Light_SideColumn/HalfColumn variants | Asymmetric layouts |

### Data & Statistics
| Index | Name | Use |
|-------|------|-----|
| 9-10 | Light_Text+Table / Light_Table | Tables |
| 11-12 | Light_Four/Three_Statistics | Key metrics |
| 13 | Dark_Two_Statistics | Dark stat callouts |
| 26-27 | Light_Timeline_Checkmarks/Blue | Timelines |

### Team & Special
| Index | Name | Use |
|-------|------|-----|
| 17-18 | Light_Team_Cards / Light_Team_6Person | Team slides |
| 22-23 | Light_Table of Contents variants | Navigation |
| 16 | Light_3_Column_Text+Checks | Checklists |
| 35-38 | Light_No-Headline variants | Full content area |

## Elisity Element Library

For comprehensive element documentation including slide-embedded icons and partner logos, see [`ELEMENTS.md`](ELEMENTS.md).

### SVG Icon Library

Located in `icons/`, 48 SVG icons for network security diagrams:

### Infrastructure
- `router.svg`, `switch.svg`, `firewall.svg`, `switch-firewall.svg`
- `wireless-ap.svg`, `wireless-router.svg`, `wireless-lan-controller.svg`
- `server.svg`, `data-center.svg`, `cloud.svg`, `internet.svg`

### Cloud Providers
- `AWS.svg`, `Azure.svg`, `GCP.svg`

### Elisity Products
- `cloud-control-center.svg` - Elisity Cloud Control Center
- `virtual-edge.svg` - Elisity Virtual Edge
- `virtual-edge-node.svg` - Elisity Virtual Edge Node
- `virtual-edge-vm.svg` - Virtual Edge VM

### Devices
- `laptop.svg`, `desktop-computer.svg`, `server.svg`
- `printer.svg`, `ip-phone.svg`, `smart-TV.svg`, `camera.svg`
- `generic-device.svg`, `device-group.svg`, `virtual-machine.svg`

### Users & Identity
- `user.svg`, `users.svg`, `IDP.svg`, `NAC.svg`, `ad-agent.svg`

### Security & Policy
- `policy.svg`, `policy2.svg`, `policies.svg`, `security-profile.svg`

### Locations
- `campus.svg`, `branch.svg`, `hospital.svg`, `factory.svg`, `data-center.svg`

### Industrial/Medical (OT/IoMT)
- `plc.svg`, `hvac.svg`, `robot.svg`, `eng-workstation.svg`
- `ct-scanner.svg`, `EHR-server.svg`

### Other
- `application.svg`, `data.svg`

### Element Library Deck (Copy/Paste Elements)

The `templates/elisity-element-library.pptx` contains 9 slides of pre-built elements:
- **Slide 1**: Main icon library (60+ elements)
- **Slide 2**: Partner logos and extended icons
- **Slides 4-7**: Network diagram elements and device icons
- **Slides 8-9**: Combined elements and variations

These elements can be copied directly into new slides for diagram building. See [`ELEMENTS.md`](ELEMENTS.md) for complete catalog.

### Using SVG Icons in Presentations

**CRITICAL**: SVG icons must be rasterized to PNG before use in presentations:

```javascript
const sharp = require('sharp');

// Rasterize SVG to PNG at 2x resolution
await sharp('icons/virtual-edge-node.svg')
  .resize(200, 200)
  .png()
  .toFile('workspace/virtual-edge-node.png');
```

## Reading and Analyzing Content

### Text Extraction
```bash
python -m markitdown path-to-file.pptx
```

### Raw XML Access
For comments, speaker notes, layouts, animations, design elements:

```bash
python ooxml/scripts/unpack.py <office_file> <output_dir>
```

**Key file structures:**
- `ppt/presentation.xml` - Main presentation metadata
- `ppt/slides/slide{N}.xml` - Individual slide contents
- `ppt/notesSlides/notesSlide{N}.xml` - Speaker notes
- `ppt/slideLayouts/` - Layout templates
- `ppt/slideMasters/` - Master slide templates
- `ppt/theme/` - Theme and styling

## Creating New Presentations (From Scratch)

Use the **html2pptx** workflow with Elisity brand guidelines.

### Design Requirements

**CRITICAL**: Always use Elisity brand colors and typography:
- Primary colors: Deep Blue (#053242), Elisity Green (#0B6280)
- Accents: True Blue (#54B9F1), New Blue (#65F1FC), Easy Green (#B5FC7B)
- Font: Inter (Extra Bold for headlines, Regular for body)
- Style: Clean, professional, "Confidently Cool"

### Workflow

1. **MANDATORY**: Read [`html2pptx.md`](html2pptx.md) completely
2. Create HTML file for each slide with Elisity styling
3. Rasterize any icons using Sharp before including in HTML
4. Convert HTML to PPTX using `scripts/html2pptx.js`
5. **Visual validation**: Generate thumbnails and inspect

```bash
python scripts/thumbnail.py output.pptx workspace/thumbnails --cols 4
```

### Elisity HTML Slide Template

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;800&display=swap');

    body {
      font-family: 'Inter', Arial, sans-serif;
      margin: 0;
      padding: 40px;
      background: #FFFFFF;
      color: #053242;
    }

    h1 {
      font-weight: 800;
      font-size: 36pt;
      color: #053242;
      margin-bottom: 20px;
    }

    h2 {
      font-weight: 500;
      font-size: 24pt;
      color: #0B6280;
    }

    p, li {
      font-weight: 400;
      font-size: 14pt;
      line-height: 1.5;
    }

    .accent {
      color: #54B9F1;
    }

    .highlight {
      background: linear-gradient(135deg, #0B6280, #54B9F1);
      color: white;
      padding: 20px;
      border-radius: 8px;
    }
  </style>
</head>
<body>
  <!-- Slide content here -->
</body>
</html>
```

## Creating Presentations from Elisity Template

**Recommended approach** for consistent, on-brand presentations.

### Workflow

1. **Extract and analyze template**:
   ```bash
   python -m markitdown templates/elisity-master-slides.pptx > template-content.md
   python scripts/thumbnail.py templates/elisity-master-slides.pptx workspace/template-thumbs
   ```

2. **Create template inventory** at `template-inventory.md` documenting all 39 layouts

3. **Create outline** matching content to appropriate layouts:
   - Cover slides: indices 19-21, 24
   - Content: indices 0-8, 14-15, 28-33
   - Statistics: indices 11-13
   - Section dividers: index 25
   - Closing: index 34

4. **Rearrange slides**:
   ```bash
   python scripts/rearrange.py templates/elisity-master-slides.pptx working.pptx 19,0,0,11,25,0,34
   ```

5. **Extract text inventory**:
   ```bash
   python scripts/inventory.py working.pptx text-inventory.json
   ```

6. **Generate replacement content** and save to `replacement-text.json`

7. **Apply replacements**:
   ```bash
   python scripts/replace.py working.pptx replacement-text.json output.pptx
   ```

## Editing Existing Presentations

### Workflow

1. **MANDATORY**: Read [`ooxml.md`](ooxml.md) completely
2. Unpack: `python ooxml/scripts/unpack.py <file> <output_dir>`
3. Edit XML files
4. Validate: `python ooxml/scripts/validate.py <dir> --original <file>`
5. Pack: `python ooxml/scripts/pack.py <input_dir> <output_file>`

## Creating Thumbnail Grids

```bash
python scripts/thumbnail.py presentation.pptx [output_prefix] [--cols 4]
```

- Default: 5 columns, max 30 slides per grid
- Range: 3-6 columns
- Slides are zero-indexed

## Converting Slides to Images

```bash
# PPTX to PDF
soffice --headless --convert-to pdf presentation.pptx

# PDF to JPEG
pdftoppm -jpeg -r 150 presentation.pdf slide
```

## Code Style Guidelines

- Write concise code
- Avoid verbose variable names
- Avoid unnecessary print statements

## Dependencies

Required (should be pre-installed):

- **markitdown**: `pip install "markitdown[pptx]"`
- **pptxgenjs**: `npm install -g pptxgenjs`
- **playwright**: `npm install -g playwright`
- **react-icons**: `npm install -g react-icons react react-dom`
- **sharp**: `npm install -g sharp`
- **LibreOffice**: For PDF conversion
- **Poppler**: `poppler-utils` for pdftoppm
- **defusedxml**: `pip install defusedxml`

## Product Terminology

When creating Elisity presentations, use correct product names:

- **Elisity Platform** (not "Elisity product")
- **Elisity IdentityGraph™** (always include ™)
- **Elisity Cloud Control Center**
- **Elisity Virtual Edge**
- **Elisity Virtual Edge Node**
- **Elisity Dynamic Policy Engine**
- **Elisity Intelligence**

**Industry Terms:**
- Microsegmentation (not micro-segmentation)
- Zero Trust
- Identity-based microsegmentation
- IT/IoT/OT/IoMT devices

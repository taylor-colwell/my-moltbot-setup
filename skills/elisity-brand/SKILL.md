---
name: elisity-brand
description: Applies Elisity's official brand colors, typography, and writing style to any artifact. Use when brand guidelines, visual formatting, corporate identity, or Elisity design standards apply. Ensures consistent "Confidently Cool" brand essence across all materials.
license: Proprietary - Elisity, Inc.
---

# Elisity Brand Styling

## Overview

This skill provides Elisity's official brand identity, style resources, and writing guidelines. Use it to ensure all materials reflect Elisity's professional, authoritative presence in the microsegmentation and Zero Trust security space.

**Keywords**: Elisity, branding, corporate identity, visual identity, post-processing, styling, brand colors, typography, microsegmentation, Zero Trust, network security

## Brand Essence

**"Confidently Cool"** — Everything we do is with purpose, precision, and boldness. Our style is intentional and thoughtful, with clean design that conveys authority and trust.

## Brand Guidelines

### Color Palette

Our color palette conveys authority and trust while adding fresh, dynamic energy. These analogous colors blend smoothly from deep to bright, creating harmonious flow.

**Primary Colors:**

| Name | HEX | RGB | Use |
|------|-----|-----|-----|
| Deep Blue | `#053242` | 5, 50, 66 | Primary dark backgrounds, headers |
| Elisity Green | `#0B6280` | 11, 98, 128 | Primary brand color, accents |
| True Blue | `#54B9F1` | 84, 185, 241 | Secondary accent, highlights |

**Accent Colors:**

| Name | HEX | RGB | Use |
|------|-----|-----|-----|
| New Blue | `#65F1FC` | 101, 241, 252 | Bright accent, callouts |
| Easy Green | `#B5FC7B` | 181, 252, 123 | Bright accent, success states |
| White | `#FFFFFF` | 255, 255, 255 | Backgrounds, text on dark |

**Color Usage Rules:**
- Use black text on light backgrounds
- Use white text on dark backgrounds
- Grey text or lighter shades of black for secondary content only
- Deep Blue and Elisity Green for primary elements
- New Blue and Easy Green for highlights and accents

### Typography

**Primary Typeface: Inter** (Google Font - https://fonts.google.com/specimen/Inter)

Inter is carefully designed for screens and provides a clean, crisp typeface for readers to process.

| Element | Font | Weight | Notes |
|---------|------|--------|-------|
| Headlines | Inter | Extra Bold (800) | Primary headlines |
| Subheadings | Inter | Medium (500) | Supporting titles below headlines |
| Body Text | Inter | Regular (400) | All paragraph text |
| Eyebrow | Inter | Medium (500) | ALL CAPS, category labels above sections |

**Typography Rules:**
- Left alignment is prioritized for headlines, subheadings, and body text
- Use sentence-style capitalization (capitalize first word, lowercase rest)
- Eyebrow text is always ALL CAPS
- Maintain clear visual hierarchy through size, weight, and color

**Fallback Fonts:**
- Headings: Arial (if Inter unavailable)
- Body: Helvetica, Arial (if Inter unavailable)

## Company Information

### Official Names

- **Company Name:** Elisity, Inc.
- **Product Name:** Elisity Platform

### Product Feature Names (Always Capitalize)

- Elisity IdentityGraph™
- Elisity Cloud Control Center
- Elisity Virtual Edge
- Elisity Virtual Edge Node
- Elisity Dynamic Policy Engine
- Elisity Intelligence

### Company Boilerplate

> Elisity is a leap forward in network segmentation architecture and is leading the enterprise effort to achieve Zero Trust maturity, proactively prevent security risks, and reduce network complexity. Designed to be implemented in weeks, without downtime, upon implementation, the platform rapidly discovers every user, workload, and device on an enterprise network and correlates comprehensive insights into the Elisity IdentityGraph™. This empowers teams with the context needed to automate classification and apply dynamic security policies to any device wherever and whenever it appears on the network. These granular, identity-based microsegmentation security policies are managed in the cloud and enforced using your existing network switching infrastructure in real-time, even on ephemeral IT/IoT/OT devices. Founded in 2019, Elisity has a global employee footprint and a growing number of customers in the Fortune 500.

### Category Terms

- Microsegmentation
- Network Segmentation
- Identity-based Microsegmentation
- Zero Trust Segmentation
- Universal ZTNA (Gartner context only)

## Writing Style Guide

Elisity follows the **Associated Press Stylebook (AP Style)** with specific company conventions.

### Technology Terms

| Correct | Incorrect |
|---------|-----------|
| agentless | agent-less |
| antivirus | anti-virus |
| anti-malware | antimalware |
| cyberattack | cyber attack |
| cybersecurity | cyber security |
| data sheet | datasheet |
| data center | datacenter |
| database | data base |
| e-book | ebook, eBook |
| endpoint | end point |
| login (noun) | log-in |
| log in (verb) | login |
| Microsegmentation | micro-segmentation |
| on-premises | on-premise, on-prem |
| on-site, off-site | onsite, offsite |
| runbook | run book |
| white paper | whitepaper |
| webcam, webcast, webinar | web cam, web cast |
| webpage, website | web page, web site |

### Capitalization Rules

- Use sentence-style capitalization in titles and headings
- Always capitalize product names (Elisity IdentityGraph™, Elisity Cloud Control Center, etc.)
- Capitalize first word after a colon if it starts a complete sentence
- Lowercase "beta" unless part of an official product name

### Number Formatting

- Spell out numbers one through nine
- Use numerals for 10 and higher
- Always use numerals for: addresses, ages, currency, dates, times, percentages, measurements
- Never use st, nd, rd, th with dates (December 25, not December 25th)

### Punctuation

- Use Oxford comma (easy, efficient, and secure)
- Single space before and after em dashes
- No space before or after en dashes in ranges (15–20%)
- Use "percent" (US) not "per cent" (UK)

## Logo Usage

### Logo Color Rules

- Use solid black logo on light backgrounds and gradients
- Use solid white logo on dark backgrounds
- Never place logo over colors without enough contrast
- Never remove or modify logo elements
- Elisity logo always appears first when paired with partner logos

## Features

### Smart Font Application

- Applies Inter Extra Bold to headings (24pt and larger)
- Applies Inter Regular to body text
- Automatically falls back to Arial if Inter unavailable
- Preserves readability across all systems

### Text Styling

- Headlines (24pt+): Inter Extra Bold
- Subheadings: Inter Medium
- Body text: Inter Regular
- Eyebrow text: Inter Medium, ALL CAPS
- Smart color selection based on background

### Shape and Accent Colors

- Non-text shapes use Elisity brand accent colors
- Primary accent: Elisity Green (#0B6280)
- Secondary accents: True Blue (#54B9F1), New Blue (#65F1FC)
- Cycles through accents for visual interest while staying on-brand

## Technical Details

### Font Management

- Uses system-installed Inter font when available
- Provides automatic fallback to Arial/Helvetica
- For best results, pre-install Inter font family
- Download from: https://fonts.google.com/specimen/Inter

### Color Application (python-pptx)

```python
from pptx.util import RGBColor

# Elisity Brand Colors
DEEP_BLUE = RGBColor(5, 50, 66)        # #053242
ELISITY_GREEN = RGBColor(11, 98, 128)  # #0B6280
TRUE_BLUE = RGBColor(84, 185, 241)     # #54B9F1
NEW_BLUE = RGBColor(101, 241, 252)     # #65F1FC
EASY_GREEN = RGBColor(181, 252, 123)   # #B5FC7B
WHITE = RGBColor(255, 255, 255)        # #FFFFFF
```

### CSS Color Variables

```css
:root {
  --elisity-deep-blue: #053242;
  --elisity-green: #0B6280;
  --elisity-true-blue: #54B9F1;
  --elisity-new-blue: #65F1FC;
  --elisity-easy-green: #B5FC7B;
  --elisity-white: #FFFFFF;
}
```

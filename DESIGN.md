# Matt Traces Archive — static information pages

## Target before implementation

A small personal-tool information site, not a sign-up screen or dashboard.
Use a white page, dark system text, one blue link color, and a readable single column.
At 402 × 874 and 1100 × 760, keep the same content order and final copy.

```text
Matt Traces Archive
Home    Privacy    Terms

Personal trace backups
Matt Traces Archive is a personal-use desktop tool.
It backs up the owner's own agent trace files to the owner's own Google Drive.

Private by purpose
The owner is the only user. Google Drive access is limited to files this app creates.

Privacy policy    Terms of service
```

Privacy uses the same frame with the title “Privacy policy”, followed by access,
use and storage, sharing, retention and revocation sections. Terms uses the title
“Terms of service”, followed by personal use, responsibility and availability.

## Contract

- Plain semantic HTML; no scripts, forms, accounts, analytics, external fonts or images.
- Shared navigation links to all three pages, with the current page marked.
- Native keyboard navigation, visible focus, underlined links, and 44px navigation targets.
- Body type 18px, line height 1.6; heading scale 30px/22px; maximum column width 42rem.
- 8px spacing grid; 24px phone gutters; no card boxes, decorative hero or animated elements.
- All content wraps without horizontal scrolling at 390px and when text is enlarged.
- Page titles are unique; page language is English; privacy is reachable from the home page.
- No personal identifiers beyond the app name; no public email address.
- No invented Google verification value. A comment in the home page head marks its future location.

## Identity

Always: plain-language purpose first; calm paper-and-ink layout; directly linked policies.
Never: marketing claims; sign-up or upload controls.

## Route map

- `/` → app description and policy links.
- `/privacy.html` → policy and Google Account access-revocation link.
- `/terms.html` → personal-use terms.

## Visual acceptance

Inspect the actual live pages at 390px and 1440px widths. Exercise links and keyboard focus;
screenshots alone do not prove navigation. Keep screenshots and interaction output outside the repo.
The task requests one pass, not an independent design/model review loop.

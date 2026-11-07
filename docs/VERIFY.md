# Verify the static site

Last live proof: 2026-11-07 — blocked — deployment not yet run

## Boundary

This verifies only public information pages. It does not prove Google domain ownership,
OAuth publication, token lifetime, or the backup tool's behavior.
See [FEATURES.md](FEATURES.md) and [../DESIGN.md](../DESIGN.md).

## Failure modes first

- The user-site repository already belongs to another site; do not overwrite it.
- Pages may be disabled, deployed from the wrong branch, or serving a stale commit.
- HTTPS, page paths, stylesheet links or policy navigation may fail.
- Copy may overstate access, omit revocation, expose identifiers, or contain a fake verification token.
- Small-screen text may overflow; keyboard focus or policy links may not work.
- Google may request additional account or brand checks after the site is published.

## Frozen done-check

All three exact HTTPS URLs must return HTTP 200 without authentication:

- https://mattsagentcal.github.io/
- https://mattsagentcal.github.io/privacy.html
- https://mattsagentcal.github.io/terms.html

Capture curl output, response bodies and headers in the task artifact directory.
Compare the served HTML and CSS to the source. Use the installed Playwright package
from `/Users/calstudio/.hermes/hermes-agent/node_modules/playwright` to open the live
home page, click Privacy, Terms and Home, and assert the resulting URL and heading.
Check no horizontal overflow at 390px and capture each page, plus home at 1440px.
Check keyboard focus reaches the navigation. Keep a Playwright trace and JSON receipt.
Run this as one live E2E journey; do not substitute unit tests or mock responses.

## Launch and doctor

No package install, build, local service, model or simulator is needed.
GitHub Pages serves static files from the `main` branch root.
Read-only preflight:

```sh
gh api user --jq .login
gh api repos/MattsAgentCal/MattsAgentCal.github.io/pages
git status --short
git worktree list
```

The account must be `MattsAgentCal`; do not change credentials.
Pages must report the expected HTTPS URL and source `main` at `/`.
The published commit must match the site source commit.

## Repeating the HTTP check

```sh
curl --proto '=https' --fail --silent --show-error --output /dev/null \
  --write-out '%{url_effective} HTTP %{http_code}\n' https://mattsagentcal.github.io/
curl --proto '=https' --fail --silent --show-error --output /dev/null \
  --write-out '%{url_effective} HTTP %{http_code}\n' https://mattsagentcal.github.io/privacy.html
curl --proto '=https' --fail --silent --show-error --output /dev/null \
  --write-out '%{url_effective} HTTP %{http_code}\n' https://mattsagentcal.github.io/terms.html
```

## Evidence and cleanup

The task handoff `RESULT.md` records the live output, exact publication commit,
artifact locations and the remaining Google account steps. Browser screenshots,
trace and response bodies stay outside the public repository.
Close the browser in a `finally` block, including on failure. Do not stop shared
browsers or services. Retain no process or local listener. GitHub Pages is the
requested continuing hosted artifact and stays enabled.

## Maintenance

After any HTML, CSS or verification-tag change, repeat the live HTTP check and
browser policy journey. Update this proof line to `clean`, `changed`, or `blocked`,
with the retained artifact path. Never label the Google account steps complete
without evidence from the Google account owner.

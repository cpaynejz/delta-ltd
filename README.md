# delta-ltd

Fixture that gates analytics injection behind explicit user consent. Tests Discovery against consent-mode-style sites. Default persona: **Delta Ltd** (the direct-gtag persona — Delta has no GTM container, only a GA4 stream).

**Live URL:** `https://cpaynejz.github.io/delta-ltd/`

## Test plan scenarios served

- TC-3.1.6 site behind cookie-banner consent
- TC-3.4.1 / TC-2.6.1 direct gtag.js (paste gtag loader in the consent-grant handler instead of the GTM snippet)
- Documents Discovery's behavior boundary on consent-gated tags

## How to configure

Edit `index.html` and replace the placeholder:

```js
var GTM_ID = '__GTM_CONTAINER_ID__';
```

with your real GTM container ID. Commit and push.

## Expected vs likely-actual behavior

- **Discovery without consent action:** GTM is NOT in the DOM (banner is showing). Discovery should report the site as having no GTM evidence.
- **Discovery if Playwright auto-clicks Accept:** depends on whether the probe interacts with banners (currently it does not). If it doesn't, document this as a known limitation.

This fixture is mostly useful for documenting what TraceConverge **cannot** detect today, rather than proving a happy-path. File a finding either way.

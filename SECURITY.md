# Security Policy

## Supported versions

| Version | Supported |
| ------- | --------- |
| 3.0.5 (this fork) | ✅ |
| 3.0.4 and earlier (upstream) | ❌ — unmaintained |

This fork exists because upstream WordPress Social Login is **closed on wordpress.org** and has
had no update since 2020-09-24. Fixes here are applied on a best-effort basis.

## Reporting a vulnerability

Please report security issues **privately** rather than in a public issue.

1. Use GitHub's private reporting: **Security → Report a vulnerability** on this repository.
2. If that is unavailable, contact the maintainer listed on the repository profile.

Please include:

- the affected version,
- a description of the issue and its impact,
- steps to reproduce,
- and any suggested fix or patch.

We aim to acknowledge reports within 5 business days.

## Known unfixed issues

Understood, documented, and not yet remediated. Patches are welcome.

| Area | Issue | Class |
| --- | --- | --- |
| Some admin components | State-changing admin actions without nonce verification | CSRF |
| Whole plugin | Upstream code base is unmaintained | Long-term risk |

### Reviewed and found not vulnerable

- **`redirect_to` spoofing / open redirect.** The `redirect_to` request parameter is passed to
  `wp_safe_redirect()` (`includes/services/wsl.authentication.php`), which validates the target
  against the site's allowed hosts and falls back to the admin URL. External destinations are not
  honoured. Reviewed 2026-10-11; no change required.
- **Filesystem access.** As of 3.0.5 the plugin contains no dynamic file reads or writes other than
  the log viewer, which is constrained by `sanitize_file_name()` and a `realpath()` containment
  check.

## Disclosure note

The arbitrary file read fixed in 3.0.5 was identified independently and is not covered by any
published advisory. It requires administrator-level access or a CSRF against an administrator,
but leads directly to disclosure of `wp-config.php` (database credentials, authentication salts)
and therefore to full site compromise. **If you run this plugin, upgrade to 3.0.5 immediately.**

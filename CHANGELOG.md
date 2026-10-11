# Changelog

All notable changes to this fork are documented here.
This project adheres to [Semantic Versioning](https://semver.org/).

## [3.0.5] — 2026-10-11

Security release. Forked from upstream WordPress Social Login **3.0.4**, the final upstream
release (2020-09-24). Upstream is closed on wordpress.org and receives no further updates,
so none of the issues below have an upstream fix.

### Fixed

- **Arbitrary file read / path traversal in the authentication log viewer**
  (`includes/admin/components/watchdog/index.php`).

  The `log_file` request parameter was passed unsanitised to `file_get_contents()`. An
  administrator — or any request able to CSRF an administrator, since the form carried no
  nonce — could therefore read arbitrary files on the server, for example:

  ```
  log_file=../../../../wp-config.php
  ```

  This exposed database credentials and authentication salts.

  Fix: `sanitize_file_name()` + `wp_unslash()` on the input, a `realpath()` containment check
  that only permits direct children of the WSL log directory, and `esc_attr()` / `esc_html()` /
  `esc_textarea()` on output.

- **Stored XSS via the `[wordpress_social_login_meta]` shortcode**
  (`includes/widgets/wsl.auth.widgets.php`).

  The `css_class` and `assets_base_url` shortcode attributes, and the `provider`, `identity`
  and `photourl` values read from linked provider accounts, were concatenated into HTML
  without escaping. Related to CVE-2023-4773 (Authenticated (Contributor+) Stored Cross-Site
  Scripting via Shortcode).

  Fix: `esc_attr()`, `esc_url()` and `esc_html()` on all output.

- **Reflected XSS on the provider loading screens**
  (`includes/widgets/wsl.loading.screens.php`).

  `$provider` was echoed into a JavaScript string literal and into a hidden input value, and
  `$provider_name` into the page heading, without escaping.

  Fix: `esc_js()`, `esc_attr()` and `esc_html()`.

### Changed

- Version string corrected. Upstream was inconsistent: the plugin header read `3.0.4` while
  the internal `WORDPRESS_SOCIAL_LOGIN_VERSION` constant read `3.0.3`. Both are now `3.0.5`.

### Known issues not fixed in this release

Tracked in [SECURITY.md](SECURITY.md). Patches are welcome.

- Several admin-side components perform state-changing actions without nonce verification (CSRF).
- `$_REQUEST['redirect_to']` is used without `wp_validate_redirect()` in
  `includes/services/wsl.authentication.php` and `includes/widgets/wsl.auth.widgets.php`
  (open-redirect class).
- The upstream code base is unmaintained; migrating to a maintained social-login provider is
  recommended for the long term.

## [3.0.4] — upstream baseline

Imported unmodified as the patching baseline. See the upstream project for earlier history.

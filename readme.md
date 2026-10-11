> ## ⚠️ Security fork — read this first
>
> This repository is a **security-patched fork** of
> [WordPress Social Login](https://wordpress.org/plugins/wordpress-social-login/) by
> [Miled](https://github.com/miled). Upstream is **closed on wordpress.org** and has had
> **no update since 2020-09-24**.
>
> **Fork version: 3.0.5** (based on upstream 3.0.4).
>
> | Issue fixed | File | Upstream fix |
> | --- | --- | --- |
> | Arbitrary file read / path traversal in the authentication log viewer | `includes/admin/components/watchdog/index.php` | none |
> | Stored XSS via the `[wordpress_social_login_meta]` shortcode (related to CVE-2023-4773) | `includes/widgets/wsl.auth.widgets.php` | none |
> | Reflected XSS on the provider loading screens | `includes/widgets/wsl.loading.screens.php` | none |
>
> See [CHANGELOG.md](CHANGELOG.md) for details, and [SECURITY.md](SECURITY.md) to report an issue.
>
> ### Fork provenance and licence
>
> Forked from upstream 3.0.4 and maintained independently. Changes are applied as small,
> reviewable commits — one commit per issue. No upstream code has been rewritten beyond the
> minimum needed to fix the issues above.
>
> Upstream is **MIT licensed**; that licence is unchanged and the upstream copyright notice
> — Copyright (C) 2011-2020 Mohamed Mrassi and contributors — is retained in
> [LICENSE](LICENSE), as the MIT licence requires.

---

## To the original author

This fork is not a takeover. It exists only because upstream is closed on wordpress.org and
has had no release since 2020-09-24, while the plugin still has tens of thousands of active
installs.

**If [Miled](https://github.com/miled) — or whoever maintains WordPress Social Login today —
would rather ship these fixes under the original project, that is entirely welcome.** The
patches are deliberately small and self-contained, one commit per issue, so they can be
cherry-picked, squashed, rewritten, or reimplemented in whatever form suits upstream:

```bash
git log --oneline 44fccab..main     # the three security fixes, one commit each
git format-patch 44fccab..main      # as mailbox patches, ready to apply or review
```

No permission, attribution, or credit is required — the MIT licence already permits this. If
upstream ever resumes releases, this fork will be marked superseded and pointed at the
official version.

---

## [WordPress Social Login](https://wordpress.org/plugins/wordpress-social-login/) 3.0.5

**WordPress Social Login** is a free and open source plugin made by the community, for the community.

Basically, WordPress Social Login allow your website visitors and customers to register and login via social networks such as twitter, facebook and google but it has much more to offer.

For more information about WordPress Social Login, refer to our [online user guide](http://miled.github.io/wordpress-social-login/).

![WSL Authentication Widget](https://raw.githubusercontent.com/miled/wordpress-social-login/master/assets/screenshot-1.png)

### Key Features

- No premium features.
- One-click social login.
- Absolute privacy of your website users data.
- Wide variety of identities providers.
- A highly customizable and fully extensible widgets.
- Easy-to-use and clean user interfaces.
- Contacts import from google, facebook, live, linkedin and vkontakte.
- User profiles and contacts management.
- Compatible with WordPress 3.0+, BuddyPress and bbPress.
- ACL-based security model.
- Provides a direct access to social networks apis.
- Modular design easily extended.
- Comprehensive documentation.

#### License

MIT — That's short for do whatever you want.

#### Thanks

Big thanks to everyone who have contributed to WordPress Social Login by submitting Patches, Ideas, Reviews and by Helping in the support forum.

#### Screenshots
![screenshot](https://raw.githubusercontent.com/miled/wordpress-social-login/master/assets/screenshot-2.png)
===
![screenshot](https://raw.githubusercontent.com/miled/wordpress-social-login/master/assets/screenshot-3.png)
===
![screenshot](http://miled.github.io/wordpress-social-login/assets/img/theme_fontawesome.png)
===
![screenshot](https://raw.githubusercontent.com/miled/wordpress-social-login/master/assets/screenshot-4.png)
=
![screenshot](https://raw.githubusercontent.com/miled/wordpress-social-login/master/assets/screenshot-5.png)
===
![screenshot](https://raw.githubusercontent.com/miled/wordpress-social-login/master/assets/screenshot-6.png)
===
![screenshot](https://raw.githubusercontent.com/miled/wordpress-social-login/master/assets/screenshot-7.png)
===
![screenshot](https://raw.githubusercontent.com/miled/wordpress-social-login/master/assets/screenshot-8.png)
===
![screenshot](https://raw.githubusercontent.com/miled/wordpress-social-login/master/assets/screenshot-9.png)

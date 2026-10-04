# Letters Home plugins

Export email, filter it locally, and upload it to a [Letters Home](https://sendlettershome.com) collection.

- **Mail Export** — guides Gmail labeling and Google Takeout.
- **Email Import** — filters a downloaded MBOX by address, with originals-only or both-direction selection. Requires Node.js 24+.

## Codex

```sh
codex plugin marketplace add bustertown/letters-home-plugins --ref main
codex plugin add letters-home-mail-export@letters-home
codex plugin add letters-home-email-import@letters-home
```

## Claude Code

```sh
claude plugin marketplace add bustertown/letters-home-plugins
claude plugin install letters-home-mail-export@letters-home
claude plugin install letters-home-email-import@letters-home
```

Install either or both, then restart your host. Try: “Help me export emails from one address and import them into Letters Home.”

## Privacy and setup

No Gmail API connection or Google credentials. Filtering runs locally in an approved folder; upload requires your authorization. Browser assistance can expose page information to your AI host. Original-only detection has limitations—review results before uploading.

See the [setup and privacy guide](GUIDE.md) for folder configuration, supported files, limits, and updates. This repository marketplace is separate from the official OpenAI and Anthropic directories.

[Support](https://sendlettershome.com/contact) · [Privacy](https://sendlettershome.com/privacy-policy) · [Terms](https://sendlettershome.com/terms-of-use)

First-party contents retain their copyright; no open-source license is granted. Bundled dependencies retain their [licenses](plugins/letters-home-email-import/THIRD-PARTY-NOTICES.txt).

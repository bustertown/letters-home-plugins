# Letters Home plugins

Two plugins help prepare saved emails for [Letters Home](https://sendlettershome.com):

| Plugin | Purpose | Requirements |
| --- | --- | --- |
| Letters Home Mail Export | Search Gmail, apply an export label, and request a selected Google Takeout download. | Manual guidance works in any host that loads the skill. Optional browser assistance requires host browser controls and your permission. |
| Letters Home Email Import | Filter a downloaded MBOX by address and your choice of originals only or both directions, then assist with collection upload. | Local Codex or Claude Code, Node.js 24+, an approved import folder, and a Letters Home collection. Browser upload assistance requires host browser and file controls. |

This is a repository marketplace. Adding it makes the plugins available for you to install; it does not connect your Google account. The plugins have not been approved for the OpenAI or Anthropic official directories.

## Install in Codex

Run in a terminal with a current Codex CLI:

```sh
codex plugin marketplace add bustertown/letters-home-plugins --ref main
codex plugin list --marketplace letters-home
codex plugin add letters-home-mail-export@letters-home
codex plugin add letters-home-email-import@letters-home
```

Install whichever plugins you need. Restart Codex and start a new chat after installation. The desktop Plugins view also lets you browse and install from the Letters Home source after adding it.

Try: “Help me label emails from one address and export them through Google Takeout.” For a downloaded MBOX, try: “Help me import original messages from one address into my Letters Home collection.”

The portable importer uses the host's plugin data directory as its approved folder. Ask the agent for that folder and place the raw MBOX there before filtering. If your Codex version uses the compatibility loader, set `LETTERS_HOME_IMPORT_DIR` to an absolute folder containing only the intended export, then restart Codex. For example, set the variable when launching the CLI:

```sh
LETTERS_HOME_IMPORT_DIR="$HOME/LettersHomeImport" codex
```

Create the folder first. GUI apps may not inherit terminal environment variables; use a current portable loader or configure that environment through the host. A missing approved folder produces an error rather than unrestricted filesystem access.

## Install in Claude Code

In a terminal:

```sh
claude plugin marketplace add bustertown/letters-home-plugins
claude plugin install letters-home-mail-export@letters-home
claude plugin install letters-home-email-import@letters-home
```

Use a current Claude Code release with plugin `userConfig` support. When enabling the importer, choose an absolute local email import folder when prompted. Put the exported raw MBOX in that folder. Use `/mcp` to check the local connection, then invoke `/letters-home-email-import:email-import` or `/letters-home-mail-export:prepare-gmail-export`.

## What happens to mail

The export skill guides Gmail and Google Takeout. You handle sign-in and security checks. With browser assistance, page information can be visible to your AI host; review its privacy controls before granting access. The skill can guide label selection and export requests but Google creates the archive and controls download availability.

The importer reads and copies selected mail locally. It sends counts and progress to the host, not message bodies; the address and file paths supplied as tool arguments are visible to the host/model. It requests no Gmail API OAuth scopes and holds no Google credentials or Letters Home browser cookies. Upload happens through the signed-in Letters Home website after the file and collection are authorized.

Original-only selection checks reply headers and conservative subject hints. It is not perfect thread reconstruction: replies missing those signals can pass. Review uncertain and unparseable counts before upload. Both-direction selection includes matching sender and recipient headers; Gmail conversation membership alone does not qualify a message.

Filter limits are 20 GiB input, 5 GiB output, and 10,000 selected messages. Large archives run in the background with progress polling. Original archives are preserved. Selected and crashed partial files remain on disk until you remove them; handled cancellation removes partial output.

Do not upload an untouched Takeout ZIP or an unfiltered All Mail archive. Takeout ZIPs can contain HTML and other files; extract and select the raw Mail MBOX before importing. PST and OLM exports are unsupported. The archive filter requires MBOX; EML can use the website's saved-email uploader separately.

The export skill and importer can be used together, but installing either does not give your host missing browser or desktop-file capabilities. A web-only host cannot run this local MCP process.

## Updates and support

```sh
codex plugin marketplace upgrade letters-home
claude plugin marketplace update letters-home
claude plugin update letters-home-email-import@letters-home
```

Refresh the marketplace, update installed plugins using the host's plugin manager, and restart the host after changing versions. Review updates before enabling newly requested access.

Support: [contact Letters Home](https://sendlettershome.com/contact) or support@sendlettershome.com. Include plugin version, host version, and sanitized error text. Do not send mail archives, subjects, private addresses, credentials, or screenshots containing private mail.

[Privacy policy](https://sendlettershome.com/privacy-policy) · [Terms of use](https://sendlettershome.com/terms-of-use). Bundled third-party licenses are retained in the importer's `THIRD-PARTY-NOTICES.txt`.

First-party plugin contents retain their existing copyright. This distribution does not grant an open-source license for those contents; third-party components retain the licenses in their notices.

# CodePress Sites

Publish a static website from your own AI conversation, migrate an authorized public page into editable source, and keep editing the site after claiming it in CodePress.

**Development preview, version 0.2.2.** These are public plugin source exports. This repository does not mean either platform has approved or published a directory listing. A production rehearsal has verified guest publishing, guest editing, browserless capture/migration and explicit browser claim. Final authenticated-edit permission elevation, complete review recordings and submission checks remain in progress. Never treat a queued update as published.

## Connect for development

The remote Streamable HTTP server is **https://api.codepress.dev/mcp/sites**.

- **Claude:** use a custom connector in Settings → Connectors, with this server URL. Use **sign in when needed** when offered. The plugin bundle is in [claude/](../claude/), with its manifest, connector configuration and two skills. The directory source folder is `claude` on the `distribution` branch.
- **ChatGPT:** add a development MCP connection using the same server URL and mixed anonymous/OAuth authentication where supported. The portable plugin source is in [openai/](../openai/). A ZIP upload must contain that folder's contents at its root; creating a development connection and installing a package are separate platform steps.

Guest discovery, publishing and migration do not require a CodePress account. Protected account and App tools request CodePress OAuth in the same connection. Select only the workspace you intend to authorize. A valid connection may need explicit additional permission before an edit can run; do not bypass that consent or create a second connector to obtain access.

## Try the workflow

1. Ask: **Build a one-page site for my bakery and put it live. I do not have a CodePress account.** The agent prepares static source, uploads it and explicitly publishes. It returns the confirmed live address, expiry and a separate private **Manage in CodePress** link.
2. Ask for a heading change and publication. Before claim, the site-scoped authority retained in this conversation can update the same address. Identical retries retain their original operation identifiers; a later failure must not cause another site to be created.
3. To migrate a page you own or are authorized to copy, give its public URL and ask to capture it into editable static source and publish a separate site. An agent with a browser can inspect it. The bounded server capture fallback supplies source material, not screenshots: the agent must say which checks did and did not run.
4. Open **Manage in CodePress** privately, sign in and explicitly confirm the free claim. The site becomes an ordinary App in your Personal workspace, retaining its public address and live content. Claiming is free and removes the guest expiry on that address. It does not purchase a subscription or start CodePress AI work.
5. Ask the same connected agent to edit and publish the claimed App. Complete its CodePress OAuth permission request. The agent reads current source and submits a complete static file set against the fresh source revision. It polls the update status and confirms publication only after success. Guest authority does not edit a claimed App.

**Keep management links and capabilities private.** A public site URL grants no edit or claim rights. Do not put private handoffs in shared screenshots, recordings, public pages, issues or logs.

## Supported content and limits

The service hosts static HTML, CSS and browser JavaScript, or static output from supported client builds. It does not run an always-on Python server or a database. The agent uses its own tools, model account and usage limits for generation and builds; model subscriptions do not transfer to CodePress.

For small sites, `upload_guest_site_files` accepts an **array** of up to 16 files, with up to 128 KiB of authored UTF-8 text and up to 4 MiB of same-site captured assets. It packages source/output server-side, so a shell, ZIP tool or compiler is not required for plain HTML. Publication is a separate explicit call. Additional HTML documents retain their exact document or directory routes. Follow the current live schemas and errors for authoritative limits.

Use `prepare_guest_site_creation` when the client cannot securely generate creation recovery material. Keep the returned private pair unchanged for creation and identical retries. Never invent a bearer secret.

Claimed static edits include every file that should remain. Retain unchanged authorized assets with the supported snapshot-bound source references; omitted files are removed from that App's next output. Custom source/build workflows use their normal App editing path.

Guest sites are removed at the expiry the service returns unless claimed. A claimed site stays free on its CodePress address. Custom domains are a separate optional CodePress account setting, outside this plugin's purchase-free workflow.

## Repository contents and provenance

[claude/](../claude/) and [openai/](../openai/) contain the maintained manifests, skills, brand mark, changelog, license and public setup instructions. Each folder has an `EXPORT.json` inventory with byte hashes and the canonical source revision. The root [EXPORT.json](../EXPORT.json) covers this complete public snapshot. Review credentials, private submission-state records, backend code and monorepo history are excluded.

The two skill sources are identical across the platform folders. These runtime files were exported from canonical revision `46edfcbaca1c120c9b5cc9ee45ec0241d3b8adae`; public documentation and subset inventories are adapted for this standalone repository. Release validation and directory acceptance remain separate from source availability.

This Claude source export adds directory-only metadata: its manifest references the existing, unmodified 512×512 CodePress PNG at [.claude-plugin/icon.png](.claude-plugin/icon.png) as `./.claude-plugin/icon.png`, relative to this plugin root, and explicitly sets `privacyPolicyUrl` to `https://codepress.dev/privacy`. Skills, MCP configuration, the OpenAI export and functional version 0.2.2 retain their prior bytes. The canonical revision and input hash remain provenance; this adapted public source is not byte-identical to the already delivered full ZIPs and does not replace or redefine those archives. Directory acceptance must be checked against the exact public commit before the first portal save or submission.

## Privacy and support

Publish only content you intend to make public. Editable source and management authority remain private. Only migrate sources you are authorized to use.

[Privacy policy](https://codepress.dev/privacy) · [Terms](https://codepress.dev/tos) · [Support](https://codepress.dev/support) · [CodePress](https://codepress.dev/)

Contact **support@codepress.dev** with a safe error code and public site identifier. Omit credentials and private management links.

## License

The existing [MIT license](LICENSE) applies only to the exported files enumerated in this repository's inventories. It grants no rights to other CodePress source, the hosted service or trademarks.

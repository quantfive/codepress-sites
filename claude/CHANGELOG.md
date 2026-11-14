# Release notes

## 0.2.2 — candidate

- Both skills lead no-compiler clients to `upload_guest_site_files` with a
  complete tool-argument example (`files: [{path, text}]`) and a separately
  labelled same-site captured-asset example (`capture_artifact: {capture_id,
artifact_id}`), before the ZIP archive path. They state that `files` is an
  array in tool arguments and that the path-keyed `files` maps belong only inside
  the ZIP manifests. Two real ChatGPT runs had sent the manifest map shape first.
- Clients without a cryptographically secure generator call
  `prepare_guest_site_creation` (#22952) once before the first create and pass
  its private `operation_id` and `retry_secret` unchanged; they never type or
  invent the secret, and stop with an explanation when neither is available.
- The small-file path documents the page routes from #22950: `index.html` is
  `/`, `about.html` is `/about.html`, `about/index.html` is `/about/`, and an
  authored `404.html` is the not-found page.
- Both skills add an "Edit a claimed site" section for `update_app_content`
  (#22960): send the complete file set from a fresh source read, let the server
  write the route manifest, and retry identical input with the same operation
  ID after `operation_retry_required` or `app_update_pending`. An
  `operation_id_conflict` is not treated as proof of changed input, because a
  server from another release can return it for an identical request: the
  agent keeps the original ID and payload, checks status and stops if it cannot
  settle the earlier update. They say that a
  claimed site never edited this way may still serve extra pages as downloads.
- `create_guest_site` instructions use the new optional private `retry_secret`:
  one random lowercase UUIDv4 per new site, reused with the same operation ID
  only for identical retries, kept out of every reply, page and report. After a
  successful creation the agent keeps that site for uploads, capture and
  recovery; a later failure never creates another site. If a server rejects the
  field, the agent reports the compatibility problem.
- The migrate skill tells the agent to keep reading capture text from the
  returned `next_offset` until it is `null`; a chunk can be shorter than the
  requested limit.
- **Requires the backend with `retry_secret` (#22938), preparation (#22952),
  multipage small-file routes (#22950) and claimed static routes (#22960).** Deploy the server before distributing
  this package. Older packages keep working against
  the new server with same-network recovery only.
- Same endpoint, mixed authentication with DCR, `commerce: false`,
  `countries: []`, listing text, identity, support and legal links, assets and
  all five positive and three negative review cases.

Not yet real client verified. No portal upload, rescan, submission, review,
approval or publication is claimed.

## 0.2.1 — candidate

- Rewrite the OpenAI listing `longDescription` around publishing static sites,
  authorized migration, source ownership and editing a claimed App. It no
  longer mentions pricing, free hosting or subscriptions, which the OpenAI
  portal metadata scan flagged on 0.2.0. The truthful pricing facts stay in
  `review.commerce_description`.
- The API host now serves the OpenAI Apps domain-verification response at
  `https://api.codepress.dev/.well-known/openai-apps-challenge` (a backend
  change, not part of this package).
- Same endpoint, mixed authentication with DCR, `commerce: false`, countries,
  identity, support and legal links, skills, review cases and file inventory.

Not yet real client verified. No portal rescan, submission, review, approval,
publication or publisher verification is claimed.

## 0.2.0 — candidate

- Add `review.commerce_description`: the plugin publishes and claims free
  sites, has no purchase, checkout or subscription tools and does not sell
  hosting. `commerce` stays false.
- Add `publication.release_notes` and `publication.countries: []`: the owner
  approved all OpenAI-supported countries with no added restrictions. Demo
  recording, portal publisher verification and reviewer access stay absent.
- Rewrite the review prompts naturally; each negative case now states its
  setup, expected response and prohibited tool use.
- The post-claim case uses the advertised App source tools
  (`list_app_source_files`, `read_app_source_file`, `update_app_content`,
  `get_app_content_update_status`) instead of implying `update_app` edits source.
- Remove paid hosting prices and upgrade prompts from the skills, README,
  walkthrough and the public Sites claim guidance. Claimed sites stay free on
  their CodePress address; custom-domain pricing and entitlements are unchanged.
- Support link is now <https://codepress.dev/support>.
- Same endpoint, mixed authentication, identity, skills and file inventory.

Not yet real client verified. No portal validation, submission, review,
approval, publication or recorded demonstration is claimed.

## 0.1.0 — candidate

- Package the existing publish-site and migrate-site workflows byte for byte.
- Declare one remote mixed-auth connection for guest publishing and protected
  account App work after OAuth; ordinary account MCP remains separate.
- Generate OpenAI Agent Plugins and claude.ai remote-plugin layouts from one
  authored configuration, with deterministic ZIPs and a minimal public export.
- Provide source/file digests, allowlist validation and a local secret scan.
- Include consumer guidance, review cases and an unrecorded walkthrough script.
- Claimed sites stay free on their CodePress address. Unclaimed guest sites
  still expire.

Not yet real client verified. No portal validation, submission, review,
approval, publication, public repository or recorded demonstration is claimed.

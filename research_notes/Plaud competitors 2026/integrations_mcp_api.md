# Integration capabilities of AI voice recorders competing with Plaud (MCP, APIs, webhooks, automation, exports) — as of Nov 2026

> Method note: In this research session, direct page fetches to docs.plaud.ai, docs.omi.me and fieldy.ai failed: those hosts are not on the session's network allowlist. Findings therefore come from search-engine excerpts of those primary pages plus secondary sources. Each claim is labeled as primary docs, vendor blog/marketing, or third-party review. Anything that matters for a decision should be re-checked against the primary page.

## Q1. Official MCP servers: URL, remote vs local, tools, auth, plan tier, Claude Connector Directory status

### Takeaway
Plaud has the most mature setup for Claude. It has a verified listing in Claude's Connector Directory, a remote server at `https://mcp.plaud.ai/mcp` plus a local npx package, and read-only tools. Fieldy, Omi, Pocket, Bee (Amazon) and Limitless also have official MCP servers. Of these, Fieldy claims a one-click Claude connector, while Pocket and Omi are added as custom connectors. Pocket is the only one confirmed (via a third-party review) to have write tools, for updating action items.

### Cited Findings

**Plaud (official)**
- Remote MCP URL is `https://mcp.plaud.ai/mcp`. In claude.ai the path is Settings → Connectors; another docs page describes Customize → Connectors → search "Plaud Web MCP" — [Plaud docs: MCP](https://docs.plaud.ai/plaud-mcp-cli/mcp); [Plaud docs: app MCP](https://docs.plaud.ai/documentation/plaud_app/mcp?ref=menu)
- For Claude Desktop and Claude Code, Plaud's docs use a local package, `@plaud-ai/mcp@latest`, run via `npx -y` — [Plaud docs](https://docs.plaud.ai/plaud-mcp-cli/mcp)
- Plaud's docs say the HTTP route is hosted in the US and data is "processed in transit only" and not stored after the request — [Plaud docs](https://docs.plaud.ai/plaud-mcp-cli/mcp)
- Tools named in the official docs: `list_files` (lists recordings, optional filters), `get_file`, `get_note`, `get_transcript` (full transcript with timestamps and speaker labels) — [Plaud docs](https://docs.plaud.ai/plaud-mcp-cli/mcp)
- The Claude directory listing is "verified" and requires sign-in. It shows five read-only tools (list files, get file, get note, get transcript, get current user), no write actions, with connector URL `https://mcp.plaud.ai/mcp` — [Claude marketplace: Plaud connector](https://claude.com/marketplace/connectors/plaud); [Claude directory](https://claude.ai/directory/33b42d5b-de4e-43c6-ae45-135b15ec1791)
- A third-party page lists seven tools, adding login, logout and get_current_user, and dates the launch to **September 22, 2026** — via search excerpt; third-party, not verified against Plaud release notes — [innfactory / mcpbundles / agentman pages](https://www.mcpbundles.com/skills/plaud)
- Plan tier: Plaud's pricing pages list "Plaud MCP Server (Beta)" among features included in **all plans**. A third-party page says the docs only require an active Plaud account — [Plaud pricing](https://www.plaud.ai/pages/plaud-ai-plan-pricing); [SEA pricing](https://sea.plaud.ai/pages/plaud-ai-plan-pricing)
- Auth: sign-in (OAuth-style browser login) per the directory listing, which says "sign-in required" — [Claude marketplace](https://claude.com/marketplace/connectors/plaud)
- Plaud also has a support article for MCP — [Plaud Support: Plaud MCP](https://support.plaud.ai/hc/en-us/articles/57751078986265-Plaud-MCP)
- A Plaud MCP is also exposed through Zapier's MCP catalog — [Zapier MCP: Plaud](https://zapier.com/mcp/plaud)

**Fieldy (official)**
- MCP endpoint is `https://api.fieldy.ai/mcp` for Claude, ChatGPT and Cursor, with browser sign-in authorization — [Fieldy Help: Connecting Fieldy to Claude/ChatGPT](https://intercom.help/fieldy/en/articles/15019124-connecting-fieldy-to-claude-chatgpt-and-your-own-apps); [Fieldy blog: developer platform](https://www.fieldy.ai/blog/introducing-fieldy-developer-platform-public-api-mcp) (vendor blog)
- Fieldy markets a "1-click" Claude connector added through a pre-filled link. Whether it is in the official Claude directory is unconfirmed — [Fieldy blog: Claude connector](https://www.fieldy.ai/blog/fieldy-claude-chatgpt-connector) (vendor blog)

**Omi (official)**
- Hosted MCP at `https://api.omi.me/v1/mcp` (Streamable HTTP), with Bearer auth using an `omi_mcp_` key created at app.omi.me/developers. Developer keys (`omi_dev_`) do **not** work for MCP — [Omi docs: MCP setup](https://docs.omi.me/doc/developer/mcp/setup)
- `/v1/mcp/sse` is described as a permanent compatibility alias, but one version of the docs still lists it as the primary URL (internal docs inconsistency). Local stdio options (uvx, Python, Docker) using `OMI_API_KEY` are marked deprecated — [Omi docs: MCP setup](https://docs.omi.me/doc/developer/mcp/setup); [setup.md](https://docs.omi.me/doc/developer/mcp/setup.md)
- The introduction page lists 8 tools covering search and retrieval over memories and conversations. A review says the open-source server can also create, edit and delete memories and conversations — [Omi docs: MCP intro](https://docs.omi.me/doc/developer/mcp/introduction.md); [webofmike review](https://webofmike.com/pocket-vs-omi/) (third-party)
- Omi's marketing page covers Claude and Cursor integration — [Omi blog](https://www.omi.me/blogs/integrations/mcp-claude-cursor) (vendor blog)

**Pocket (official)**
- Remote MCP at `https://public.heypocketai.com/mcp`, added in Claude as a custom connector (not found in the directory) — [hackceleration / search summary](https://hackceleration.com/resources/integrations/claude/plaud); [webofmike review](https://webofmike.com/pocket-ai-recorder/) (third-party)
- Auth is OAuth, or an API key sent as `Bearer pk_...` for clients that only accept static headers. Claude Code connects with one command — [webofmike Pocket review](https://webofmike.com/pocket-ai-recorder/) (third-party)
- Seven tools: account info, folder lists, hybrid search across recordings, action-item search and action-item **updates** on any plan. Full transcripts with audio links and cross-meeting questions require **Pro**. On the free plan, MCP is "mostly search" — [webofmike Pocket review](https://webofmike.com/pocket-ai-recorder/) (third-party; not verified against Pocket docs)

**Bee (Amazon) (official)**
- The official Bee CLI doubles as an MCP server. It exports conversations, facts and tasks to local Markdown for Claude and Codex. Amazon hackathon resources list Bee developer docs for the CLI, MCP server, Bee Skill and API — [Amazon Developer Hackathon resources](https://amazonappdev2026.devpost.com/resources); [Devpost](https://amazonappdev2026.devpost.com/)
- Bee joined Amazon in 2025 — [AI Engineer: Bee, Amazon](https://ai.engineer/orgs/bee-amazon)

**Limitless (official; acquired by Meta)**
- Meta acquired Limitless on Dec 5, 2025 and new hardware sales stopped that day. Existing owners got free Unlimited service through end of 2026 — [mrktcorrect](https://mrktcorrect.com/blog/limitless-pendant) (third-party)
- Official hosted MCP at `https://api.limitless.ai/mcp`. The Developer API is in beta and covers Pendant data only — [Limitless Developer Platform](https://www.limitless.ai/developers)

**Mobvoi TicNote**
- "TicNote Connect" connects AI assistants to TicNote knowledge. Digital Trends reports a TicNote API accessible from ChatGPT, Codex and Claude. MCP is not explicitly confirmed — [TicNote site](https://ticnote.com/en); [Digital Trends](https://www.digitaltrends.com/wearables/mobvois-ticnote-watch-wants-to-take-notes-for-you/)

### Inferences
- For a Claude user, Plaud is the lowest-friction option: a verified directory connector, available on all plans, read-only, which limits how much damage a misbehaving agent could do. Fieldy is likely close behind. Pocket and Omi need a custom-connector URL, and Omi also needs an API key.
- Pocket's write tools and Omi's create/edit/delete capability carry more agent risk, but they also allow two-way workflows.
- Plaud's "processed in transit only" statement covers the MCP route, not the Plaud cloud itself.

### Gaps
- The Sept 2026 Plaud MCP launch date is supported only by third-party pages. No Plaud release note was retrievable.
- The exact tool count is 4 in the docs excerpt, 5 in the directory listing and 7 on a third-party page. The directory listing (5) is the most authoritative of the three.
- No primary docs were retrieved for Pocket's tool list or plan gating.
- Omi's full tool names were not retrieved. Directory status for Fieldy and Omi is unconfirmed.
- I found no MCP evidence for HiDock, Soundcore Work, UMEVO, Viaim or iFlytek.

## Q2. Public REST APIs and webhooks (official vs unofficial)

### Takeaway
Plaud has **no public general-purpose API** for end users. Its developer offering, Plaud Embedded (device SDK plus a Transcription API), is for companies building products. Fieldy, Omi and Limitless (beta) have official public APIs. Omi is the only brand found with documented developer webhooks, and those have known reliability and security issues.

### Cited Findings
- Plaud Help Center: "there is no public, general-purpose Plaud API available to users today," with no sign-up or waitlist. Users are pointed to Plaud MCP — [Plaud Support: API access](https://support.plaud.ai/hc/en-us/articles/60726890231449-How-can-I-get-API-access-to-my-Plaud-data)
- **Plaud Embedded** is Plaud's developer platform for companies, offering a device SDK and a Transcription API. Docs are at docs.plaud.ai and access is requested at dev.plaud.ai — [Plaud Support](https://support.plaud.ai/hc/en-us/articles/60726890231449-How-can-I-get-API-access-to-my-Plaud-data)
- Fieldy's Public API uses API keys from Fieldy Developer Settings, limited to 30 requests/minute — [Fieldy Help](https://intercom.help/fieldy/en/articles/15019124-connecting-fieldy-to-claude-chatgpt-and-your-own-apps); [Fieldy blog](https://www.fieldy.ai/blog/introducing-fieldy-developer-platform-public-api-mcp) (vendor blog)
- Omi has a developer REST API with `omi_dev_` keys, separate from MCP keys — [Omi docs](https://docs.omi.me/doc/developer/mcp/setup)
- Omi has a "Conversation created" developer webhook, configured in Developer Settings. Known issues:
  - Some pendant conversations never fire the webhook — [GitHub #24749](https://github.com/BasedHardware/omi/issues/24749); [fix PR #24750](https://github.com/BasedHardware/omi/pull/24750)
  - Merged conversations fire the webhook and are later deleted — [#22413](https://github.com/BasedHardware/omi/issues/22413); [PR #22415](https://github.com/BasedHardware/omi/pull/22415)
  - Payloads are **unsigned**, so receivers cannot verify the sender — [#20939](https://github.com/BasedHardware/omi/issues/20939)
- Limitless Developer API is in beta and covers Pendant data only — [Limitless Developers](https://www.limitless.ai/developers)
- Bee has developer API keys from the Bee developer website. The community BeeMCP reads them from `BEE_API_TOKEN` — [OkGoDoIt/beemcp](https://github.com/OkGoDoIt/beemcp)

### Inferences
- If a user wants a scripted pipeline (e.g., an n8n job that pulls Plaud transcripts), Plaud supports only Zapier's trigger and MCP. Its consumer data cannot be pulled through a REST API. Fieldy and Omi support custom pipelines directly.
- Anyone who builds on Omi's webhooks should verify payloads some other way (e.g., re-fetch via the API) because they are unsigned.

### Gaps
- No public API or webhook documentation was found for Pocket, HiDock, TicNote (beyond press mentions), Soundcore, UMEVO, Viaim or iFlytek.
- Plaud Embedded pricing and eligibility were not found.
- No Fieldy webhook evidence was found.

## Q3. Zapier / Make / n8n, native exports, and HubSpot / Google Workspace

### Takeaway
Plaud is the only brand found with a native Zapier app. It is trigger-only ("Transcript & Summary Ready"), and through it Plaud data can reach Google Drive, HubSpot and Salesforce. No brand has a native HubSpot app. HiDock and TicNote have native Notion export, HiDock also exports to Google Docs, and UMEVO export is manual.

### Cited Findings

**Plaud**
- The Zapier app is **trigger-only**. The trigger is "Transcript & Summary Ready" (`new_ai_generation_complete`); Plaud cannot be acted on from other apps. Team workspaces can be selected at authorization — [Plaud Support: Zapier](https://support.plaud.ai/hc/en-us/articles/12200669941647-Zapier-integration); [Zapier: Plaud integrations](https://zapier.com/apps/plaud/integrations)
- Zapier templates exist for Plaud to Google Drive ("exports the file to Google Drive when a transcript and summary are ready") and to Salesforce — [Zapier Plaud→Drive](https://zapier.com/apps/plaud/integrations/google-drive); [Zapier Plaud→Salesforce](https://zapier.com/apps/plaud/integrations/salesforce); [Zapier blog: 4 ways to automate Plaud](https://zapier.com/blog/automate-plaud/)
- **HubSpot:** there is no native Plaud app in the HubSpot Marketplace. The community workaround is a Zapier zap that creates a HubSpot engagement from the Plaud trigger; Make or the HubSpot API can also do this — [HubSpot Community: Plaud Notetaker](https://community.hubspot.com/t/plaud-notetaker/149994)
- Zapier's free plan polls triggers every 15 minutes — [search summary of Zapier pages](https://zapier.com/apps/plaud/integrations)
- Plaud describes a direct app-to-Notion export — [Plaud blog: export to Notion](https://www.plaud.ai/blogs/articles/how-to-export-voice-recordings-to-notion-automatically) (vendor blog)

**HiDock (HiNotes)**
- HiNotes **Pro and Unlimited** support direct export to Notion, Google Docs and Microsoft OneNote. The bundled "Member" plan does not include integrations — [HiDock guide: Notion export](https://www.hidock.com/blogs/user-guide/how-to-export-hinotes-meeting-summaries-to-notion-2026-guide) (vendor blog); [HiNotes](https://www.hidock.com/pages/hinotes)
- Per the search summary of HiDock pages, file export covers TXT, PDF, Word, CSV, SRT and Markdown — [HiDock](https://www.hidock.com/pages/hinotes) (vendor)
- No HiDock Zapier app or public API was found.

**Mobvoi TicNote**
- The TicNote Cloud web app exports to Notion and Obsidian — [TicNote Cloud](https://ticnote.com/en/membership); [PR Newswire: TicNote Watch](https://www.prnewswire.com/news-releases/mobvoi-announces-ticnote-watch-the-ai-note-taker-that-captures-your-day-from-your-wrist-302894236.html)
- Export formats: audio (Ogg), transcript (TXT), summary (Markdown), mind map (PNG) — [Amazon listing](https://www.amazon.com/Mobvoi-Transcription-Languages-Dual-Mode-Recording/dp/B0G2YD641T) (retailer/marketing)

**UMEVO**
- Moving UMEVO Note Plus content to Notion is manual: copy the text, or export audio from the app or over USB — [UMEVO blog](https://www.umevo.ai/blogs/ume-all-posts/building-a-second-brain-syncing-ai-voice-notes-to-notion) (vendor blog)

**Others**
- No native Zapier app was found for Fieldy, Omi, Pocket, Bee, HiDock or TicNote. An agent-workflow product offers Plaud→Google Drive backup with Sheets tracking — [AgentPMT](https://www.agentpmt.com/agent-workflow-skills/plaud-recordings-to-google-drive-sync) (third-party)

### Inferences
- For a user on HubSpot and Google Workspace, the realistic paths are:
  - **Plaud:** Zapier (Plaud trigger → Drive/Docs file plus HubSpot engagement), with the Claude connector for ad-hoc querying.
  - **Fieldy or Omi:** custom n8n/Make HTTP flows against their APIs.
  - Claude itself can bridge the gap if the HubSpot and Google Drive connectors are also enabled: read the transcript via the recorder MCP, then write to HubSpot or Drive.
- None of the brands offer a native n8n node or Make app that I could find.

### Gaps
- I could not verify any Make or n8n native apps for any brand.
- Soundcore Work, Viaim (RecDot) and iFlytek export or integration details were not found in this pass.
- Zapier plan requirements for Plaud (free vs paid tiers, multi-step zaps for HubSpot) were not confirmed.

## Q4. Third-party / community MCP servers and their risk

### Takeaway
Community MCP servers exist for Plaud, Omi and Bee. They mostly use unofficial or reverse-engineered web APIs, browser/CDP sessions or personal tokens. Now that official servers exist for all three, these add credential and breakage risk without much benefit.

### Cited Findings
- **Plaud:**
  - `mcp-server-plaud` (PyPI) connects Claude to Plaud via the **unofficial Plaud web API** — [PyPI](https://pypi.org/project/mcp-server-plaud/)
  - `plaud-mcp` (davidlinjiahao) drives the running Plaud Desktop app over Chrome DevTools Protocol — [Glama](https://glama.ai/mcp/servers/davidlinjiahao/plaud-mcp/schema); [LobeHub](https://lobehub.com/ja/mcp/davidlinjiahao-plaud-mcp)
  - Another community server exists — [GitHub charathram/plaud-mcp](https://github.com/charathram/plaud-mcp)
  - There is also a `plaud-tools` package — [PyPI plaud-tools](https://pypi.org/project/plaud-tools/)
- **Omi:** the `omi-mcp` PyPI package ("extended MCP tools for Omi REST API") has changed auth handling across versions — [PyPI omi-mcp](https://pypi.org/project/omi-mcp/0.1.8/); a separate community server is [fourcolors/omi-mcp](https://glama.ai/mcp/servers/fourcolors/omi-mcp/tools/read_omi_memories); a Docker image also exists — [Docker Hub mcp/omi](https://hub.docker.com/r/mcp/omi)
- **Bee:**
  - BeeMCP (unofficial) uses a `BEE_API_TOKEN` — [OkGoDoIt/beemcp](https://github.com/OkGoDoIt/beemcp)
  - Hackathon builds: [bee-memory-mcp](https://github.com/MSAbhishek22/bee-memory-mcp) and [between-sessions](https://github.com/wilmccann/between-sessions)

### Inferences
- Risks:
  - Unofficial-API servers can break whenever the vendor changes its web app, and they may violate the ToS.
  - CDP-based servers inherit a full logged-in desktop session.
  - Token-based servers hold long-lived credentials, often in plaintext config.
  - Third-party aggregator listings (vinkius, conare, mcpmarket) relay data through extra parties.
- Recommendation: use the official servers (mcp.plaud.ai, api.omi.me/v1/mcp, Bee CLI).

### Gaps
- No security audits of any community server were found. Maintenance status and star counts were not checked.

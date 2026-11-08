# Privacy, Security, Data Handling and Company Stability: Plaud and Competing AI Voice Recorders (as of Nov 2026)

Research notes for a church pastor who records confidential pastoral conversations and board meetings. Collected 2026-11-08 via web search. Note on method: direct fetches of plaud.ai and of an independent security researcher's site were blocked by this session's network settings, so some details come from search-result excerpts of those pages rather than full-page reads. Claims are labeled **[vendor claim]** or **[third-party]** where it matters.

## Certifications (SOC 2 Type II, HIPAA/BAA, GDPR, ISO 27001, EN 18031)

### Takeaway
Plaud has the strongest documented certification stack in the category: SOC 2 Type II (announced Sept 2026), ISO 27001/27701 (auditor named: Sensiba), and a BAA on request. Most rivals (Pocket, Fieldy, Omi, UMEVO) claim SOC 2/HIPAA only in their own marketing. Viaim claims ISO 27001/27701. TicNote, HiDock, and Soundcore Work have no independently confirmed certifications in what I found.

### Cited Findings
- **Plaud:** announced SOC 2 Type II on Sept 22, 2026. Scope is security, availability, and confidentiality, and the certificate is available via its Trust Center **[vendor-published; audit is third-party]**. Sources: [Plaud blog](https://www.plaud.ai/blogs/news/plaudai-is-now-soc-2-type-ii-certified-heres-what-that-actually-means), [Plaud support: security & compliance](https://support.plaud.ai/hc/en-us/articles/57744166222489-Plaud-s-security-and-compliance)
- **Plaud:** certified to ISO/IEC 27001 and ISO/IEC 27701 by Sensiba **[vendor statement naming auditor]**. Source: [Plaud healthcare page](https://www.plaud.ai/pages/healthcare-solution)
- **Plaud:** claims HIPAA, GDPR, and EN 18031 compliance and will sign a BAA on request. Source: [Plaud Trust Center](https://www.plaud.ai/pages/trust)
- **Plaud HIPAA, third-party view:** reviewers say Plaud is not automatically HIPAA compliant for everyday consumer use, and that a signed BAA plus correct configuration is required. One reviewer says the HIPAA attestation was verified through Drata. Sources: [Mentalyc](https://www.mentalyc.com/blog/is-plaud-hipaa-compliant), [Layer3Labs](https://www.layer3labs.io/guides/is-plaud-hipaa-compliant), [RecordingLaw](https://www.recordinglaw.com/is-plaud-hipaa-compliant/)
- **Conflicting claim:** an anonymous "Plaud complaints" site says Plaud lacks GDPR/SOC 2 and that they are "on the roadmap." This is likely outdated or competitor-linked, it is unverified, and it contradicts the Sept 2026 SOC 2 announcement. Source: [plaudcomplaints site](https://plaudcomplaints-8pufap4n.manus.space/)
- **Plaud, Jan 2026:** at the NotePin S launch the company cited ISO 27001, SOC 2, HIPAA, and GDPR. Source: [SiliconANGLE](https://siliconangle.com/?p=726719)
- **Pocket (Open Vision Engineering):** a June 2026 funding release says it is HIPAA and SOC 2 compliant **[vendor claim in press release]**. Source: [VCA Online](https://www.vcaonline.com/news/2026062904/pocket-raises-11m-from-accel-and-others-as-demand-surges-for-its-personal-ai-assistant-device/)
- **Fieldy (Field Labs):** claims HIPAA compliance, says its practices were "validated through independent audits," and points to a Trust Dashboard **[vendor claim]**. Source: [Fieldy blog](https://www.fieldy.ai/blog/fieldy-is-hipaa-compliant-ai-note-taking-you-can-trust-with-confidential-data)
- **Omi:** marketing cites "SOC 2 + HIPAA" **[vendor claim]**. This sits alongside an independent researcher's April 2026 vulnerability disclosure (see Incidents). Source: [Layer3Labs Omi review](https://www.layer3labs.io/guides/omi-ai-review)
- **HiDock:** a Nudge Security aggregator profile lists HiDock as SOC 2 compliant. Unverified, with no audit report found. HiNotes publishes a GDPR-style Data Processing Addendum. Sources: [Nudge Security](https://security-profiles.nudgesecurity.com/app/hidock-com), [HiNotes DPA](https://hinotes.hidock.com/data-processing-addendum)
- **UMEVO:** its blog says it is "fully compliant with SOC 2, HIPAA, and GDPR" **[self-reported; no audit found]**. Source: [UMEVO security page](https://www.umevo.ai/pages/security-compliance)
- **Viaim (RecDot):** marketing says ISO 27001 and ISO 27701. A reviewer notes these do not satisfy FERPA or NDAA requirements. Source: [Vibe.us review](https://vibe.us/blog/viaim-recdot-review-vs-vibe-dot/)
- **iFlytek Smart Recorder:** passed China's CCRC information security certification, which is a Chinese certification, not SOC 2 or ISO. Source: [iFlytek product page](https://www.iflytek.com/en/products/recorder/smart-recorder.html)
- **Mobvoi TicNote:** no SOC 2 or ISO certification found.
- **Soundcore Work (Anker):** no certification found.

### Inferences
- For a church use case, HIPAA is not legally required (pastoral counseling is generally not a HIPAA-covered entity). SOC 2 Type II and ISO 27001 are still the most meaningful signals that third-party auditors have checked controls. Only Plaud has a publicly announced SOC 2 *Type II* with a named ISO auditor among the brands researched.
- "HIPAA compliant" on a consumer gadget page means little without a signed BAA. There is no official HIPAA certification body.

### Gaps
- Could not read actual SOC 2 reports, which are typically under NDA. Could not verify the Pocket, Fieldy, Omi, or UMEVO claims against auditor names.
- EN 18031 status was confirmed only for Plaud, as a vendor claim. No data found for the others.

## Encryption, on-device/offline transcription, local-only mode

### Takeaway
Nearly every brand encrypts in transit (TLS) and at rest (AES-256). None of the mainstream cloud-AI products offers true end-to-end encryption in which the vendor cannot read your audio, because cloud AI has to decrypt audio to transcribe it. Genuine offline transcription is offered mainly by iFlytek (Chinese) and claimed by UMEVO. Soundcore Work defaults to local storage and deletes the cloud copy after transcription. Omi is open source and can be self-hosted, but only by technical users.

### Cited Findings
- **Plaud:** TLS 1.2+ in transit and AES-256 at rest. Transcription is cloud-based. Sources: [Plaud healthcare page](https://www.plaud.ai/pages/healthcare-solution), [Plaud Trust Center](https://www.plaud.ai/pages/trust)
- **HiDock:** recordings live on the device, but transcription uploads the file to the HiNotes service on Microsoft Azure. HiDock describes the link as SSL and "end-to-end encrypted." Source: [HiDock Data Security](https://www.hidock.com/blogs/user-guide/hidock-data-security)
- **Soundcore Work:** stores audio and transcripts locally by default with AES-256, blocks USB audio export, and uses TLS 1.3 for upload. Data goes to the cloud only if you choose to transcribe. Audio is deleted from the cloud after transcription, but unretrieved files are kept up to 7 days. Anker says it will not back up or train on data without permission **[vendor claims]**. Sources: [Soundcore privacy blog](https://www.soundcore.com/blogs/voice-recorder/privacy-ai-voice-recorder-secure-notes), [Anker UK product page](https://www.soundcore.com/uk/products/d3200-soundcore-work-ai-voice-recorder), [Anker Nordics](https://www.ankernordics.com/products/d3200)
- **Mobvoi TicNote:** claims "end-to-end encrypted cloud storage" on U.S.-based cloud infrastructure and encryption on internal storage **[vendor/retailer claim]**. Sources: [PB Tech listing](https://www.pbtech.co.nz/product/AUDMOI0001/MOBVOI-TicNote-AI-Voice-Recorder--Note-Taker-with), [Notebookcheck](https://www.notebookcheck.net/Mobvoi-TicNote-debuts-as--agent-powered-voice-recorder.1063088.0.html)
- **Viaim:** claims AES-256 "end-to-end" encryption plus TLS **[vendor claim]**. Source: [Viaim store](https://store.viaim.ai/collections/all/products/viaim-recdot)
- **Pocket:** claims end-to-end encryption **[vendor claim]**. An affiliate comparison says Pocket retains audio, while Fieldy does not. Sources: [VCA Online](https://www.vcaonline.com/news/2026062904/pocket-raises-11m-from-accel-and-others-as-demand-surges-for-its-personal-ai-assistant-device/), [mrktcorrect Pocket vs Fieldy (affiliate)](https://mrktcorrect.com/blog/pocket-vs-fieldy)
- **Omi:** firmware and app are MIT-licensed open source and can be self-hosted, but by default audio is processed on Omi's cloud. Sources: [UMEVO blog on Omi (competitor)](https://www.umevo.ai/blogs/ume-all-posts/open-source-ai-voice-recorders-omi-whisper-and-the-diy-alternative), [Layer3Labs](https://www.layer3labs.io/guides/omi-ai-review)
- **iFlytek Smart Recorder:** transcribes offline on the device, which it markets as an information-security benefit. Sources: [iFlytek press release](https://www.newsfilecorp.com/release/208374), [iFlytek FAQ](https://www.iflytek.com/en/support/faq/smart-recorder.html)
- **UMEVO Note Plus:** marketed as "Edge AI" with a "Black Box" encryption chip. Its transcription is partly cloud minute-metered (400 free minutes/month), so the on-device claim is ambiguous **[vendor]**. Source: [UMEVO Note Plus specs](https://www.umevo.ai/blogs/ume-all-posts/umevo-note-plus-full-features-and-specs-everything-you-need-to-know)
- **Amazon Bee:** Amazon says audio is deleted after processing and that operators cannot read conversation content **[vendor claim relayed by one outlet]**. Source: [Xenospectrum](https://xenospectrum.com/en/amazon-bee-frontier-eclipse-private-compute/)

### Inferences
- "End-to-end encrypted" in this category almost always means encrypted in transit and at rest. The vendor's servers, and their AI subprocessors, still see plaintext audio during transcription.
- For the most sensitive conversations, the safest pattern is a device that records locally plus offline or local transcription (e.g., iFlytek, or a plain recorder transcribed on the user's own computer with local Whisper). The next best is a cloud product with SOC 2 Type II and zero-retention AI contracts (Plaud).

### Gaps
- Could not verify whether Plaud offers any local-only or offline transcription mode. None was found.
- UMEVO's real on-device versus cloud split is unclear.

## Data location, HQ/ownership, and AI providers

### Takeaway
Most brands in this category have Chinese or Hong Kong engineering or manufacturing roots, Plaud included. Plaud presents as a San Francisco/Delaware company but is reported to be backed by Shenzhen Jizhi Connect Technology. It states that user data sits in AWS US West (Oregon). Audio is processed by U.S. frontier AI providers (OpenAI, Google, Microsoft, and Anthropic as a selectable model). U.S.-owned alternatives are Bee (Amazon), Pocket (Delaware), Fieldy (Field Labs), and Omi (Based Hardware, San Francisco).

### Cited Findings
- **Plaud:** says it was established in the U.S. in Nov 2023 with HQ in San Francisco, and its UAE site gives a Delaware address. Taiwanese and HK press reported that it is backed by, and its hardware made by, Shenzhen Jizhi Connect Technology. Plaud issued a formal privacy statement in Sept 2025 after the controversy. Sources: [Digitimes](https://www.digitimes.com/news/a20250903PD210.html), [INSIDE (Taiwan)](https://www.inside.com.tw/article/37753-ai-hardware-taiwan-consumers-scrutiny), [unwire.hk](https://unwire.hk/2025/09/04/plaud-privacy-security-response/tech-secure/), [TechBang](https://www.techbang.com/posts/125240-plaud-hardware-manufacturing-statement)
- **Plaud data location:** the EU page says user information and voice data are stored only on U.S. servers, and the UAE page says AWS US West (Oregon). Plaud told INSIDE that earlier data had been on Google, Azure, and AWS. Sources: [Plaud EU privacy-security](https://eu.plaud.ai/pages/privacy-security), [Plaud UAE privacy-security](https://uae.plaud.ai/pages/privacy-security), [INSIDE](https://www.inside.com.tw/article/37753-ai-hardware-taiwan-consumers-scrutiny)
- An AWS case study says AWS helped Plaud with compliance "across Europe, North America, and China." Source: [Amazon press](https://press.aboutamazon.com/aws/2025/12/plaud-uses-aws-to-scale-ai-powered-meeting-solutions-globally)
- A privacy analysis argues that China's 2021 Data Security Law poses structural risk while the corporate structure remains unchanged. It is a competitor-adjacent blog, opinion only. Source: [Sally.io](https://www.sally.io/blog/plaud-gdpr-data-protection)
- **Plaud AI providers:** the help center names OpenAI, Google, and Microsoft as AI subprocessors under enterprise zero-retention, no-training agreements. A separate model FAQ also lists Claude Sonnet (Anthropic) as selectable. The two pages are inconsistent about Anthropic. Sources: [Plaud: How your data is used in AI processing](https://support.plaud.ai/hc/en-us/articles/57744162858009-How-your-data-is-used-in-AI-processing), [Plaud: AI models](https://support.plaud.ai/hc/en-us/articles/55644525081881-AI-models), [Notebookcheck on Claude](https://www.notebookcheck.net/plaud-adds-anthropic-claude-3-5-sonnet-ai-to-plaud-note-ai-voice-recorder-through-pro-plan-subscription.863882.0.html)
- **HiDock:** HiNotes runs on Microsoft Azure and uses Claude (since Oct 25, 2024) and OpenAI. Source: [HiDock Data Security](https://www.hidock.com/blogs/user-guide/hidock-data-security)
- **Soundcore Work:** transcription is powered by OpenAI GPT-4.1 per Cult of Mac. Anker is a Chinese company (Changsha/Shenzhen) and is cited here only via the Eufy history below. Source: [Cult of Mac](https://www.cultofmac.com/reviews/soundcore-work-ai-voice-recorder-review)
- **TicNote:** Mobvoi is a Chinese company listed in Hong Kong (HKG: 2438). It says TicNote data is stored on U.S.-based cloud and uses GPT-5 features. Sources: [Simply Wall St](https://simplywall.st/ja/stocks/hk/software/hkg-2438/mobvoi-shares/past), [PB Tech](https://www.pbtech.co.nz/product/AUDMOI0001/MOBVOI-TicNote-AI-Voice-Recorder--Note-Taker-with)
- **Viaim:** a directory lists its operating company as Hong Kong-based. Data location was not found. Source: [VoiceAISpace](https://www.voiceaispace.com/tool/viaim)
- **iFlytek:** a Chinese state-linked AI company; the device is offline-capable. Source: [iFlytek](https://www.iflytek.com/en/products/recorder/smart-recorder.html)
- **Pocket:** Open Vision Engineering, Inc., a Delaware corporation. Source: [Pocket privacy policy](https://heypocket.com/pages/privacy)

### Inferences
- If Chinese-jurisdiction exposure is a deciding concern, Plaud's U.S. data residency is a vendor claim not independently verified. Its corporate link to Shenzhen is documented in press. U.S.-only options are fewer and generally less mature or less audited.
- iFlytek is a U.S. Commerce Department Entity List company (from my background knowledge, not verified in this session), but offline-only use limits data flow.

### Gaps
- No independent verification of any vendor's actual data-storage location.
- Fieldy and Omi data regions and AI providers were not found.

## AI training on user data, opt-out, deletion

### Takeaway
Plaud, TicNote, Pocket, Soundcore, and Bee all claim no training on user data by default. Plaud's Trust Center phrases this as "no training without opt-in." Soundcore and Fieldy offer auto-delete. All of this is vendor-stated.

### Cited Findings
- **Plaud:** "No AI training on your data without opt-in," and AI subprocessors are under zero-retention contracts. Sources: [Plaud Trust Center](https://www.plaud.ai/pages/trust), [Plaud AI processing article](https://support.plaud.ai/hc/en-us/articles/57744162858009-How-your-data-is-used-in-AI-processing)
- **TicNote:** "never used to train AI models." Source: [PB Tech](https://www.pbtech.co.nz/product/AUDMOI0001/MOBVOI-TicNote-AI-Voice-Recorder--Note-Taker-with)
- **Pocket:** does not train on customer data. Source: [VCA Online](https://www.vcaonline.com/news/2026062904/pocket-raises-11m-from-accel-and-others-as-demand-surges-for-its-personal-ai-assistant-device/)
- **Fieldy:** minimizes retention and supports automatic deletion. Source: [Fieldy blog](https://www.fieldy.ai/blog/fieldy-is-hipaa-compliant-ai-note-taking-you-can-trust-with-confidential-data)
- **Soundcore:** deletes cloud audio after transcription and does not train without permission. Source: [Anker Nordics](https://www.ankernordics.com/products/d3200)
- **Bee:** the original Bee policy said audio was not stored or used for training. At acquisition (July 2025), Amazon would not commit to keeping that policy. In Oct 2026, Amazon reportedly said audio is deleted after processing and that shopping suggestions from conversations are opt-in. Sources: [TechCrunch](https://techcrunch.com/2025/07/22/amazon-acquires-bee-the-ai-wearable-that-records-everything-you-say/), [eWeek](https://www.eweek.com/news/amazon-acquires-bee-wearable-ai-startup/), [Xenospectrum](https://xenospectrum.com/en/amazon-bee-frontier-eclipse-private-compute/)

### Inferences
- Bee is now tied to Amazon.com shopping and Alexa+, which is a poor fit for confidential pastoral content, even with opt-in controls.

### Gaps
- Specific retention periods after account deletion were not found for most brands.

## Security incidents, breaches, controversies

### Takeaway
No confirmed Plaud breach was found. Plaud's main controversy is the 2025 Taiwan/HK "Chinese-ownership" episode. Omi has an unpatched-status independent vulnerability disclosure (April 2026). Anker has a serious precedent: in 2022–23 it falsely claimed end-to-end, local-only encryption for Eufy cameras.

### Cited Findings
- **Plaud:** searches found no breach, lawsuit, or regulatory action. Source: search of news, no hits. Fox News ran a general warning about AI recorders capturing bystanders and calls: [Fox News](https://www.foxnews.com/tech/are-you-being-secretly-recorded-by-ai-and-dont-even-know-it)
- **Omi:** an independent researcher says they privately reported 14 (headline says 17) vulnerabilities in the BasedHardware/omi backend on April 15, 2026, including an auth bypass via a development flag that returned a hardcoded user ID, and reported "fourteen days of silence" from the vendor. This is self-published and I could not fetch the full page or confirm fix status. Source: [kasparovabi security research](https://kasparovabi.github.io/security-research/2026-04-omi-disclosure.html)
- **Anker/Eufy:** cameras uploaded to the cloud with cloud storage disabled, streams were viewable unencrypted in VLC, and a hardcoded key was found. Anker admitted the encryption claims were inaccurate (Jan 2023) and removed "local-only" language. Sources: [MacRumors](https://macrumors.com/2023/01/31/anker-eufy-camera-security), [9to5Mac](https://9to5mac.com/2022/12/21/eufy-camera-security-breach/), [Android Police](https://www.androidpolice.com/eufy-cameras-end-to-end-encryption-woes/)
- **Anker** also paid Eufy owners about $2 per video to train its AI. Source: [TechSpot](https://www.techspot.com/community/topics/anker-paid-eufy-owners-2-per-video-to-train-its-ai-even-for-staged-thefts.294964/)
- **TicNote** records phone calls without notifying the other party, a legal-consent concern. Source: [Everyeye review (IT)](https://tech.everyeye.it/articoli/recensione-mobvoi-ticnote-registratore-ia-ottimo-assistente-personale-65562.html)

### Inferences
- The Eufy history is directly relevant: Soundcore Work's "local by default, deleted after transcription" claims come from the same parent company that previously misrepresented local-only and encryption claims. Treat them with more skepticism.

### Gaps
- Could not confirm whether Omi patched the reported flaws. No incident data was found for Fieldy, Pocket, HiDock, UMEVO, or Viaim.

## Company stability and cautionary precedents

### Takeaway
Plaud is by far the largest and most financially durable: reportedly over $250M ARR and over 2M users, profitable and nearly bootstrapped. Pocket raised $11M (Accel, June 2026). Omi is small, with about $2M seed. The Limitless (Meta) and Humane (HP) cases show acquisitions can cut off service, delete data on short notice, or brick devices.

### Cited Findings
- **Plaud scale:** Bloomberg (June 16, 2026) reported over $250M ARR and a target of $500M in 2026 sales. Other outlets cite $100M ARR and 2M devices shipped. Plaud reports over 2M users, with the U.S., Japan, and Europe about 80% of business. Total disclosed funding is small (CB Insights $4.75M over 3 rounds, about $6M often cited). Valuation figures ($1–2B) are unverified. Sources: [Startup Fortune summarizing Bloomberg](https://startupfortune.com/plaud-reached-250-million-in-recurring-revenue-without-a-single-venture-dollar-and-is-now-targeting-500-million-in-2026-sales/), [IT Brief UK ($100M ARR)](https://itbrief.co.uk/story/plaud-says-arr-jumps-to-usd-100-million-in-two-years), [Androguider (2M shipped)](https://www.androguider.com/2026/06/plaud-surpasses-100m-in-arr-with-2m-ai.html), [CB Insights](https://www.cbinsights.com/company/plaud/financials), [Sacra](https://sacra.com/research/plaud-revenue-growth-valuation/)
- **Plaud age:** U.S. entity est. Nov 2023. The first PLAUD Note launched in 2023. Source: [Digitimes](https://www.digitimes.com/news/a20250903PD210.html)
- **Pocket:** raised $11M from Accel and others in June 2026. Source: [VCA Online](https://www.vcaonline.com/news/2026062904/pocket-raises-11m-from-accel-and-others-as-demand-surges-for-its-personal-ai-assistant-device/)
- **Omi:** a $2M round led by Tim Draper in Jan 2025. Other databases list $0.7M to $3.7M. Sources: [Omi blog](https://www.omi.me/blogs/news/omi-raises-2m), [VCBacked](https://www.vcbacked.co/company/omi-ai)
- **Mobvoi:** publicly listed in Hong Kong. Source: [Simply Wall St](https://simplywall.st/ja/stocks/hk/software/hkg-2438/mobvoi-shares/past)
- **Bee:** acquired by Amazon in July 2025. New Bee Frontier and Eclipse devices were reportedly launched Oct 2026 with Alexa+ integration. Sources: [TechCrunch](https://techcrunch.com/2025/07/22/amazon-acquires-bee-the-ai-wearable-that-records-everything-you-say/), [Xenospectrum](https://xenospectrum.com/en/amazon-bee-frontier-eclipse-private-compute/)
- **Limitless → Meta (Dec 5, 2025):** pendant sales stopped. Service was cut in the EU, UK, Brazil, Israel, South Korea, Turkey (and China per some reports), and users had until Dec 19, 2025 (14 days) to export before deletion. Remaining users had to accept Meta's new ToS and privacy policy, and pendants are supported for "at least a year," so about Dec 2026 is the earliest possible end. Sources: [TechCrunch](https://techcrunch.com/2025/12/05/meta-acquires-ai-device-startup-limitless/), [9to5Mac](https://9to5mac.com/2025/12/05/rewind-limitless-meta-acquisition/), [TechInformed](https://techinformed.com/meta-acquires-limitless-pendant-users-moved-to-free-unlimited-plan/)
- **Humane → HP (Feb 2025, $116M):** AI Pins lost all cloud and cellular function on Feb 28, 2025, with about 10 days' notice. All customer data was permanently deleted from Humane servers. Refunds went only to devices shipped on or after Nov 15, 2024. Sources: [Tom's Hardware](https://www.tomshardware.com/peripherals/hp-buys-humane-ai-start-up-for-us-usd116-million-halts-sales-discontinues-ai-pin-support-offers-refunds), [PetaPixel](https://petapixel.com/2025/02/19/humanes-ai-pin-is-dead-and-all-devices-will-stop-working-in-10-days), [Android Authority](https://www.androidauthority.com/humane-ai-pin-shut-down-3527585/)

### Inferences
- Cloud-dependent recorders carry two risks for a pastor: (1) sudden loss of archives, and (2) confidential data passing to a new owner under new terms (Limitless → Meta, Bee → Amazon). Regular local export of transcripts and audio is essential regardless of brand.
- Plaud's revenue scale and profitability make shutdown risk lowest. Its size also makes it an acquisition target, which is speculative.
- Devices that record to local storage and work without the cloud (HiDock local recordings, Soundcore local default, iFlytek offline) still produce usable audio if the company disappears.

### Gaps
- No reliable 2026 funding or revenue data for Fieldy, HiDock, UMEVO, or Viaim. No current status on whether Limitless pendants have been shut off as of Nov 2026.

## Independent reviewer opinions on trustworthiness

### Takeaway
Independent reviewers treat Plaud as the most compliance-mature option but caution that consumer use is not HIPAA-compliant by default and flag its Shenzhen ties. Reviewers are skeptical of "invisible" recorders like Soundcore Work and of privacy promises that rest only on trust (TicNote).

### Cited Findings
- Plaud is "not automatically HIPAA compliant" for consumer use. Sources: [Mentalyc](https://www.mentalyc.com/blog/is-plaud-hipaa-compliant), [RecordingLaw](https://www.recordinglaw.com/is-plaud-hipaa-compliant/)
- One commentary argues Soundcore Work's coin-sized design bypasses social consent "through invisibility," and flags a "cloud processing contradiction." Source: [Winsome Marketing](https://winsomemarketing.com/ai-in-marketing/ankers-coin-sized-voice-recording-device)
- TicNote's privacy promises "rest on trust in the company." Source: [BriefGlance](https://briefglance.com/articles/mobvois-4g-ai-earbuds-a-productivity-leap-or-a-privacy-trap)
- Nudge Security publishes security profiles for Plaud and HiDock (aggregator). Sources: [Nudge Plaud](https://www.nudgesecurity.com/security-profile/plaud), [Nudge HiDock](https://security-profiles.nudgesecurity.com/app/hidock-com)
- Caution: many "comparison" articles are written by competitors (UMEVO, Vibe.us, Hedy, Sally) or affiliates (mrktcorrect) and have commercial bias.

### Inferences
- Rough confidence ranking for confidential use, based on verified evidence: Plaud (audited, cloud, China-linked ownership) > Fieldy/Pocket (U.S., claimed audits, younger) > HiDock/TicNote/Viaim (claims only, Chinese/HK) > Soundcore (Eufy credibility issue) > Omi (open vulnerability report) > Bee (Amazon commerce ties). iFlytek offline is a separate category: strong data isolation but Chinese state-linked.

### Gaps
- No independent lab security audits (e.g., Mozilla *Privacy Not Included*, Consumer Reports) were found for any of these recorders as of Nov 2026.

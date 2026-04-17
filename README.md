# Louis Kunasek

**Context Engineer · AI Integration · AI Governance · AI Cost Engineering · QA Automation**

San Juan, PR · Remote · Available for travel · US Army Combat Veteran

-----

Every role I’ve held has been different from the last one. Infantry in Iraq. Running 24/7 operations at Florida’s emergency operations center. Covering Hurricane Maria as a photojournalist while the island had no power. Managing a $21M FEMA compliance program. Implementing enterprise software at a major utility. Conducting archival research across eight countries. What connects all of it: I walk into complex, high-stakes environments, learn fast, and deliver.

AI is where that career converges. Since August 2024 I’ve shipped four AI artifacts independently, including a config-driven multi-tenant news platform now running 22 live markets across two languages and three brand families, with production-level AI governance and cost engineering. I direct AI tools to write code, then make the product, editorial, governance, and cost decisions the tools can’t make on their own. The compliance and quality assurance discipline from my background maps directly to AI governance.

-----

### What I’m Working On

🤖 **LangChain Academy** · LangGraph and agent architectures. Primary active work.
🐍 **Python** · FFXI Crafting Profit Calculator. Scraping live auction house data from a 20+ year MMORPG community site. Real problem, real data, no tutorials.
🧪 **Playwright** · Deepening E2E automation against production systems.
📜 **AI Governance** · EU AI Act and NIST AI RMF.

### Shipped Work

#### 🌐 portada-engine · Multi-Tenant Civic News Platform · 22 Live Markets

A config-driven multi-tenant political news aggregation platform I conceived, designed, and shipped. Twenty-two live markets in production, all serving from a single GitHub repository as one unified Vercel project with host-based routing. Three brand families: **La Portada** (Spanish, Latin America and Spain), **The StatePage** (English, United States, with state subdomains under a national apex), and **The EnglandPage** (English, country-level standalone, introducing a wordmark schema pattern reusable for future country sites).

As product owner, creative director, and technical director, I made every product, editorial, design, and architectural decision. I directed the refactor from a single-market codebase into a config-driven engine, and later directed the Phase B/D/E collapse of eleven per-market Vercel projects into one unified host-routed project. I wrote the editorial prompt architecture for each market, decomposed into 11 reusable per-market components (relevance rules, category routing, tie-breakers, KEEP/DROP examples, importance scoring, briefing voice) with anti-inflation discipline in shared engine code. AI coding assistants generated all production code under my direction.

All twenty-two markets run shared infrastructure (Next.js 14 App Router, Vercel Pro, Cloudflare DNS and Registrar, region-split Google Gemini 2.5 Flash Lite keys for editorial briefing generation, dual-layer cache with fresh and backup tiers, dual-typeface system) adapted at every layer to the realities of each market through per-market configuration. Categorization is rule-based with zero AI calls. The Social Pulse module (Bluesky, YouTube RSS, generic RSS) handles non-news signal at zero AI cost.

**AI cost engineering**: I drove monthly Gemini spend from approximately $300 in a few days on broken calls to approximately $1.41/month at ten markets on hourly cadence through architectural decisions. Moved categorization from AI to deterministic rules, decoupled the briefing cache from the main data cycle, region-split API keys for independent spend caps, ran a three-model benchmark before committing to gemini-2.5-flash-lite. Projected spend stays under $10/month at twenty-two markets on the current architecture.

**AI governance in production**: when a briefing factual-drift failure surfaced on one market (the model was resolving a generic “the governor” referent from training priors instead of the supplied headlines), I directed a shared-engine fix (factual-constraint guardrail, twenty-story input cap, length recalibration) that protected all twenty-two markets in one deploy rather than rewriting twenty-two per-market prompts. Same day, shipped a Tier 4 lead-picker fence and a press-feed `leadExcludedCategories` filter to stop unmatched or off-topic headlines from winning the homepage lead. Zero net cost increase on any of these changes. 649 Vitest tests cover host-map resolution, the categorizer with provenance tracking, the lead-picker five-tier fence, the RSS pipeline with a future-pubDate filter, palette validation, deprecated-field guards, Social Pulse filtering, the voices-route language guard, and per-market keyword coverage.

##### 🇪🇸 La Portada · Spanish · Latin America and Spain · 14 markets

🇵🇷 [**La Portada PR**](https://laportadapr.com) · *First deployment, April 2026.* Spanish-language news for Puerto Rico, modeled after the Drudge Report and Sayfie Review. “Lo esencial al momento” is the live editorial briefing.
🇲🇽 [**La Portada MX**](https://laportadamx.com) · Federal political news for Mexico. First non-PR Latin American market and the schema pressure test for the multi-tenant architecture. Categorization handles the 2024 judicial reform by treating SCJN coverage as a standalone category.
🇨🇴 [**La Portada CO**](https://laportadaco.com) · Federal political news for Colombia.
🇪🇸 [**La Portada ES**](https://laportadaes.com) · National political news for Spain.
🇦🇷 [**La Portada AR**](https://laportadaar.com) · Federal political news for Argentina.
🇵🇪 [**La Portada PE**](https://laportadape.com) · Federal political news for Peru.
🇨🇱 [**La Portada CL**](https://laportadacl.com) · Federal political news for Chile, with `security` as a standalone category.
🇩🇴 [**La Portada RD**](https://laportadard.com) · Federal political news for the Dominican Republic.
🇪🇨 [**La Portada EC**](https://laportadaec.com) · Federal political news for Ecuador.
🇬🇹 [**La Portada GT**](https://laportadagt.com) · Federal political news for Guatemala.
🇻🇪 [**La Portada VE**](https://laportadave.com) · Federal political news for Venezuela, with `justice` and `security` as standalone categories.
🇨🇷 [**La Portada CR**](https://laportadacr.com) · Federal political news for Costa Rica, with `security` as a standalone category.
🇵🇦 [**La Portada PA**](https://laportadapa.com) · Federal political news for Panama, with Canal coverage as a load-bearing economic signal.
🇨🇺 [**La Portada CU**](https://laportadacu.com) · Independent-first political news for Cuba, with `derechos_humanos` as a standalone category.

##### 🇺🇸 The StatePage · English · United States · national apex + 6 state subdomains

🇺🇸 [**The StatePage**](https://thestatepage.com) · National civic news anchoring the US brand family. State subdomains inherit AdSense approval from the parent.
🌴 [**The StatePage FL**](https://fl.thestatepage.com) · Florida political and government news.
🌉 [**The StatePage CA**](https://ca.thestatepage.com) · California political and government news.
🗽 [**The StatePage NY**](https://ny.thestatepage.com) · New York political and government news.
🦅 [**The StatePage PA**](https://pa.thestatepage.com) · Pennsylvania political and government news.
🤠 [**The StatePage TX**](https://tx.thestatepage.com) · Texas political and government news. RSS feeds curated for political balance. Government agenda strip with session/interim flex logic for the biennial Texas Legislature.
🌽 [**The StatePage IL**](https://il.thestatepage.com) · Illinois political and government news, with Chicago as a standalone category because city politics, CPS, CTA, and CPD drive disproportionate statewide attention.

##### 🏴󠁧󠁢󠁥󠁮󠁧󠁿 The EnglandPage · English · Country-Level Standalone

🏴󠁧󠁢󠁥󠁮󠁧󠁿 [**The EnglandPage**](https://theenglandpage.com) · England-level political and government news. Introduces a wordmarkParts schema pattern available for future country sites.

Repo: [github.com/plpk/portada-engine](https://github.com/plpk/portada-engine)

#### 📱 [Purese · AI-Powered Weather App](https://apps.apple.com/us/app/purese/id6744907444)

iOS weather app integrating Google Gemini 2.5 Flash API for AI-generated weather recommendations. Published to the Apple App Store using AI-assisted development. I directed the build, debugged it, and navigated the full Apple submission and review process independently. Marketing site: [purese.app](https://plpk.github.io/purese-weather-app/)

#### 🎯 TierCheckMedia · Context Engineering System

Context engineering system for AI-driven short-form video. Designed the full informational architecture: voice rules, hook taxonomy with structural formulas, human-cadence writing constraints to avoid AI-typical patterns, TTS-ready voiceover formatting, ethical guardrails, and a multi-tool pipeline (custom GPT + ElevenLabs voice clone + AI-generated music). Results in the first 15 days from a cold start: 80,000+ views, 8.4% engagement rate, double the industry average. Channels currently hibernated.

#### ✅ Playwright End-to-End Test Suite

Microsoft Playwright automated tests deployed against a production website with a 20+ year user base and active community. Real-world QA automation against live systems, real users, and real data.

### Background

- **Deputy Project Manager, EHP Compliance** · Hired as a Disaster Recovery Specialist II, then tapped to scope and launch a new Environmental Planning and Historic Preservation compliance program from a two-sentence ask. Authored the scope of work that became a $21M, 38-month FEMA work order covering hurricane recovery across 16,000+ miles of transmission lines. Led a 21-person cross-functional team. Directed the subcontractor relationship with the leading EHP engineering firm in Puerto Rico. Compliance across 1,200+ disaster recovery projects under NEPA, ESA, CWA, CAA, and NHPA. (IEM International, 2023-2024)
- **Oracle Aconex Specialist** · Enterprise project management software implementation at a major electric utility. 500+ licenses across the client’s company-wide deployment. Oracle Aconex Accredited Specialist. (Eniac Corporation, 2023)
- **Teaching Assistant, Technology Department** · Programming instruction (Python, HTML, Scratch, VEXcode VR robotics), lab IT, hardware management, faculty mentor for the Computer Club at UPR’s laboratory high school. (Universidad de Puerto Rico, 2021-2022)
- **Deputy Bureau Chief, Recovery and Preparedness** · Florida Division of Emergency Management. 24/7 operations across all 67 counties. Managed federal recovery programs (FEMA Public Assistance, Debris Operations). Operations Chief for Operation Haiti Relief. Helped introduce state agency social media use for emergency communications under Director Craig Fugate’s initiative, trained 130+ employees. (2008-2010)
- **US Army Combat Veteran** · Iraq 2003-2004, Infantry, 3rd Battalion 124th Infantry. Combat Infantryman Badge. Army Commendation Medal for Valor.
- **Graduate Researcher** · Doctoral studies in History, international archival research across eight countries

### Education

- **Doctoral Studies, History** (Coursework Completed) · University of Puerto Rico, Río Piedras · Golden Key International Honour Society
- **M.S., Political Science** · Florida State University
- **B.A., Spanish Language and Literature** · Florida State University

### Awards

Combat Infantryman Badge · Army Commendation Medal for Valor · Presidential Unit Citation (Navy) · Mississippi Emergency Service Medal · Florida Meritorious Service Ribbon · GWOT Expeditionary Medal · National Defense Service Medal · NPS Customer Service Award

-----

**Open to:** Context Engineering · AI Integration · AI Governance · AI Cost Engineering · QA Automation · AI Evaluation
**Bilingual:** English · Spanish (both native)

📫 **Louis.Kunasek@outlook.com** · [LinkedIn](https://linkedin.com/in/louiskunasek) · [Portfolio](https://louiskunasek.net) · [La Portada PR](https://laportadapr.com) · [The StatePage](https://thestatepage.com) · [The EnglandPage](https://theenglandpage.com) · [App Store](https://apps.apple.com/us/app/purese/id6744907444)

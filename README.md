# Blog — Prompt Builder

A single-file, client-side tool for Ring Ring Marketing's on-page SEO team. Fill out the Client Brief **once**, pick the client's industry, and it builds two ready-to-paste prompts with all the rules and the matching Vertical Pack already baked in:

1. **Topics prompt** — produces 4 blog topics (Blog Title + Meta Title + Meta Description), split 2 Commercial / 2 Informational.
2. **Blog Writing prompt** — produces the full 500–800 word blog post for one topic, followed by 5 meta tag sets.

It follows the same pattern as the **City Page — Prompt Builder**: every rule is embedded in the generated prompt, so you paste it into a **fresh ChatGPT (or Claude) chat** and it just works. No `CLAUDE.md` file needed alongside it.

## Live tool

👉 **https://joshuavns.github.io/blog-prompt-builder/** *(after you push this folder to a `blog-prompt-builder` repo and enable GitHub Pages)*

## How to use

1. Fill the **Client Brief**: Business Name, Website, optional Phone/Address (context only — the location is never revealed in a blog), Industry, and Writing Voice (first-person plural is the blog default).
2. **Brand Identity** — paste the client's trust signals and key service facts (years in business, certifications/licenses, manufacturer partnerships, specializations, guarantees, memberships). You can attach a `.docx / .xlsx / .csv / .txt` and the text is extracted in-browser. This carries the EEAT load because ChatGPT can't reliably crawl most sites.
3. **Step 1 — Keywords**: enter the 4 target keywords for the month and (optionally) paste topics already used so they aren't repeated. Click **Generate Topics Prompt**, run it, and the AI returns 4 topics with the best 2/2 intent split.
4. **Step 2 — Blog Writing (all 4)**: for each of the 4 blogs, paste its title (keyword and target city auto-fill), set the intent the AI assigned, and add the **4 internal links** (Blog Post, City Page, Main Page 1, Main Page 2). Click **Generate 4 Blog Writing Prompts** — it outputs one self-contained prompt per blog (blogs left without a title are skipped, so you can also do fewer).
5. Run each prompt in its **own fresh chat** to get the full blog + 5 meta tag sets. That matches the monthly cadence: 4 blogs per client.
6. **Format for Word** — paste the blog output into the bottom box and click **Clean for Word**. The Markdown links (`[anchor](url)`) and `**bold**` become formatted text with real *clickable* hyperlinks, so links carry over when you paste into your doc. Or use **Download Word (.doc)**.

### Step 1 vs Step 2 meta tags

Both steps produce meta tags, on purpose:
- **Step 1** outputs a single Meta Title + Meta Description per blog, clearly labeled a **planning preview** — it's for approving the month's topics, not for shipping.
- **Step 2** outputs the **5 final meta sets** (Meta Title + H1 + Meta Description), written *after* the blog so they're content-aware. These are the ones that go on the page; you pick one of the five.

Use **Save brief to browser** / **Load saved brief** to keep your work between sessions.

## What's baked into the prompts

- **Global rules** — no em-dashes, no cost/price framing, no year references, active voice, no buzzwords.
- **Vertical Packs** — Home Improvement, Home Care, Death Care (and a General fallback), each with the right audience, tone, and the commercial/informational blog angles. The Industry dropdown auto-selects the matching pack.
- **Blog structure** — 500–800 words, opening/body/closing (never those literal headings), H2/H3, short paragraphs, a featured-snippet block.
- **EEAT** — pulls trust signals from Brand Identity in priority order; verifiable facts only.
- **Keyword discipline** — focus keyword used exactly twice (first paragraph = the City Page Link anchor; last paragraph = no link).
- **Internal links** — 4 required, spread across sections, natural mid-sentence anchors.
- **Content restrictions** — no address/physical city, no DIY/repairs, business name ≤ 2 times, soft closing CTA (no phone, no hard sell).
- **5 meta tag sets** — Meta Title 56–58 chars (hyphen separator), H1 55–75 chars, Meta Description 140–160 chars with the business name once and a soft blog CTA, with the business-name placement varied across the 5 sets.

## Notes

- Everything is client-side. No data leaves the browser; **Save** uses `localStorage`.
- File parsing uses small CDN libraries (mammoth for `.docx`, SheetJS for `.xlsx`), so the attach feature needs the page online — which it is on GitHub Pages.
- The Vertical Packs and all rules are embedded in `index.html`. If the blog SOP changes, update the constants there to match.
- This is the blog counterpart to the City Page — Prompt Builder. Keep the rules in sync with the team's blog SOP.

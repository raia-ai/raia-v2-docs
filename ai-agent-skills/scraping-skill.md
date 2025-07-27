# Scraping Skill

The **Scraping Skill** allows agents to ingest content from external websites by crawling and extracting structured or unstructured data. You can configure scraping sources by specifying various parameters, which control what gets scraped, how deep the crawler goes, and in what format the content is returned.

### 🧩 Config Parameters

Each scrape configuration includes the following required fields:

#### 🔗 Website _(Required)_

* **What it is:** The root URL to start the web crawl from.
* **Format:** Must begin with `http://` or `https://`.
* **Example:** `https://example.com`

> The crawler will begin from this URL and follow internal links up to the depth and limit you define.

***

#### 🧭 Crawler Type _(Required)_

* **What it is:** Determines which backend engine handles the crawling and scraping.
* **Options:**
  * `Apify` – Enterprise-grade web scraping with JavaScript rendering.
  * `Firecrawl` – Fast, AI-assisted scraping; ideal for simpler sites or headless crawls.

> ⚠️ Each crawler type may behave differently and support different exclusion rules (see “Excluded URLs” below).

***

#### 📦 Crawl Format _(Required)_

* **What it is:** The output format in which content is returned after scraping.
* **Options:**
  * `Markdown` – Lightweight text format ideal for content summarization and LLM ingestion.
  * `JSON` – Structured data, suitable for programmatic processing.
  * `HTML` – Raw HTML output, useful for custom parsers.
  * `Content` – Parsed clean content blocks (typically used with Firecrawl).

> Choose a format depending on the agent’s downstream processing logic.

***

#### 📄 Page Limit _(Required)_

* **What it is:** Caps the number of total pages crawled per website.
* **Purpose:** Prevents large or infinite crawls that could overload websites or incur unnecessary costs.
* **Example:** `10` (maximum of 10 pages scraped)

***

#### 🧬 Max Depth _(Required)_

* **What it is:** Controls how far the crawler follows links from the starting URL.
* **Depth Levels:**
  * `1` = Crawl only the starting page.
  * `2` = Include pages directly linked from the start page.
  * `3+` = Deeper nested links (e.g., homepage → category → product → details)

***

#### 🚫 Excluded URLs _(Optional)_

* **What it is:** A list of paths or full URLs to skip during the crawl.
* **Purpose:** Useful for ignoring login pages, irrelevant sections, or known spam.
* **How to use:** Click the **+ Add Exclude URL** button to define exclusion rules.

**🔍 Crawler-Specific Notes:**

* **Apify:** Excludes based on URL string match or regex.
* **Firecrawl:** Uses prefix-based exclusion (starts with...).

> 🧠 Check the documentation for each crawler engine on how exclusions are applied.

***

### ✅ Best Practices

* Use a **low depth** and **modest page limit** when first testing.
* If targeting **blogs or knowledge bases**, Markdown is often ideal.
* If you're scraping **product listings or structured data**, JSON is recommended.
* Use exclusions to block terms like `/login`, `/admin`, `/cart` to avoid irrelevant pages.

***

Let me know if you'd like a JSON or YAML template version of this config for automation or API submission.
